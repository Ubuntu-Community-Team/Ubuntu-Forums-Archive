---
title: "make &amp; make install confusion"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by dwebb86 on 2007-07-12
ok, I'm trying to install rainbowcrack or ophcrack, or both. 
I have johntheripper installed, but I'm trying to use this laptop as a portable security center, and I am installing as many apps as I can so I can learn to use them all and hit up security issues from all angles. 
I'm pretty new to linux, only about a month under my belt. 
Either I'm just doing something stupid, or I'm missing a vital part for these commands to work.

for Ophcrack the linux install directions are as follows:
[B]The linux version is a source package. It can be compiled and 
installed using the "./configure", "make" and "make install"
commands. The tables have to be downloaded by hand, from the URL given
above.[/B]
I change to the ophcrack folder directory, do **./configure**, and get this: 
[B]XXXX@XXXX:/home/XXXX/Desktop/ophcrack-2.4# ./configurechecking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/XXXX/Desktop/ophcrack-2.4/missing: Unknown `--run' option
Try `/home/XXXX/Desktop/ophcrack-2.4/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
./configure: line 5528: syntax error near unexpected token `2.4.0,'
./configure: line 5528: `AM_PATH_GTK_2_0(2.4.0, , { { echo "$as_me:$LINENO: error:'
[/B]

and, I can't run **make** from there.

for Rainbowcrack the linux install directions are as follows:
[B]RainbowCrack 1.2 source



openssl is required to build the source



build the source in windows:

	nmake -f makefile.win



build the source in linux:

	make -f makefile.linux[/B]

after changing to the rainbowcrack **src** folder and doing **make -f makefile.linux** I get this:

[B]XXXX@XXXX:/home/XXXX/Desktop/tools/rainbowcrack-1.2-src/src# make -f makefile.linux
g++ Public.cpp ChainWalkContext.cpp HashAlgorithm.cpp HashRoutine.cpp RainbowTableGenerate.cpp -lssl -O3 -o rtgen
ChainWalkContext.cpp:14:26: error: openssl/rand.h: No such file or directory
ChainWalkContext.cpp: In member function ‘void CChainWalkContext::GenerateRandomIndex()’:
ChainWalkContext.cpp:348: error: ‘RAND_bytes’ was not declared in this scope
HashAlgorithm.cpp:9:25: error: openssl/des.h: No such file or directory
HashAlgorithm.cpp:10:25: error: openssl/md5.h: No such file or directory
HashAlgorithm.cpp:11:25: error: openssl/sha.h: No such file or directory
HashAlgorithm.cpp:16: error: ‘des_key_schedule’ has not been declared
HashAlgorithm.cpp: In function ‘void setup_des_key(unsigned char*, int&)’:
HashAlgorithm.cpp:18: error: ‘des_cblock’ was not declared in this scope
HashAlgorithm.cpp:18: error: expected `;' before ‘key’
HashAlgorithm.cpp:20: error: ‘key’ was not declared in this scope
HashAlgorithm.cpp:30: error: ‘des_set_key’ was not declared in this scope
HashAlgorithm.cpp: In function ‘void HashLM(unsigned char*, int, unsigned char*)’:
HashAlgorithm.cpp:45: error: ‘des_key_schedule’ was not declared in this scope
HashAlgorithm.cpp:45: error: expected `;' before ‘ks’
HashAlgorithm.cpp:47: error: ‘ks’ was not declared in this scope
HashAlgorithm.cpp:48: error: ‘des_cblock’ was not declared in this scope
HashAlgorithm.cpp:48: error: expected primary-expression before ‘)’ token
HashAlgorithm.cpp:48: error: expected primary-expression before ‘)’ token
HashAlgorithm.cpp:48: error: ‘DES_ENCRYPT’ was not declared in this scope
HashAlgorithm.cpp:48: error: ‘des_ecb_encrypt’ was not declared in this scope
HashAlgorithm.cpp: In function ‘void HashMD5(unsigned char*, int, unsigned char*)’:
HashAlgorithm.cpp:53: error: ‘MD5’ was not declared in this scope
HashAlgorithm.cpp: In function ‘void HashSHA1(unsigned char*, int, unsigned char*)’:
HashAlgorithm.cpp:58: error: ‘SHA1’ was not declared in this scope
make: *** [rtgen] Error 1
[/B]

and that's that. 

anyone out there have any ideas? I'm probably just doing something dumb. thanks for helping.

---

### Post by linuxwizard on 2007-07-13
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by t3rror on 2007-07-24
I would suggest installing the **libssl-dev** and **libcurl13-openssl-dev** packages.  I believe this will satisfy your dependencies.  I just ran across the same issue while trying to compile rainbowcrack, and after installing these files along with their dependencies, I was able to configure the compile without issue.

---

### Post by DeHorde on 2008-03-13
Just to add to t3rrors answer, on gutsy that would be:
```
sudo apt-get install libssl-dev libcurl4-openssl-dev
```

---

### Post by zvacet on 2008-03-13
Open terminal and go to the directory where you downloaded source package and type 

```
sudo apt-get build-dep **package_name**
```

package_name = exact name of your package.This command should satisfied dependencies.

---

