<template lang="html">
  <div class="container">
    <h2>{{title}}</h2>
    <p><i>This generates a new wallet address & mnemonic seed </i></p>
    <div class="btn-group btn-group-lg" role="group">
    </div>
    <button type="button" v-on:click="createWallet" class="btn btn-success" style="margin-top: 30px; background-color:#0c091d; border-color:#0F232B; padding:14px 18px; font-size:19px; box-shadow:0 4px 6px 0 hsla(0, 0%, 0%, 0.5)">Create Wallet</button>
    <br><br>
    <div id="panel1" class="console panel panel-default" :class="displayClass">
      <div class="panel-heading">
        <h3 class="panel-title"> Public Address </h3>
      </div>
      <div class="panel-body">
        {{ public_addr }}
      </div>
    </div>
    <div id="panel2" class="console panel panel-default" :class="displayClass">
      <div class="panel-heading">
        <h3 class="panel-title"> Mnemonic seed </h3>
      </div>
      <div class="panel-body">
        {{ mnemonicString }}
      </div>
    </div>
    <hr>
    <i>
      Source code:  <a target="_blank" href="https://github.com/haven-protocol-org/haven-paper-wallet">github.com/haven-protocol-org/haven-paper-wallet</a>
    </i>
  </div>
</template>

<script>
const walletUtils = require('mymonero-core-js/monero_utils/monero_wallet_utils')

export default {
  data () {
    return {
      title: 'Haven Paper Wallet',
      displayClass: 'is-hidden',
      mnemonicString: '',
      public_addr: ''
    }
  },
  methods: {
    createWallet: function () {
      const wallet = walletUtils.NewlyCreatedWallet('english')
      this.public_addr = wallet.keys.public_addr
      this.mnemonicString = wallet.mnemonicString
      this.displayClass = ''
    }
  }
}
</script>

<style lang="css">
  .panel-body {
    font-family: "Lucida Console", "Lucida Sans Typewriter", monaco, "Bitstream Vera Sans Mono", monospace;
    font-size: 12px;
    text-align: left;
    color: #2bf22b;
    background-color: #000;
  }
  .console {
    overflow-wrap: break-word;
    margin: auto;
    max-width: 750px
  }

  .is-hidden {
    visibility: hidden;
  }
</style>
