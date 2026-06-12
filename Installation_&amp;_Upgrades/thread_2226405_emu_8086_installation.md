---
title: "emu 8086 installation"
date: 2014-05-27
forum: Installation &amp; Upgrades
---

### Post by showmik on 2014-05-27
i am using Ubuntu 14.04 LTS. i want to install emu8086 for assembly language programming.
i am so tired to find this emu8086 program. please help me to solve this problem.... :( :( :(

---

### Post by gordintoronto on 2014-05-27
emu8086 is a Windows program. Have you looked at nasm, from the repositories?

---

### Post by showmik on 2014-05-30
yup, i have installed nasm but i can't able to access it...
can you help me to find a assembly language compilear for ubuntu 14.04 LTS...
please help me. i need your help so badly.. :(

---

### Post by mcduck on 2014-05-30
I just tested installing nasm from Ubuntu's repositories (on 14.04) and it seems to be working fine. What kind of problem are you having accessing it?

It is a command-line application, so if you just couldn't find it in the menus then that would explain it...

---

### Post by showmik on 2014-05-30
i have installed nasm. i can find it. how become it will be run...

[U][I][B][SIZE=4]in terminal, i input

nasm -h[/SIZE][/B][/I][/U]

then show:
usage: nasm [-@ response file] [-o outfile] [-f format] [-l listfile]
            [options...] [--] filename
    or nasm -v   for version info


    -t          assemble in SciTech TASM compatible mode
    -g          generate debug information in selected format
    -E (or -e)  preprocess only (writes output to stdout by default)
    -a          don't preprocess (assemble only)
    -M          generate Makefile dependencies on stdout
    -MG         d:o, missing files assumed generated
    -MF <file>  set Makefile dependency file
    -MD <file>  assemble and generate dependencies
    -MT <file>  dependency target name
    -MQ <file>  dependency target name (quoted)
    -MP         emit phony target


    -Z<file>    redirect error messages to file
    -s          redirect error messages to stdout


    -F format   select a debugging format


    -o outfile  write output to an outfile


    -f format   select an output format


    -l listfile write listing to a listfile


    -I<path>    adds a pathname to the include file path
    -O<digit>   optimize branch offsets
                -O0: No optimization
                -O1: Minimal optimization
                -Ox: Multipass optimization (default)


    -P<file>    pre-includes a file
    -D<macro>[=<value>] pre-defines a macro
    -U<macro>   undefines a macro
    -X<format>  specifies error reporting format (gnu or vc)
    -w+foo      enables warning foo (equiv. -Wfoo)
    -w-foo      disable warning foo (equiv. -Wno-foo)


    -h          show invocation summary and exit


--prefix,--postfix
  this options prepend or append the given argument to all
  extern and global variables


Warnings:
    error                   treat warnings as errors (default off)
    macro-params            macro calls with wrong parameter count (default on)
    macro-selfref           cyclic macro references (default off)
    macro-defaults          macros with more default than optional parameters (default on)
    orphan-labels           labels alone on lines without trailing `:' (default on)
    number-overflow         numeric constant does not fit (default on)
    gnu-elf-extensions      using 8- or 16-bit relocation in ELF32, a GNU extension (default off)
    float-overflow          floating point overflow (default on)
    float-denorm            floating point denormal (default off)
    float-underflow         floating point underflow (default off)
    float-toolong           too many digits in floating-point number (default on)
    user                    %warning directives (default on)
    lock                    lock prefix on unlockable instructions (default on)
    hle                     invalid hle prefixes (default on)


response files should contain command line parameters, one per line.


For a list of valid output formats, use -hf.
For a list of debug formats, use -f <form> -y.
[U][I][B]
[SIZE=4]than again input : man nasm[/SIZE][/B][/I][/U]

shows:
usage: nasm [-@ response file] [-o outfile] [-f format] [-l listfile]
            [options...] [--] filename
    or nasm -v   for version info


    -t          assemble in SciTech TASM compatible mode
    -g          generate debug information in selected format
    -E (or -e)  preprocess only (writes output to stdout by default)
    -a          don't preprocess (assemble only)
    -M          generate Makefile dependencies on stdout
    -MG         d:o, missing files assumed generated
    -MF <file>  set Makefile dependency file
    -MD <file>  assemble and generate dependencies
    -MT <file>  dependency target name
    -MQ <file>  dependency target name (quoted)
    -MP         emit phony target


    -Z<file>    redirect error messages to file
    -s          redirect error messages to stdout


    -F format   select a debugging format


    -o outfile  write output to an outfile


    -f format   select an output format


    -l listfile write listing to a listfile


    -I<path>    adds a pathname to the include file path
    -O<digit>   optimize branch offsets
                -O0: No optimization
                -O1: Minimal optimization
                -Ox: Multipass optimization (default)


    -P<file>    pre-includes a file
    -D<macro>[=<value>] pre-defines a macro
    -U<macro>   undefines a macro
    -X<format>  specifies error reporting format (gnu or vc)
    -w+foo      enables warning foo (equiv. -Wfoo)
    -w-foo      disable warning foo (equiv. -Wno-foo)


    -h          show invocation summary and exit


--prefix,--postfix
  this options prepend or append the given argument to all
  extern and global variables


Warnings:
    error                   treat warnings as errors (default off)
    macro-params            macro calls with wrong parameter count (default on)
    macro-selfref           cyclic macro references (default off)
    macro-defaults          macros with more default than optional parameters (default on)
    orphan-labels           labels alone on lines without trailing `:' (default on)
    number-overflow         numeric constant does not fit (default on)
    gnu-elf-extensions      using 8- or 16-bit relocation in ELF32, a GNU extension (default off)
    float-overflow          floating point overflow (default on)
    float-denorm            floating point denormal (default off)
    float-underflow         floating point underflow (default off)
    float-toolong           too many digits in floating-point number (default on)
    user                    %warning directives (default on)
    lock                    lock prefix on unlockable instructions (default on)
    hle                     invalid hle prefixes (default on)


response files should contain command line parameters, one per line.


For a list of valid output formats, use -hf.
For a list of debug formats, use -f <form> -y.

---

### Post by mcduck on 2014-05-30
This should be helpful for how to use nasm: [http://docs.cs.up.ac.za/programming/asm/derick_tut/#compiling]("http://docs.cs.up.ac.za/programming/asm/derick_tut/#compiling")

---

