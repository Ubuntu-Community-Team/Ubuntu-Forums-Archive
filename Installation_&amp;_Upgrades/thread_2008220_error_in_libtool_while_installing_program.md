---
title: "error in libtool while installing program"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by narendrapatel on 2012-06-22
hii,
 i'm installing a program named shallow-parser-hin-3.0 and during installation i got the following error..



make[1]: Leaving directory `/home/naren/sampark/shallow_parser_hin/bin/sl/CRF++-0.51'
make[1]: Entering directory `/home/naren/sampark/shallow_parser_hin/bin/sl/CRF++-0.51'
cd . && /bin/bash /home/naren/sampark/shallow_parser_hin/bin/sl/CRF++-0.51/missing --run autoheader
rm -f stamp-h1
touch config.h.in
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
make  all-am
make[2]: Entering directory `/home/naren/sampark/shallow_parser_hin/bin/sl/CRF++-0.51'
/bin/bash ./libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I.     -O3 -Wall -Wno-deprecated -mieee-fp -c -o libcrfpp.lo libcrfpp.cpp
./libtool: line 698: X--tag=CXX: command not found
./libtool: line 731: libtool: ignoring unknown tag : command not found
./libtool: line 698: X--mode=compile: command not found
./libtool: line 848: *** Warning: inferring the mode of operation is deprecated.: command not found
./libtool: line 849: *** Future versions of Libtool will require -mode=MODE be specified.: command not found
./libtool: line 992: Xg++: command not found
./libtool: line 992: X-DHAVE_CONFIG_H: command not found
./libtool: line 992: X-I.: command not found
./libtool: line 992: X-O3: command not found
./libtool: line 992: X-Wall: command not found
./libtool: line 992: X-Wno-deprecated: command not found
./libtool: line 992: X-mieee-fp: command not found
./libtool: line 992: X-c: command not found
./libtool: line 1040: Xlibcrfpp.lo: command not found
./libtool: line 1045: libtool: compile: cannot determine name of library object from `': command not found
make[2]: *** [libcrfpp.lo] Error 1
make[2]: Leaving directory `/home/naren/sampark/shallow_parser_hin/bin/sl/CRF++-0.51'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/naren/sampark/shallow_parser_hin/bin/sl/CRF++-0.51'
make: *** [install] Error 2


if anybody has solution to this problem please give the solution as soon as possible..
thanking you..

---

### Post by dino99 on 2012-06-22
seems like you need to use a different libtool release

dont you have a README with that app or a txt or so to explain how to install it ?

---

### Post by narendrapatel on 2012-06-26
thanks dino99 for your concern, 
there is one install file which gives u instruction how to install it and it says as given below:-


Basic Installation
==================

Follow the below Steps : 

  1) untar the binary package of shallow-parser-hin-3.0.tgz
    
        tar -xvzf shallow-parser-hin-3.0.tgz

  2) `cd' to the directory containing the package binary.

    cd shallow-parser-hin-3.0

  3.1) Export the Variable `SHALLOW_PARSER_HIN'.
 
       echo "export SHALLOW_PARSER_HIN=~/sampark/shallow_parser_hin" >> ~/.bashrc

  3.2) Set the PATH to the SHALLOW_PARSER_HIN/bin/sl/sys/hin

       echo "export PATH=\$PATH:\$SHALLOW_PARSER_HIN/bin/sys/hin/" >> ~/.bashrc

  3.3) Compile the ~/.bashrc
  
       source ~/.bashrc

  4)   To Install 
       Type `make install' to install the programs, data files and
       documentation.
                   
    make install

 For how to use shallow parser for hindi, please refer to the file README-user.

 To Uninstall 
 -- ---------

     If you want to remove the program binaries and object files from the
     binary package directory type `make uninstall'. 

      make uninstall 

you can get this application from url
[http://ltrc.iiit.ac.in/showfile.php?filename=downloads/shallow_parser.php](http://ltrc.iiit.ac.in/showfile.php?filename=downloads/shallow_parser.php)
app is the hindi one

it will be your generous work for me if you can install and give some solution to the above problem..
thank you.

---

### Post by dino99 on 2012-06-26
do you have set libtool as it might ?

To use libtool, add the
new generic library building commands to your Makefile, Makefile.in,
or Makefile.am.  See the documentation for details.  (synaptic libtool details)

do you have the required packages for compiling ?
(automake, autoconf, build-essential & the kernel headers)

and if the problem persist, try with a different release as said previously (but uninstall the actual libtool first before trying an other release)

[http://packages.ubuntu.com/en/lucid/libtool](http://packages.ubuntu.com/en/lucid/libtool)

---

### Post by narendrapatel on 2012-07-02
hi dino99,
i have tried everything what you have suggested in the same manner as you asked but nothing improved. the error is still as it is.
 If you don't mind, can you please do install the app in your system and find some solution to the problem.
thanks

---

### Post by narendrapatel on 2012-07-09
> **dino99 said:**
> do you have set libtool as it might ?

To use libtool, add the
new generic library building commands to your Makefile, Makefile.in,
or Makefile.am.  See the documentation for details.  (synaptic libtool details)

do you have the required packages for compiling ?
(automake, autoconf, build-essential & the kernel headers)

and if the problem persist, try with a different release as said previously (but uninstall the actual libtool first before trying an other release)

[http://packages.ubuntu.com/en/lucid/libtool](http://packages.ubuntu.com/en/lucid/libtool)
hi dino99,
i have tried everything what you have suggested in the same manner as  you asked but nothing improved. the error is still as it is.
 If you don't mind, can you please do install the app in your system and find some solution to the problem.
thanks

---

