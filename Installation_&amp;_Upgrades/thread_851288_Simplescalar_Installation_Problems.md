---
title: "Simplescalar Installation Problems"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by dplusplus on 2008-07-06
I have gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2) installed.

Then I Was trying to install simplescalar, so i did the following without any error:
tar xvfz simplesim-3v0d.tgz
make config-alpha
make clean

After that i did :
make sim-safe
this gave me error:
machine.h:224: error: array type has incomplete element type
Then i saw in one site, it was instructed:
&#9679; machine.h in simplesim folder - change line 224 from "extern enum md_opcode md_mask2op[];" to "extern enum md_opcode *md_mask2op;" 
&#9679; machine.c in simplesim folder - change line 78 from "enum md_opcode md_mask2op[MD_MAX_MASK+1];" to "enum md_opcode *md_mask2op;
I did the same and then compiled again, and then typed "make sim-safe" again and worked fine with lots of warnings though.

Ok somehow fine till now, and then typed:
./sim-safe ./tests-alpha/bin/test-math
Gave me error:
Segmentation fault (core dumped)

Going by the various forum talks, I can understand till now that it is trying to access some other memory segments, and I need to correct some
pointer addresses maybe. But still can't figure out what exactly am i supossed to do or make any other changes.

Help is kindly needed.

Regards and thanks 

- Dev

---

### Post by zi.coder on 2008-09-13
> **dplusplus said:**
> I have gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2) installed.

Then I Was trying to install simplescalar, so i did the following without any error:
tar xvfz simplesim-3v0d.tgz
make config-alpha
make clean

After that i did :
make sim-safe
this gave me error:
machine.h:224: error: array type has incomplete element type
Then i saw in one site, it was instructed:
&#9679; machine.h in simplesim folder - change line 224 from "extern enum md_opcode md_mask2op[];" to "extern enum md_opcode *md_mask2op;" 
&#9679; machine.c in simplesim folder - change line 78 from "enum md_opcode md_mask2op[MD_MAX_MASK+1];" to "enum md_opcode *md_mask2op;
I did the same and then compiled again, and then typed "make sim-safe" again and worked fine with lots of warnings though.

Ok somehow fine till now, and then typed:
./sim-safe ./tests-alpha/bin/test-math
Gave me error:
Segmentation fault (core dumped)

Going by the various forum talks, I can understand till now that it is trying to access some other memory segments, and I need to correct some
pointer addresses maybe. But still can't figure out what exactly am i supossed to do or make any other changes.

Help is kindly needed.

Regards and thanks 

- Dev

Move the line:
extern enum md_opcode md_mask2op[];

below the definition of md_opcode (about 6 lines below). That should do the trick with gcc 4.x

---

### Post by aiyeou on 2008-10-13
Thanks zi - that worked perfectly with gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Another problem - while compiling for Alpha ISA (make config-alpha) an error:
```
mase-mem.c:134: error: static declaration of &#8216;mem_access_latency&#8217; follows non-static declaration
mase-mem.h:104: error: previous declaration of &#8216;mem_access_latency&#8217; was here 
```

Which was fixed for PISA build by making memory access latency declaration on line 132 of mase-mem.c  non-static as
```
unsigned int			/* total latency of access */
mem_access_latency(int blk_sz)		/* block size accessed */
```

but in case of alpha it compiles and throws an seg fault while running test-math. 

Thanks for any suggestions?

---

