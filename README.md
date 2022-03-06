Auditing tools and uses

1.  Slither - Static analyzer
    https://github.com/crytic/slither

    Quick Review Printers
    human-summary: Print a human-readable summary of the contracts
    inheritance-graph: Export the inheritance graph of each contract to a dot file
    contract-summary: Print a summary of the contracts
    
    In-Depth Review Printers
    call-graph: Export the call-graph of the contracts to a dot file
    cfg: Export the CFG of each functions
    function-summary: Print a summary of the functions
    vars-and-auth: Print the state variables written and the authorization of the functions
    To run a printer, use --print and a comma-separated list of printers.

    Tools
    slither-check-upgradeability: Review delegatecall-based upgradeability
    slither-prop: Automatic unit test and property generation
    slither-flat: Flatten a codebase
    slither-check-erc: Check the ERC's conformance
    slither-format: Automatic patch generation

    My comments:

2.  Mythril - static analyzer
    https://github.com/ConsenSys/mythril
    Get it with Docker:
    $ docker pull mythril/myth
    Install from Pypi:
    $ pip3 install mythril
    See the docs for more detailed instructions.
    Usage
    Run:
    $ myth analyze <solidity-file>
    Or:
    $ myth analyze -a <contract-address>
    Specify the maximum number of transaction to explore with -t <number>. You can also set a timeout with --execution-timeout <seconds>. Example (source code):

3.  Echidna - fuzzer
    https://github.com/crytic/echidna
    https://github.com/crytic/building-secure-contracts/blob/master/program-analysis/echidna/finding-transactions-with-high-gas-consumption.md
    Adding Constructor Arguments: https://github.com/crytic/echidna/issues/693

    (Default for no arguments) Run user-defined property tests: echidna-test contract.sol --test-mode property
    Detect integer overflows (Solidity 0.8.x+): echidna-test contract.sol --test-mode overflow
    Find the maximum value for a function: echidna-test contract.sol --test-mode optimization
    Execute every line of code without any testing target ("unconstrained execution"): echidna-test contract.sol --test-mode exploration
    echidna-test contracts/echidna/Gas.sol --config config/echidna/gas.yaml

    (Default for no arguments) Run user-defined property tests: echidna-test contract.sol --test-mode property
    Detect integer overflows (Solidity 0.8.x+): echidna-test contract.sol --test-mode overflow
    Find the maximum value for a function: echidna-test contract.sol --test-mode optimization
    Execute every line of code without any testing target (“unconstrained execution”): echidna-test contract.sol --test-mode exploration

4.  Smartcheck - static analysis
    https://github.com/smartdec/smartcheck
    To start analysis simply run:
    smartcheck -p .
    Required argument: -p <path to directory or file>. Optional argument: -r <path to .xml-file with rules>; by default it uses the built-in rules files.
