# LLVM IR Slicer and Source Extractor

```text
⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣠⣄⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⢰⡟⠉⠉⠙⣦⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⢸⡇⠀⠀⠀⠸⣧⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠈⣿⡄⠀⠀⢠⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⢀⣤⡶⠶⢶⣤⣄⣀⠘⠛⠶⣴⠿⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⣾⡇⠀⠀⠀⠈⠙⢿⣿⣷⣶⣤⣄⣀⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠘⢷⣄⡀⠀⠀⢀⣸⡟⠉⠙⠻⣿⣿⣿⣷⣶⣤⣄⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠉⠛⠛⠛⠛⠉⠀⠀⢸⣦⣄⡉⠛⠿⣿⣿⣿⣿⣿⣶⣤⣀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢿⣿⣿⣆⠀⠀⠙⠻⢿⣿⣿⣿⣿⣷⣄⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⣿⣿⣿⣦⠀⠀⠀⠀⠈⠙⠻⢿⣿⣿⣷⡀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠸⣿⣿⣿⣧⡀⠀⠀⠀⠀⠀⠀⠉⠛⠿⣷⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠹⣿⣿⣿⣷⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠙⣿⣿⣿⣧⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠻⣿⣿⣷⡀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠉⠛⠓⠀⠀⠀⠀⠀⠀⠀⠀
```

This project aims to extract specific functions from an LLVM Intermediate Representation (IR) file. It's built using C++ and leverages the C++ LLVM API parsing `*.ll` files and extracting the slices of code corresponding to the LLVM IR files.

## Prerequisites

- CMake 3.10 or higher
- LLVM 13
- A C++17-compatible compiler (e.g., GCC, Clang)

## Building the Project

First, clone the repository and navigate into the project's root directory.

```bash
git clone https://github.com/raptor-oss/llvm-source-extractor.git
cd llvm-source-extractor/
```

Create a build directory and navigate into it.

```bash
mkdir build
cd build
```

Run CMake to generate the build files and build the project.

```bash
cmake ..
make
```

After successful build, you should see an executable named `LLVMSourceExtractor` inside the `build/` directory.

## Running the Project

For usage instructions, from the `build/` directory, execute:

```bash
❯ ./LLVMSlicer --help
LLVM IR Slicer and Source Extractor
Usage: ./LLVMSourceExtractor [OPTIONS]

Options:
  -h,--help                   Print this help message and exit
  --input TEXT REQUIRED       The Path to LLVM IR file (*.ll)
```

To run a sample program (run the following from within the build directory):

```bash
./LLVMSlicer --input=../test/test_data/test_rust.ll

---------------------------------------------
IR:   %2 = sext i32 %0 to i64
---------------------------------------------
IR:   %3 = tail call i64 @_ZN3std2rt10lang_start17h2964b571ece19e55E(void ()* @_ZN6sample4main17h2d3e56a54a8f5081E, i64 %2, i8** %1)
---------------------------------------------
IR:   %4 = trunc i64 %3 to i32
---------------------------------------------
IR:   ret i32 %4
---------------------------------------------
```

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.
