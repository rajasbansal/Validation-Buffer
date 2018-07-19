The repository consists of a boom/ directory which contains the code for the BOOM core which uses the rocket chip sources. These sources need to be edited to change the Validation Buffer.

This code is used along with BOOM v1. BOOM v2 has a very different compilation strategy than v1. Here, inside the rocket chip directory, change the directory to the emulator/ directory.

Prior to running make, certain variables must be exported. The following variables need to be exported :-

export RISCV=PATH_TO_RISC-V_TOOLS
export PATH=$PATH:$RISCV/bin
export CC=gcc-4.9
export CXX=g++-4.9

Here running "make", leads to the compilation of the boom emulator which can be used to run binaries and test programs. Running "make run" runs all the RISC-V assembly tests and benchmarks. 

When "make run" is used, one can see the command (in the emulator directory)
./emulator-rocketchip-BOOMConfig +max-cycles=100000000 +verbose COMPILED_BINARY 3>&1 1>&2 2>&3 | $RISCV/bin/spike-dasm  > OUTPUT_TEXT_FILE && [ $PIPESTATUS -eq 0 ]

Here $RISCV/riscv64-unknown-elf/share/riscv-tests/isa/ directory contains all test programs (see the dump files) which are run. There is a symbolic link inside the output directory here. Thus the compiled binary that needs to be run needs to be placed in place of COMPILED_BINARY.

Running SPEC applications has the same procedure. 

Try running the hello world C program using "spike pk executable" to ensure that spike has been installed correctly.