### Post by n2ubu on 2009-02-28
hi,
I am installing simplesim-3.0 and following the tutorial guide by Prof. Narahari.
([http://www.seas.gwu.edu/~bhagiweb/cs211/SimpleScalar/simplescalar-linux-install.txt](http://www.seas.gwu.edu/~bhagiweb/cs211/SimpleScalar/simplescalar-linux-install.txt))

while running ./ configure command, I am getting the error.
Please help me

output/error is attached here. 
-----------------
ubuntu@ubuntu:~/simplescalar3$ ls
f2c-1994.09.27         simplesim-2.0d.tar.gz  simpleutils-990811.tar.gz
gcc-2.7.2.3            simplesim-3.0          ssbig-na-sstrix
gcc-2.7.2.3.ss.tar.gz  simplesim-3v0d.tgz     sslittle-na-sstrix
glibc-1.09             simpletools-2v0.tgz
Readme.gcc-2.7.2.3     simpleutils-990811
ubuntu@ubuntu:~/simplescalar3$ pwd
/home/ubuntu/simplescalar3
ubuntu@ubuntu:~/simplescalar3$ export HOST=i386-unknown-linux
ubuntu@ubuntu:~/simplescalar3$ export  IDIR=/home/ubuntu/simplescalar3
ubuntu@ubuntu:~/simplescalar3$ cd $IDIR/simpleutils-990811
ubuntu@ubuntu:~/simplescalar3/simpleutils-990811$ ./configure --host=$HOST --target=sslittle-na-sstrix --with-gnu-as --with-gnu-ld --prefix=$IDIR
Created "Makefile" in /home/ubuntu/simplescalar3/simpleutils-990811
/tmp/cNf13136.pos: line 7: gcc32: command not found
*** The command 'gcc32 -o conftest -g -O2 -W -Wall   conftest.c' failed.
*** You must set the environment variable CC to a working compiler.
ubuntu@ubuntu:~/simplescalar3/simpleutils-990811$
-------------------------------------------------------------------

---

### Post by bakshi.hrishikesh on 2009-03-13
> hi,
I am installing simplesim-3.0 and following the tutorial guide by Prof. Narahari.
([http://www.seas.gwu.edu/~bhagiweb/cs...ux-install.txt](http://www.seas.gwu.edu/~bhagiweb/cs...ux-install.txt))

while running ./ configure command, I am getting the error.
Please help me

output/error is attached here.
-----------------
ubuntu@ubuntu:~/simplescalar3$ ls
f2c-1994.09.27 simplesim-2.0d.tar.gz simpleutils-990811.tar.gz
gcc-2.7.2.3 simplesim-3.0 ssbig-na-sstrix
gcc-2.7.2.3.ss.tar.gz simplesim-3v0d.tgz sslittle-na-sstrix
glibc-1.09 simpletools-2v0.tgz
Readme.gcc-2.7.2.3 simpleutils-990811
ubuntu@ubuntu:~/simplescalar3$ pwd
/home/ubuntu/simplescalar3
ubuntu@ubuntu:~/simplescalar3$ export HOST=i386-unknown-linux
ubuntu@ubuntu:~/simplescalar3$ export IDIR=/home/ubuntu/simplescalar3
ubuntu@ubuntu:~/simplescalar3$ cd $IDIR/simpleutils-990811
ubuntu@ubuntu:~/simplescalar3/simpleutils-990811$ ./configure --host=$HOST --target=sslittle-na-sstrix --with-gnu-as --with-gnu-ld --prefix=$IDIR
Created "Makefile" in /home/ubuntu/simplescalar3/simpleutils-990811
/tmp/cNf13136.pos: line 7: gcc32: command not found
*** The command 'gcc32 -o conftest -g -O2 -W -Wall conftest.c' failed.
*** You must set the environment variable CC to a working compiler.
ubuntu@ubuntu:~/simplescalar3/simpleutils-990811$
-------------------------------------------------------------------

Give your processor configurations.
If it is 64 bit you might have to follow these instructions: [http://harryscode.blogspot.com/2008/10/installing-simplescalar.html](http://harryscode.blogspot.com/2008/10/installing-simplescalar.html)

---

### Post by bakshi.hrishikesh on 2009-03-13
> 
Thanks zi - that worked perfectly with gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Another problem - while compiling for Alpha ISA (make config-alpha) an error:
Code:

mase-mem.c:134: error: static declaration of ‘mem_access_latency’ follows non-static declaration
mase-mem.h:104: error: previous declaration of ‘mem_access_latency’ was here

Which was fixed for PISA build by making memory access latency declaration on line 132 of mase-mem.c non-static as
Code:

unsigned int			/* total latency of access */
mem_access_latency(int blk_sz)		/* block size accessed */

but in case of alpha it compiles and throws an seg fault while running test-math.

Thanks for any suggestions?
Last edited by aiyeou; October 13th, 2008 at 03:00 PM.. Reason: new info 

Install gcc-3.3 instead of 4.2.

```
sudo apt-get install g++-3.3 gcc-3.3 

export CC="gcc-3.3";
```

---

### Post by rohanbk on 2010-02-08
I figured that there was no point in creating a new thread, so I decided to append my problem with SimpleScalar installation. I've reached the stage of the installation where I'm meant to install gcc using the following command:

```
./configure --host=$HOST --target=sslittle-na-sstrix --with-gnu-as --with-gnu-ld --prefix=$IDIR
```

However, I keep getting the same error message and I've exhausted many options for remedying it. I tried re-installing bison, replacing flex with flex-old, and re-installing binutils, but nothing seemed to work. Below are the versions of the files that I was working with, and here is the link to the wiki page I was using [Link]("http://wiki.bigbuddysociety.net/index.php?title=SimpleScalar_3.0")

simplesim-3v0d
simpletools-2v0
simpleutils-990811
gcc-2.7.2.3

```
====== Memory map: ========
08048000-08076000 r-xp 00000000 08:06 359685     /home/rohanbk/ece668/sslittle-na-sstrix/bin/ar
08076000-08077000 r-xp 0002d000 08:06 359685     /home/rohanbk/ece668/sslittle-na-sstrix/bin/ar
08077000-08078000 rwxp 0002e000 08:06 359685     /home/rohanbk/ece668/sslittle-na-sstrix/bin/ar
0967c000-0969d000 rwxp 0967c000 00:00 0          [heap]
40000000-4001c000 r-xp 00000000 08:06 275826     /lib/ld-2.9.so
4001c000-4001d000 r-xp 0001b000 08:06 275826     /lib/ld-2.9.so
4001d000-4001e000 rwxp 0001c000 08:06 275826     /lib/ld-2.9.so
4001e000-4001f000 r-xp 4001e000 00:00 0          [vdso]
4001f000-40021000 rwxp 4001f000 00:00 0 
40021000-40022000 r-xp 00000000 08:06 237234     /usr/lib/locale/en_IN/LC_MESSAGES/SYS_LC_MESSAGES
40022000-40029000 r-xs 00000000 08:06 220846     /usr/lib/gconv/gconv-modules.cache
40029000-4002c000 rwxp 40029000 00:00 0 
40034000-40190000 r-xp 00000000 08:06 74006      /lib/tls/i686/cmov/libc-2.9.so
40190000-40191000 ---p 0015c000 08:06 74006      /lib/tls/i686/cmov/libc-2.9.so
40191000-40193000 r-xp 0015c000 08:06 74006      /lib/tls/i686/cmov/libc-2.9.so
40193000-40194000 rwxp 0015e000 08:06 74006      /lib/tls/i686/cmov/libc-2.9.so
40194000-40198000 rwxp 40194000 00:00 0 
401ab000-401b8000 r-xp 00000000 08:06 269345     /lib/libgcc_s.so.1
401b8000-401b9000 r-xp 0000c000 08:06 269345     /lib/libgcc_s.so.1
401b9000-401ba000 rwxp 0000d000 08:06 269345     /lib/libgcc_s.so.1
bfe98000-bfead000 rw-p bffeb000 00:00 0          [stack]
make: *** [libgcc1.null] Aborted
make: *** Deleting file `libgcc1.null
```'

---

### Post by WatchMaker7 on 2010-02-18
I ran into the same problem. Its the result of -D_FORTIFY_SOURCE which was enabled in version 8.10. I tried switching to an earlier version of gcc and disabling the check by putting                  -U_FORTIFY_SOURCE or -D_FORTIFY_SOURCE=0 in CPPFLAGS as is suggested here [https://wiki.ubuntu.com/CompilerFlags](https://wiki.ubuntu.com/CompilerFlags). However, neither of those things fixed the problem. What I wound up doing was installing an old version of Ubuntu on a separate partition and just not letting it update past version 8.04. The install worked like a charm then. 
This isn't a real fix though, so if someone figures out how to actually disable the check for simplescalar, please share.

---

