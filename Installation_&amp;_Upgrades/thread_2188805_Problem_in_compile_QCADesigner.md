---
title: "Problem in compile QCADesigner"
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by unname-phoenix-j on 2013-11-19
Hello

I want to complie QCADesigner in my ubuntu .

This is the content of INSTALL file in source folder :

```
[COLOR=#000000][FONT=dejavu sans mono]Basic Installation[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]==================[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   These are generic installation instructions.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   The `configure' shell script attempts to guess correct values for[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]various system-dependent variables used during compilation.  It uses[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]those values to create a `Makefile' in each directory of the package.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]It may also create one or more `.h' files containing system-dependent[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]definitions.  Finally, it creates a shell script `config.status' that[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]you can run in the future to recreate the current configuration, a file[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]`config.cache' that saves the results of its tests to speed up[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]reconfiguring, and a file `config.log' containing compiler output[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono](useful mainly for debugging `configure').[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   If you need to do unusual things to compile the package, please try[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]to figure out how `configure' could check whether to do them, and mail[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]diffs or instructions to the address given in the `README' so they can[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]be considered for the next release.  If at some point `config.cache'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]contains results you don't want to keep, you may remove or edit it.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   The file `configure.in' is used to create `configure' by a program[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]called `autoconf'.  You only need `configure.in' if you want to change[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]it or regenerate `configure' using a newer version of `autoconf'.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]The simplest way to compile this package is:[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]  1. `cd' to the directory containing the package's source code and type[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     `./configure' to configure the package for your system.  If you're[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     using `csh' on an old version of System V, you might need to type[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     `sh ./configure' instead to prevent `csh' from trying to execute[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     `configure' itself.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]     Running `configure' takes awhile.  While running, it prints some[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     messages telling which features it is checking for.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]  2. Type `make' to compile the package.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]  3. Optionally, type `make check' to run any self-tests that come with[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     the package.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]  4. Type `make install' to install the programs and any data files and[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     documentation.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]  5. You can remove the program binaries and object files from the[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     source code directory by typing `make clean'.  To also remove the[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     files that `configure' created (so you can compile the package for[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     a different kind of computer), type `make distclean'.  There is[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     also a `make maintainer-clean' target, but that is intended mainly[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     for the package's developers.  If you use it, you may have to get[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     all sorts of other programs in order to regenerate files that came[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     with the distribution.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Compilers and Options[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]=====================[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   Some systems require unusual options for compilation or linking that[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]the `configure' script does not know about.  You can give `configure'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]initial values for variables by setting them in the environment.  Using[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]a Bourne-compatible shell, you can do that on the command line like[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]this:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     CC=c89 CFLAGS=-O2 LIBS=-lposix ./configure[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Or on systems that have the `env' program, you can do it like this:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     env CPPFLAGS=-I/usr/local/include LDFLAGS=-s ./configure[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Compiling For Multiple Architectures[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]====================================[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   You can compile the package for more than one kind of computer at the[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]same time, by placing the object files for each architecture in their[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]own directory.  To do this, you must use a version of `make' that[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]supports the `VPATH' variable, such as GNU `make'.  `cd' to the[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]directory where you want the object files and executables to go and run[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]the `configure' script.  `configure' automatically checks for the[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]source code in the directory that `configure' is in and in `..'.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   If you have to use a `make' that does not supports the `VPATH'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]variable, you have to compile the package for one architecture at a time[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]in the source code directory.  After you have installed the package for[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]one architecture, use `make distclean' before reconfiguring for another[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]architecture.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Installation Names[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]==================[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   By default, `make install' will install the package's files in[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]`/usr/local/bin', `/usr/local/man', etc.  You can specify an[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]installation prefix other than `/usr/local' by giving `configure' the[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]option `--prefix=PATH'.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   You can specify separate installation prefixes for[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]architecture-specific files and architecture-independent files.  If you[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]give `configure' the option `--exec-prefix=PATH', the package will use[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]PATH as the prefix for installing programs and libraries.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Documentation and other data files will still use the regular prefix.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   In addition, if you use an unusual directory layout you can give[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]options like `--bindir=PATH' to specify different values for particular[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]kinds of files.  Run `configure --help' for a list of the directories[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]you can set and what kinds of files go in them.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   If the package supports it, you can cause programs to be installed[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]with an extra prefix or suffix on their names by giving `configure' the[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]option `--program-prefix=PREFIX' or `--program-suffix=SUFFIX'.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Optional Features[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]=================[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   Some packages pay attention to `--enable-FEATURE' options to[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]`configure', where FEATURE indicates an optional part of the package.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]They may also pay attention to `--with-PACKAGE' options, where PACKAGE[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]is something like `gnu-as' or `x' (for the X Window System).  The[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]`README' should mention any `--enable-' and `--with-' options that the[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]package recognizes.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   For packages that use the X Window System, `configure' can usually[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]find the X include and library files automatically, but if it doesn't,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]you can use the `configure' options `--x-includes=DIR' and[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]`--x-libraries=DIR' to specify their locations.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Specifying the System Type[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]==========================[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   There may be some features `configure' can not figure out[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]automatically, but needs to determine by the type of host the package[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]will run on.  Usually `configure' can figure that out, but if it prints[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]a message saying it can not guess the host type, give it the[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]`--host=TYPE' option.  TYPE can either be a short name for the system[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]type, such as `sun4', or a canonical name with three fields:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     CPU-COMPANY-SYSTEM[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]See the file `config.sub' for the possible values of each field.  If[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]`config.sub' isn't included in this package, then this package doesn't[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]need to know the host type.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   If you are building compiler tools for cross-compiling, you can also[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]use the `--target=TYPE' option to select the type of system they will[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]produce code for and the `--build=TYPE' option to select the type of[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]system on which you are compiling the package.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Sharing Defaults[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]================[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   If you want to set default values for `configure' scripts to share,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]you can create a site shell script called `config.site' that gives[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]default values for variables like `CC', `cache_file', and `prefix'.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]`configure' looks for `PREFIX/share/config.site' if it exists, then[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]`PREFIX/etc/config.site' if it exists.  Or, you can set the[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]`CONFIG_SITE' environment variable to the location of the site script.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]A warning: not all `configure' scripts look for a site script.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Operation Controls[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]==================[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]   `configure' recognizes the following options to control how it[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]operates.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]`--cache-file=FILE'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     Use and save the results of the tests in FILE instead of[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     `./config.cache'.  Set FILE to `/dev/null' to disable caching, for[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     debugging `configure'.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]`--help'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     Print a summary of the options to `configure', and exit.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]`--quiet'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]`--silent'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]`-q'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     Do not print messages saying which checks are being made.  To[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     suppress all normal output, redirect it to `/dev/null' (any error[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     messages will still be shown).[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]`--srcdir=DIR'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     Look for the package's source code in directory DIR.  Usually[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     `configure' can determine that directory automatically.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]`--version'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     Print the version of Autoconf used to generate the `configure'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]     script, and exit.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]`configure' also accepts some other, not widely useful, options.[/FONT][/COLOR]
```

I ran following commands respectively :

```
[COLOR=#000000][FONT=dejavu sans mono]$ ./autogen.sh[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]$ autoconf configure.in [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]$ ./configure[/FONT][/COLOR]
``` 

None of the above commands did not return error in output but after i ran 'MAKE' command after about one min that 'MAKE' command return output i got this error : 

```
[COLOR=#000000][FONT=dejavu sans mono]Making check in src[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[1]: Entering directory `/home/woeful/Desktop/QCADesigner-2.0.3/src'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[1]: Nothing to be done for `check'.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[1]: Leaving directory `/home/woeful/Desktop/QCADesigner-2.0.3/src'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Making check in po[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[1]: Entering directory `/home/woeful/Desktop/QCADesigner-2.0.3/po'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]file=./`echo de | sed 's,.*/,,'`.gmo \[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]	[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]  && rm -f $file && /usr/bin/msgfmt -c -o $file de.po[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]/usr/bin/msgfmt: de.po: warning: PO file header missing or invalid[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                        warning: charset conversion will not work[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]/usr/bin/msgfmt: found 1 fatal error[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[1]: *** [de.gmo] Error 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[1]: Leaving directory `/home/woeful/Desktop/QCADesigner-2.0.3/po'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make: *** [check-recursive] Error 1[/FONT][/COLOR]
```


&#1615;Thanks

---

