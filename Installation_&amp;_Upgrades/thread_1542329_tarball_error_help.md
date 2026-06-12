---
title: "tarball error help"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by wookiesteve on 2010-07-30
basically i followed all the instructions i could find and have been looking for why this isn't working and cant find out why any help would be appreciated. this is what i do in the command prompt and the response that i get.

nunuabiznus@nunuabiznus:~$ cd /home/nunuabiznus/Downloads/lkl-0.1.1.tar.gz
bash: cd: /home/nunuabiznus/Downloads/lkl-0.1.1.tar.gz: Not a directory
nunuabiznus@nunuabiznus:~$ cd /home/nunuabiznus/Downloads/lkl
nunuabiznus@nunuabiznus:~/Downloads/lkl$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets ${MAKE}... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking string.h, usability... no
checking string.h, presence... no
checking for string.h,... no
checking stdio.h, usability... no
checking stdio.h, presence... no
checking for stdio.h,... no
checking sys/io.h usability... yes
checking sys/io.h presence... yes
checking for sys/io.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
nunuabiznus@nunuabiznus:~/Downloads/lkl$ make
cd . \
	  && CONFIG_FILES= CONFIG_HEADERS=config.h \
	     /bin/bash ./config.status
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
make  all-am
make[1]: Entering directory `/home/nunuabiznus/Downloads/lkl'
make[1]: Leaving directory `/home/nunuabiznus/Downloads/lkl'
nunuabiznus@nunuabiznus:~/Downloads/lkl$ make check
nunuabiznus@nunuabiznus:~/Downloads/lkl$ make install
make[1]: Entering directory `/home/nunuabiznus/Downloads/lkl'
/bin/bash ./mkinstalldirs /usr/local/bin
  /usr/bin/install -c lkl /usr/local/bin/lkl
/usr/bin/install: cannot create regular file `/usr/local/bin/lkl': Permission denied
make[1]: *** [install-binPROGRAMS] Error 1
make[1]: Leaving directory `/home/nunuabiznus/Downloads/lkl'
make: *** [install-am] Error 2
nunuabiznus@nunuabiznus:~/Downloads/lkl$

---

### Post by oldos2er on 2010-07-30
"/usr/bin/install: cannot create regular file `/usr/local/bin/lkl': Permission denied"

Run **sudo make install** to have the necessary permissions to write to /usr/local/bin.

---

