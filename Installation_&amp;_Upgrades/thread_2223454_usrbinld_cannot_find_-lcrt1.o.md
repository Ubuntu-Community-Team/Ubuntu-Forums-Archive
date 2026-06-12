---
title: "/usr/bin/ld: cannot find -lcrt1.o"
date: 2014-05-11
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2014-05-11
Hi, I am trying to compile a program suite and get the message:
/usr/bin/ld: cannot find -lcrt1.o

(under Ubuntu 12.04, gcc-4.8.1)

I understand that I am missing a library but which one??? Searches fo 'lcrt' or 'libcrt' only give me something on remote control which has nothing to do with this program. Here an example of one of many:

"/usr/bin/ld: cannot find -lcrt1.o
collect2: error: ld returned 1 exit status
make: *** [simple_test_equal] Fehler 1
cp: der Aufruf von stat für »simple_test_equal“ ist nicht möglich: Datei oder Verzeichnis nicht gefunden"

I suppose the following lines are the product of the first problem, namely that lcrt1, or whatever it is part of is missing!

Thanks for hints, D-E

---

### Post by matt_symes on 2014-05-11
Hi

What sotware suite are you trying to compile ?

Can you provide a link so we can take a look ?

Kind regards

---

### Post by WigginsACK on 2014-05-11
Sudo apt-get install libc6-dev

Does that fix it?

---

### Post by dieter-erich on 2014-05-11
Thanks,
   1) it is an electron microscopy image reconstruction software suite whose ß-version a colleague provided me with. I want to get it compiled myself without bothering him.
    2) I have already the latest version of  libc6-dev installed.
I am wondering how one can find out which library is missing from such cryptic messages....

---

### Post by steeldriver on 2014-05-11
Can you give us some more context about the error message e.g. the actual compiler command line that's causing the error? 

Also is your platform 32-bit or 64-bit?

---

### Post by dieter-erich on 2014-05-14
Hi, some new info:

I was able to compile the program on my nettop running 32 bit ubuntu-12.04. Strangely, the compiler output lacked the "-lcrt1.o" and the binary was created. The output of 'ldd' on the functioning installation is:

ldd simple_prime 
    linux-gate.so.1 =>  (0x00867000)
    libgfortran.so.3 => /usr/lib/i386-linux-gnu/libgfortran.so.3 (0x003f6000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0x00c63000)
    libgomp.so.1 => /usr/lib/i386-linux-gnu/libgomp.so.1 (0x00cf7000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x00e52000)
    libquadmath.so.0 => /usr/lib/i386-linux-gnu/libquadmath.so.0 (0x00a63000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0x00585000)
    /lib/ld-linux.so.2 (0x00325000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0x00839000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0x00155000)

I suppose that my other PCs (one running Centos 6.5 and two running Ubuntu 10.04 (32 bit and 64 bit, but with gcc-4.8 and gfortran-4.8 installed !) lack a particular library or a wrong library becomes linked. What would be the corresponding libraries suitable for these systems? 

I also find it strange that '-lcrt1.o' is not present in the output line of the compiler when the compilation runs smoothly. 
In the functioning installation crt1.o is present here:

locate crt1.o
/usr/lib/i386-linux-gnu/Mcrt1.o
/usr/lib/i386-linux-gnu/Scrt1.o
/usr/lib/i386-linux-gnu/crt1.o
/usr/lib/i386-linux-gnu/gcrt1.o
/usr/lib64/Mcrt1.o
/usr/lib64/Scrt1.o
/usr/lib64/crt1.o
/usr/lib64/gcrt1.o

In the non-functioning installation it is here:

/usr/lib/Mcrt1.o
/usr/lib/Scrt1.o
/usr/lib/crt1.o
/usr/lib/gcrt1.o

No idea whether this might have anything to do with the problem. In particular, because it says "-lcrt1.o" and not "crt1.o". Is crt1.o part of a library, but if so, which one? I have tried installing libraries with similar names but this did not change anything......

Thanks for hints!

---

### Post by dieter-erich on 2014-05-14
SOLVED! 
I was told by a specialist that -lcrt1.o was not needed in the compilation script. On removing it everything now runs smoothly.
Thanks for your willingness to help, D-E

---

