# Anchor Contract Deployment

- navigate to your project director
  `cd your_project_directory`
- install the packages
  `yarn install`
- build the project
  `anchor build`
- generate the program address
- ex: solana address -k target/deploy/basic_1-keypair.json
  `solana address -k your_key_path`

- this will give use the program address
- ex: _8B4uarvHDTSFFLL1Htsvw1WM4tEiD5Wf2jf8wFmbATW7_

- copy the id and paste it at:
  `declare_id!("8B4uarvHDTSFFLL1Htsvw1WM4tEiD5Wf2jf8wFmbATW7")`

- run anchor build again
  `anchor build`
- now deploy the program
  `anchor deploy`

if the program failed to deploy then we need to troubleshoot the problem, some of the things that we can do here are:

- if you are deploying the program on devent make sure that cluster is set to _devnet_ and [programs.devnet] is set

- if your are deploying on localnet then make sure the local rpc node is running
  `solana-test-validator`

- check if your wallet value in Anchor.toml is the same as your pc's solana keypair path
  to check it run _solana config get_
  now set the wallet=_your keypair path_

- the _Most IMP_ thing is to check if there's any space in your project path, if it exists then remove it or move the project somewhere else that doesn't have any space in it's path

for ex: Program path: `/mnt/c/Web Development/My Projects/Blockchain/solana/anchor-learning/anchor/examples/tutorial/basic-1/target/deploy/basic_1.so`

here i had two spaces at _Web Development_ and _My Project_ which were giving me the error - _something about signer_

after removing those spaces the contract deployed successfully :)

# Testing

- the first error you might get is _module not found @project-serum/anchor_ so just install it with
  `yarn add yarn add @project-serum/anchor`

- if you are on devnet then change the provider to devnet, or just use the configuration set in Anchor.toml
  `const provider = anchor.AnchorProvider.env();`
