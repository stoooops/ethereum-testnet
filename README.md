# ethereum-testnet

Dockerized one-touch Ethereum testnet

## Run
To run the testnet, simply run the following command:

```bash
docker-compose up
```

or

```bash
yarn start
```

or

```bash
yarn start:detach
```

If you shut it down and restart it, it will continue from the last block mined.

### Restart from genesis block

To wipe state and re-initialize `geth` from the genesis block, run the following command:

```bash
yarn regenesis
```

## Fund Accounts

You can re-initialize the `genesis.json` file with your own accounts by setting the following environment variables:

- `CHAIN_ID` - The chain ID of the testnet
- `MINER_ADDRESS` - The address of the miner account
    - (private key hard-coded in empty-password protected keystore file in `execution/keystore` directory)
- `DEPLOYER_ADDRESS` - The address of the deployer account
    - (default is "m/44'/60'/0'/0" path for "test test test test test test test test test test test junk" mnemonic)
- `ADDRESS_USER1` - The address of the user1 account
- `ADDRESS_USER2` - The address of the user2 account
- `ADDRESS_USER3` - The address of the user3 account

If you change the `MINER_ADDRESS`, you will need to also update the `docker-compose.yml` and generate a
Then run the following command to re-initialize the `genesis.json` file:

```bash
yarn mkgenesis
```

If you wish to add more, you can search for those strings in the codebase and extend the pattern.

Once you're done, you can run `yarn regenesis` to re-initialize the testnet.

## Connect to the testnet JSON-RPC

To test if the testnet is running, you can use the scripts in the `scripts` directory.

To test an RPC call, run:

```bash
yarn rpc
```

To test an authenticated RPC call using the JWT secret, run:

```bash
yarn rpc:auth
```

