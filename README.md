# DEPRECATED

»Coinvestor« has been renamed to »[Autopilot](https://github.com/rasshofer/autopilot)«. Please install and use it instead.

# Coinvestor

> A simple (CLI) tool to »Cost Average«-buy Bitcoin, Litecoin, and/or Ethereum using Coinbase or GDAX

Cost averaging is a common investment technique of buying a fixed amount of a particular investment (e.g. cryptocurrencies) on a regular schedule, regardless of the share price. Hence one purchases more shares when prices are low and fewer shares when prices are high. This way one is able to compensate for exchange rate fluctuations.

Coinvestor is supposed to be configured as a cronjob that is executed once per day/week/month.

<img src="https://cdn.rawgit.com/rasshofer/coinvestor/master/screenshot.png" alt="Coinvestor" width="675" height="327">

## CLI

```shell
npm install -g coinvestor
```

```shell
$ coinvestor {OPTIONS}
```

## Configuration

Coinvestor is configured using the following options via a configuration file, environment variables, and/or command-line arguments.

First of all, Coinvestor looks for a JSON file called `coinvestor.json` within the current working directory.

```json
{
  "coinbase_api_key": "NlpFapHtwkqyOfg",
  "coinbase_api_secret": "bchx51JunqVeEH2LG2li7iKDWMj1lrVo",
  "btc": "10"
}
```

Afterwards, Coinvestor will take environment variables into account.

```shell
coinbase_api_key=Ffs0PvsT9OSgDs3 coinbase_api_secret=SuOMOn7GMjcetdamzD2OWqAN8DQex0nB btc=12 eth=34 ltc=56 coinvestor
```

Concluding, Coinvestor will take command-line arguments into account.

```shell
coinvestor --coinbase_api_key=Ffs0PvsT9OSgDs3 --coinbase_api_secret=SuOMOn7GMjcetdamzD2OWqAN8DQex0nB --btc=12 --eth=34 --ltc=56
```

(All options are merged into a single configuration using the hierarchy described above.)

## Options

### Coinbase account

In order to use Coinvestor, you need to create a new API key for your Coinbase account. To do so, head over to [https://www.coinbase.com/settings/api](https://www.coinbase.com/settings/api) and create a new key. Coinvestor needs the following permissions in order to perform buys for you.

- `wallet:accounts:read`
- `wallet:buys:create`
- `wallet:payment-methods:read`

Make sure you granted all of these permissions for the API key.

#### `coinbase_api_key`

Your Coinbase API key. 15 characters long.

Example: `NlpFapHtwkqyOfg`

#### `coinbase_api_secret`

Your Coinbase API secret. 32 characters long.

Example: `bchx51JunqVeEH2LG2li7iKDWMj1lrVo`

### GDAX account

Besides Coinbase you’re also able to buy coins using GDAX. In order to use Coinvestor with GDAX, you need to create a new API key for your GDAX account. To do so, head over to [https://www.gdax.com/settings/api](https://www.gdax.com/settings/api) and create a new key. Coinvestor needs the following permissions in order to perform buys for you.

- `View`
- `Trade`

Make sure you granted all of these permissions for the API key.

#### `gdax_api_key`

Your GDAX API key. 32 characters long.

Example: `1ab05e21dc847c87970130229b61a987`

#### `gdax_api_secret`

Your GDAX API secret.

Example: `AwtyoyLzp3MyDGxuJvj2nGSTWR1mBHMDIxybMH1YqJcsYwOaDIH6JQxbDGLdFmWIKl0bDwcaHJ56JRVaM2gsYD==`

#### `gdax_api_passphrase`

Your GDAX API passphrase. 11 characters long.

Example: `johxudf2va4`

### Purchases

Now that Coinvestor is able to perform buys for you, you need to specify what kind of buys you want to be performed.

#### `strategy`

The strategy used when buying. Choose `total` in case your specified amount is supposed to be bought including any Coinbase fees (= contained) or choose `amount` in case the specified amount is supposed to be bought excluding any Coinbase fees (= charged supplementary).

Default: `total`

#### `currency`

The base currency used for buying cryptocurrencies. As of now, Coinvestor is not able to handle credit card payments or SEPA bank accounts (due to security restrictions), thus it will always use the FIAT account/wallet matching your base currency.

Example: `USD`

Default: `EUR`

#### `btc`

Amount of your base currency to buy Bitcoin for.

Example: `12.34`

Default: `0`

#### `eth`

Amount of your base currency to buy Ethereum for.

Example: `13.37`

Default: `0`

#### `ltc`

Amount of your base currency to buy Litecoin for.

Example: `0.50`

Default: `0`

## Changelog

* 0.0.5
  * Fix README
* 0.0.4
  * Implement support for GDAX
* 0.0.3
  * Remove unused import
* 0.0.2
  * Fix screenshot within README
* 0.0.1
  * Initial version

## License

Copyright (c) 2017 [Thomas Rasshofer](http://thomasrasshofer.com/)  
Licensed under the MIT license.

See LICENSE for more info.
