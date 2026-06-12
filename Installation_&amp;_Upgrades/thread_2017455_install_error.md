---
title: "install error"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by tripti56 on 2012-07-05
hello,
I am trying to install shallow-parser-hin-3.0.And when i use the make install command it gives me error:
**I**n file included from node.h:13:0,
                 from node.cpp:9:
path.h:26:52: error: 'size_t' has not been declared
make[2]: *** [node.lo] Error 1
make[2]: Leaving directory `/home/tripti/sampark/shallow_parser_hin/bin/sl/CRF++-0.51'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/tripti/sampark/shallow_parser_hin/bin/sl/CRF++-0.51'
make: *** [install] Error 2
:confused:

I have upgraded everything what all needed for it even then i m getting this problem.
Here are the instructions that are needed to be followed:

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

4) To Install 
Type `make install' to install the programs, data files and
documentation.

make install

For how to use shallow parser for hindi, please refer to the file README-user.

To Uninstall 
-- ---------

If you want to remove the program binaries and object files from the
binary package directory type `make uninstall'. 

make uninstall


can anyone help me in this matter.
Thanks in advance:)

---

### Post by dino99 on 2012-07-05
Seems there is some mistery with this app  ;)

[http://www.google.com/search?q=shallow-parser-hin-3.0](http://www.google.com/search?q=shallow-parser-hin-3.0)

---

### Post by tripti56 on 2012-07-10
wat is dis???

---

