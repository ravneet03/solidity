
# MyToken Project

## Project Title
MyToken Smart Contract

## Simple Overview
This project involves creating a simple smart contract for a custom token on the Ethereum blockchain. The contract includes functionalities for minting and burning tokens, managing balances, and storing token details.

## Description
The MyToken smart contract is a basic implementation of an ERC20-like token on the Ethereum blockchain. It includes the following features:
- Public variables to store token details such as name, abbreviation, and total supply.
- A mapping to keep track of balances associated with different addresses.
- A mint function to create new tokens and increase the total supply.
- A burn function to destroy tokens and decrease the total supply with checks to ensure sufficient balance.

## Getting Started

### Installing
To get started with this project, follow these steps:

1. Open [Remix IDE](https://remix.ethereum.org/).

2. Create a new file named `MyToken.sol` and paste the following code:

    ```solidity
    // SPDX-License-Identifier: MIT
    pragma solidity 0.8.18;

    /*
           REQUIREMENTS
        1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
        2. Your contract will have a mapping of addresses to balances (address => uint)
        3. You will have a mint function that takes two parameters: an address and a value. 
           The function then increases the total supply by that number and increases the balance 
           of the “sender” address by that amount
        4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
           It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
           and from the balance of the “sender”.
        5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
           to the amount that is supposed to be burned.
    */

    contract MyToken {

        // public variables here
      string public tokenName = "SLOY";
      string public tokenAbbrv = "SLY";
      uint public totSupply = 0;

        // mapping variable here
      mapping (address => uint) public balances;

        // mint function
      function mint (address _address, uint _value) public {
        totSupply += _value;
        balances[_address] += _value;
      }
        // burn function
      function burn (address _address, uint _value) public {
        
        if (balances[_address] >= _value){totSupply -= _value;
        balances[_address] -= _value;
        }
      }
    }
    ```

### Executing Program
To compile and deploy the smart contract, follow these steps in Remix IDE:

1. **Compile the Contract:**
   - Select the `MyToken.sol` file in the file explorer.
   - Click on the "Solidity Compiler" tab on the left panel.
   - Ensure the compiler version is set to `0.8.18`.
   - Click on the "Compile MyToken.sol" button.

2. **Deploy the Contract:**
   - Click on the "Deploy & Run Transactions" tab on the left panel.
   - Ensure the environment is set to "JavaScript VM" for local testing.
   - Click on the "Deploy" button.

3. **Interact with the Deployed Contract:**
   - After deployment, the contract will appear in the "Deployed Contracts" section.
   - Expand the contract to view the available functions.
   - Use the `mint` function to create new tokens:
     - Enter an address and value.
     - Click on the "transact" button.
   - Use the `burn` function to destroy tokens:
     - Enter an address and value.
     - Click on the "transact" button.
   - You can also view the token details and balances using the respective public variables and mapping.

## Help
If you encounter any issues, ensure that:
- You have selected the correct Solidity compiler version (0.8.18).
- You are using the correct environment in Remix IDE.
- Your code does not have any syntax errors.

For further assistance, you can refer to the official documentation of [Remix IDE](https://remix-ide.readthedocs.io/).

## Authors
Contributors:
- Ravneet Singh

## License
This project is licensed under the MIT License - see the LICENSE.md file for details.
