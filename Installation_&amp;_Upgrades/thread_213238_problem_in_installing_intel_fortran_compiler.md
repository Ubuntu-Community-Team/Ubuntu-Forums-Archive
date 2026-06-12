---
title: "problem in installing intel fortran compiler"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by hadian on 2006-07-11
Hi
i want to install Intel Fortran Compiler on Ubuntu dapper, but it fails. after unpacking the pakage and running the installer script, i got some  warnings. here is what i did:
```
reza@reza-laptop:~/tmp_install/l_fc_p_9.0.021$ sudo ./install.sh



**********************************************************************
"Welcome to Installation"

Please make your selection by entering an option:

1. "Intel(R) Fortran Compiler 9.0 for Linux*" - install

        1a. Readme
        1b. Release Notes
        1c. Installation Guide
        1d. Product Web Site URL
        1e. Intel(R) Support Web Site URL

x. Exit.

Please type a selection  :   1

======================================================================

Please select an option to continue:
        1. Proceed with Serial Number to install and register. [Recommended]
        2. Provide name of an existing license file.
        x. Exit.

Please type your selection  :   2

======================================================================

Please provide the license file name with full path (*.lic)
        x.Exit

License file path  :   /opt/intel/licenses/noncommercial_for_l_NJ24-MNSFKJZM.lic
Checking RPM version ...

Checking Dependencies ...
Checking Kernel and glibc dependencies ...

install_fc.sh can't identify your machine type, glibc, or kernel.

This product is supported for use with the following combinations   :

    Machine Type                Kernel  glibc

1.  IA-32/EM64T                 2.4.x   2.2.5
    IA-32/EM64T                 2.4.x   2.2.4
    IA-32/EM64T                 2.4.x   2.2.93
    IA-32/EM64T                 2.4.x   2.3.2
    IA-32/EM64T                 2.6.x   2.3.x
    IA-32/EM64T                 2.6.x   2.4.x

x.  Exit

If you would you like to perform an unsupported install of this product, enter the number corresponding to the platform most similar to yours. Otherwise, enter "x" to exit   :   1
find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

```
and if i continue the installation i get:
```
Intel(R) Fortran Compiler for 32-bit applications, Version 9.0
Installing...
Installation failed.

```
it should be noted that i could install it without any problem on [ubuntu 5.10 ](http://www.ubuntuforums.org/showthread.php?t=89571&highlight=intel+fortran)
and [this instruction ](http://www.ubuntuforums.org/showthread.php?t=169664&highlight=intel+fortran) did not work and gave me this error:
```
./make9: line 7: setenv: command not found
./make9: line 9: syntax error near unexpected token `)'
./make9: line 9: `if ( { test -z $DEBFILE } ) then'
```
could anybody let me know how to install this compiler?
Regards,
Hadian

---

### Post by hadian on 2006-08-05
i found the solution so i link it here, maybe it is useful for others.
[http://ubuntuforums.org/showthread.php?t=179589&page=2](http://ubuntuforums.org/showthread.php?t=179589&page=2)

---

