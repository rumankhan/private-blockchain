# Private Blockchain Application
This project built using boilerplate template provided by Udacity and is part of assessment for validating blockchain understanding.

## What problem will you solve implementing this private Blockchain application?

Your employer is trying to make a test of concept on how a Blockchain application can be implemented in his company.
He is an astronomy fans and he spend most of his free time on searching stars in the sky, that's why he would like
to create a test application that will allows him to register stars, and also some others of his friends can register stars
too but making sure the application know who owned each star.

### What is the process describe by the employer to be implemented in the application?

1. The application will create a Genesis Block when we run the application.
2. The user will request the application to send a message to be signed using a Wallet and in this way verify the ownership over the wallet address. The message format will be: `<WALLET_ADRESS>:${new Date().getTime().toString().slice(0,-3)}:starRegistry`;
3. Once the user have the message the user can use a Wallet to sign the message.
4. The user will try to submit the Star object for that it will submit: `wallet address`, `message`, `signature` and the `star` object with the star information.
    The Start information will be formed in this format:
    ```json
        "star": {
            "dec": "68° 52' 56.9",
            "ra": "16h 29m 1.0s",
            "story": "Testing the story 1"
		}
    ```
5. The application will verify if the time elapsed from the request ownership (the time is contained in the message) and the time when you submit the star is less than 5 minutes.
6. If everything is okay the star information will be stored in the block and added to the `chain`
7. The application will allow us to retrieve the Star objects belong to an owner (wallet address). 

## Understanding the code

This code is a simple architecture for a Blockchain application, it includes a REST APIs application to expose the your Blockchain application methods to your client applications or users.

1. `app.js` file. It contains the configuration and initialization of the REST Api
2. `BlockchainController.js` file. It contains the routes of the REST Api
3. `block.js` file. Contains the schema and methods related to a block
4. `blockchain.js` file. Contains the code required add blocks into the chain, validate blocks and also search block based on hash and owner address

## RESTful APIs exposed on this project

1. Run your application using the command `node app.js`
2. Request block by height: http://localhost:8000/block/0
    ![Request: http://localhost:8000/block/0 ](docs/request-genesis.png)
3. Make your first request of ownership sending your wallet address:
    ![Request: http://localhost:8000/requestValidation ](docs/request-ownership.png)
4. Sign the message with your Wallet: (If you are using latest Bitcoin core on Testnet, use getnewaddress "legacywalletlabel" legacy to generate legacy wallet address which can be used to sign message on Testnet)
    ![Use the Wallet to sign a message](docs/sign-message.png)
5. Submit your Star
     ![Request: http://localhost:8000/submitstar](docs/signing-message.png)
6. Retrieve Stars owned by me
    ![Request: http://localhost:8000/blocks/<WALLET_ADDRESS>](docs/retrieve-stars.png)
7. ValidateChain
    ![Request: http://localhost:8000/blocks/<WALLET_ADDRESS>](docs/retrieve-stars.png)

References:
CryptographicHashFunctions: https://en.wikipedia.org/wiki/Cryptographic_hash_function
Working with Promises: https://developers.google.com/web/ilt/pwa/working-with-promises
Udacity Blockchain course: https://www.udacity.com/course/blockchain-developer-nanodegree--nd1309
