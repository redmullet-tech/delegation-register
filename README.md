# delegation-register

###### How to use the contract?
Simply put, the proposed contract implementation creates a "Delegation Register" that exists purely on-chain. This means that all the data and their provenance are part of the contract's state. 

###### Ok, so how can you use it then?

It is often the case that wallet owners wish to assign delegation rights (in this context let's refer to assigners as "Delegators"") to some other wallet address to act on their behalf (in this context let's refer to them as "Proxies"). Any valid address could be assigned as a Proxy by a Delegator.

We note that the action of "delegation" does not assign ownership to the Delegator wallet (including its assets) to the Proxy address. 

###### Ok, so why is it useful then?

- Delegation assignments make sense in cases where it is extremely risky to connect and sign messages from a cold wallet that is used for storing valuable fungible or non-fungible assets. Proxies can be used to represent a Delegator and act on the Delegator's behalf under certain actions:

An action could be:
	1. claiming token airdrops
	2. minting tokens from collections that require an entry to their whitelist(s)
	3. verifying/proving token ownership e.g., apps that implement some token gated policy

- Interacting with dApps often requires signing of messages for performing certain operations. Accidentally signing a malicious transaction can authorize  access to your assets.

- Overall, this contract proposal is useful for use-cases where dApps require a global, on-chain registry that maps the "delegation" relationship between a pairs of valid wallet addresses. Current implementation maps the following delegations based on certain actions:
	1. Delegator's Address -> Wallet Address to act on all actions
	2. Delegator's Address -> Wallet Address to act on a specific Smart Contract Address (e.g., NFT Collection)
	3. <???>
	
###### Implementation features

(1) Contract is free from any dependencies. We took the design decision to implement core functionality and include it as part of the core contract without referring to any external libraries that could (potentially) introduce additional attack vectors or vulnerabilities outside our control; since these are maintained by teams that are outside the control scope of our core implementation. Therefore, we are adopting a self-contained contract philosophy.
