
# UHome Harmony

UHome network private peer. Based on Uhomej implementation. 

 
### Features: 

 * UHome peer JSON-RPC 2.0 standard ;
 
 * Keeping private keys in filesystem **keystore** ;
 
 * In Browser command line terminal;
 
 * Blockchain canonical tracing;   
 
 * Monitoring peers connectivity;
 
 * Easy go Ethereum **wallet**;
  
 * Full trace of contract storage locally; 

.

## Prerequisites Installed: 
 * Java 8 (64 bit)

.

## Run 

* `git clone https://github.com/uhomeio/uhome-harmony`
* `cd uhome-harmony`
* Run Service: `gradlew runMain`  ( live network by default or any [other environment](#options) )

Navigate to `http://localhost:8080`
JSON-RPC is available at either `http://localhost:8080/rpc` or `http://localhost:8080`

(*) Use `gradlew runMain -Dserver.port=9999` option to change web interface port number.

.

## Command line options <a id="options"></a>

| Environment        | Run      | ... |
| ------------- |:-------------|------------- |
| Main      | `gradlew runMain` | Start server connecting to **Main** network |
| Ropsten      | `gradlew runRopsten` | Start server connecting to **Ropsten** network |
| Classic | `gradlew runClassic`      | Start server connecting to **UHome Classic** network |   
| Private | `gradlew runPrivate`      | Start server, no network connection, single miner running|    
| Custom | `gradlew runCustom`      | Start server connecting to custom network (check [custom network](#custom-network)) |

.

## Run in a custom network <a id="custom-network"></a>
* `git clone https://github.com/uhomeio/uhome-harmony`
* `cd uhome-harmony`
* Run Service with custom config: 
```
gradlew runCustom -Dethereumj.conf.file=/path/to/custom.conf
```
* It is also possible to use CLI to pass parameters: 
```
gradlew runCustom -Dpeer.networkId=10101 -DgenesisFile=/path/to/custom/genesis.json -Dpeer.discovery.enabled=false -Dpeer.active.0.url=enode://0f4a5f92835a4604ecd9639ddcfb86d2a2999ad9328bc088452efffe4a7c6cd0eaaef77c779dc56fc1d0f21cd578eeb92cb5@23.101.151.28:30303
```

**Note:** parameters that haven't been substituted by either custom config or CLI will be supplied from [ethereumj.conf](https://github.com/ethereum/ethereumj/blob/master/ethereumj-core/src/main/resources/ethereumj.conf)

#### Custom config file format
Format of the file should be the same as of [ethereumj.conf](https://github.com/uhomeio/uhomej/blob/master/ethereumj-core/src/main/resources/ethereumj.conf). It also works to specify only necessary config parameters.

An example: 
  ```
  genesisFile = /path/to/custom/genesis.json
  database.dir = database-private

  peer {
    networkId = 10101
    listen.port = 50505

    discovery.enabled = false
    active = [
      {url = "enode://6ce05930c72abc632c58e2e4324f7c7ea478cec0ed4fa2528982cf34483094e9cbc9216e7aa349691242576d552a2a56aaeae426c5303ded677ce455ba1acd9d@13.84.180.240:30303"}
      {url = "enode://20c9ad97c081d63397d7b685a412227a40e23c8bdc6688c6f37e97cfbc22d2b4d1db1510d8f61e6a8866ad7f0e17c02b14182d37ea7c3c8b9c2683aeb6b733a1@52.169.14.227:30303"}
    ]
  }

  sync.fast.enabled = false
  ```
.

.

.

### Development

Check [Development troubleshooting](https://github.com/uhomeio/uhome-harmony/wiki/Development-troubleshooting)

