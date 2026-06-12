---
title: "how to install a makefile"
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by dirkwillem on 2011-12-08
Hello

I want to install a makefile in this location:
/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/Makefile
so, I hit this in the terminal:

```
/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/ make
```

but it says the file isnt there. I also know i am doing something wrong, but how do I install my makefile?(Yes I know this sounds very noobisch, but I just dont have experience with the Ubuntu terminal, only with C++)

Any help is appreciated
DirkWillem

---

### Post by searchfgold6789 on 2011-12-08
Hello,
You'll have to change the working directory first. These commands should work:
```
cd /home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/
make
```

---

### Post by dirkwillem on 2011-12-09
Thanks, it worked. But it gave an error 2 after I installed, and when I tried again it gave this


```
dirk@ubuntu:~$ cd /home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/
dirk@ubuntu:~/Bureaublad/GBA/DevkitAdvance/devkitadv$ make
make -w install-binutils
make[1]: Entering directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv'
( \
	STRIPPROG=/usr/bin/strip; \
	cd build-binutils && \
	make -w install INSTALL_PROGRAM_ARGS="-s" \
	)
make[2]: Entering directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/build-binutils'
/bin/sh ../binutils-2.12.1/mkinstalldirs /usr/local/devkitadv /usr/local/devkitadv
mkdir /usr/local/devkitadv
mkdir /usr/local/devkitadv
make[2]: *** [installdirs] Error 1
make[2]: Leaving directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/build-binutils'
make[1]: *** [install-binutils] Error 2
make[1]: Leaving directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv'
make: *** [stmp-binutils-make-install] Error 2
dirk@ubuntu:~/Bureaublad/GBA/DevkitAdvance/devkitadv
```

Does someone know what is going wrong?

---

### Post by searchfgold6789 on 2011-12-10
Permissions thing. Try:```
sudo mkdir /usr/local/devkitadv
cd /home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/ 
make
```

---

### Post by dirkwillem on 2011-12-10
it now gives some more errors:

```
dirk@ubuntu:~$ sudo mkdir /usr/local/devkitadv
[sudo] password for dirk: 
Sorry, try again.
[sudo] password for dirk: 
mkdir: cannot create directory `/usr/local/devkitadv': File exists
dirk@ubuntu:~$ cd /home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/ make
dirk@ubuntu:~/Bureaublad/GBA/DevkitAdvance/devkitadv$ make
make -w install-binutils
make[1]: Entering directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv'
( \
	STRIPPROG=/usr/bin/strip; \
	cd build-binutils && \
	make -w install INSTALL_PROGRAM_ARGS="-s" \
	)
make[2]: Entering directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/build-binutils'
/bin/sh ../binutils-2.12.1/mkinstalldirs /usr/local/devkitadv /usr/local/devkitadv
make[3]: Entering directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/build-binutils/bfd'
Making install in doc
make[4]: Entering directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/build-binutils/bfd/doc'
make[5]: Entering directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/build-binutils/bfd/doc'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/build-binutils/bfd/doc'
gcc -c -I.. -I../../../binutils-2.12.1/bfd/doc/.. -I../../../binutils-2.12.1/bfd/doc/../../include -I../../../binutils-2.12.1/bfd/doc/../../intl -I../../intl  -g -O2 ../../../binutils-2.12.1/bfd/doc/chew.c
../../../binutils-2.12.1/bfd/doc/chew.c: In function ‘print_stack_level’:
../../../binutils-2.12.1/bfd/doc/chew.c:474:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long int’ [-Wformat]
../../../binutils-2.12.1/bfd/doc/chew.c:475:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long int’ [-Wformat]
../../../binutils-2.12.1/bfd/doc/chew.c: In function ‘main’:
../../../binutils-2.12.1/bfd/doc/chew.c:1598:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long int’ [-Wformat]
gcc -o chew chew.o  
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../aoutx.h >aoutx.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change aoutx.tmp aoutx.texi
touch s-aoutx
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../archive.c >archive.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change archive.tmp archive.texi
touch s-archive
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str < ../../../binutils-2.12.1/bfd/doc/../archures.c >archures.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change archures.tmp archures.texi
touch s-archures
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str < ../../../binutils-2.12.1/bfd/doc/../bfd.c >bfd.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change bfd.tmp bfdt.texi
touch s-bfd
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str < ../../../binutils-2.12.1/bfd/doc/../cache.c >cache.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change cache.tmp cache.texi
touch s-cache
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../coffcode.h >coffcode.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change coffcode.tmp coffcode.texi
touch s-coffcode
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../corefile.c >core.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change core.tmp core.texi
touch s-core
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../elf.c >elf.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change elf.tmp elf.texi
touch s-elf
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../elfcode.h >elfcode.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change elfcode.tmp elfcode.texi
touch s-elfcode
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../format.c >format.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change format.tmp format.texi
touch s-format
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str < ../../../binutils-2.12.1/bfd/doc/../libbfd.c >libbfd.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change libbfd.tmp libbfd.texi
touch s-libbfd
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str  <../../../binutils-2.12.1/bfd/doc/../opncls.c >opncls.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change opncls.tmp opncls.texi
touch s-opncls
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../reloc.c >reloc.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change reloc.tmp reloc.texi
touch s-reloc
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../section.c >section.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change section.tmp section.texi
touch s-section
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../syms.c >syms.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change syms.tmp syms.texi
touch s-syms
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../targets.c >targets.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change targets.tmp targets.texi
touch s-targets
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../init.c >init.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change init.tmp init.texi
touch s-init
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../hash.c >hash.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change hash.tmp hash.texi
touch s-hash
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../linker.c >linker.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change linker.tmp linker.texi
touch s-linker
./chew -f ../../../binutils-2.12.1/bfd/doc/doc.str <../../../binutils-2.12.1/bfd/doc/../mmo.c >mmo.tmp
../../../binutils-2.12.1/bfd/doc/../../move-if-change mmo.tmp mmo.texi
touch s-mmo
/bin/sh ../../../binutils-2.12.1/bfd/../mkinstalldirs /usr/local/devkitadv/info
mkdir /usr/local/devkitadv/info
make[4]: *** [install-info-am] Error 1
make[4]: Leaving directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/build-binutils/bfd/doc'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/build-binutils/bfd'
make[2]: *** [install-bfd] Error 2
make[2]: Leaving directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/build-binutils'
make[1]: *** [install-binutils] Error 2
make[1]: Leaving directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv'
make: *** [stmp-binutils-make-install] Error 2

```

What could be going wrong?

---

### Post by searchfgold6789 on 2011-12-10
Still a permissions thing. Now try:```
sudo chown -R dirk /usr/local/devkitadv
cd /home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/
make
```

---

### Post by dirkwillem on 2011-12-10
thanks, that worked. but now it gives this:

```
dirk@ubuntu:~$ sudo chown -R dirk /usr/local/devkitadv
[sudo] password for dirk: 
Sorry, try again.
[sudo] password for dirk: 
dirk@ubuntu:~$ sudo chown -R dirk /usr/local/devkitadv
dirk@ubuntu:~$ cd /home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/
dirk@ubuntu:~/Bureaublad/GBA/DevkitAdvance/devkitadv$ make
rm -rf build-gcc
mkdir build-gcc
make stmp-gcc-link-newlib
make[1]: Entering directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv'
patch --strip=1 --input=gcc-3.1.patch
patching file gcc-3.1/gcc/Makefile.in
Hunk #1 succeeded at 2634 (offset -18 lines).
patching file gcc-3.1/gcc/config/arm/t-arm-elf
Hunk #1 FAILED at 80.
1 out of 1 hunk FAILED -- saving rejects to file gcc-3.1/gcc/config/arm/t-arm-elf.rej
patching file gcc-3.1/gcc/dwarf2out.c
Hunk #1 succeeded at 2103 (offset 58 lines).
patching file gcc-3.1/gcc/except.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 3829 (offset 354 lines).
Hunk #2 succeeded at 3866 (offset 354 lines).
patching file gcc-3.1/gcc/except.h
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 137 with fuzz 1 (offset -9 lines).
patching file gcc-3.1/gcc/unwind-pe.h
Reversed (or previously applied) patch detected!  Assume -R? [n] y
patching file gcc-3.1/gcc/version.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 1 with fuzz 1.
make[1]: *** [stmp-gcc-apply-patch] Error 1
make[1]: Leaving directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv'
make: *** [stmp-gcc-configure] Error 2

```

have I done something wrong, or does this have to be fixed another way?

---

### Post by searchfgold6789 on 2011-12-10
Verry interesting...Someone more advanced in this area will have to help you with that, but I can make a feeble stab at the problem:```

cd /home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/
make clean
make
```Maybe a Mod will move this to Programming Talk/Packing and Compiling Programs so the people who regularly visit there can offer their insight.

---

### Post by dirkwillem on 2011-12-11
really thanks. It gives a lot more code, but in the end it gives precisely the same error as the last time.

---

### Post by searchfgold6789 on 2011-12-11
If the makefile is not custom, i.e. if it came with software you downloaded, then check the readme and make sure it doesn't say "sudo make" rather than "make". I would hate to recommend something that could potentially break your system, but if you want you may try to compile the makefile as the root user:```
sudo make
```This should solve the error messages but the software might not install correctly, and it might patch some system files and resave them as belonging to the root user, or it could cause other system damage by causing the persmissions of some files to be incorrect. If the software is particularly...large, you may want to experiment in a Virtual machine or seperate Ubuntu installation first just to make sure that things do not get messed up.
- search
P.S. If you did not create the software yourself, the developers would love to hear from you. What are you trying to compile?

---

### Post by dirkwillem on 2011-12-12
well, that didnt work. the bad thing is that devkitadvance (what Im trying to install, its for making GBA games)doesnt contain a README. I think that the problem is this: (see the bold section]
```
1dirk@ubuntu:~/Bureaublad/GBA/DevkitAdvance/devkitadv$ sudo make
[sudo] password for dirk: 
rm -rf build-gcc
mkdir build-gcc
make stmp-gcc-link-newlib
make[1]: Entering directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv'
patch --strip=1 --input=gcc-3.1.patch
patching file gcc-3.1/gcc/Makefile.in
Hunk #1 succeeded at 2634 (offset -18 lines).
[b]patching file gcc-3.1/gcc/config/arm/t-arm-elf
Hunk #1 FAILED at 80.
1 out of 1 hunk FAILED -- saving rejects to file gcc-3.1/gcc/config/arm/t-arm-elf.rej[/b]
patching file gcc-3.1/gcc/dwarf2out.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 2103 (offset 58 lines).
patching file gcc-3.1/gcc/except.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 3829 (offset 354 lines).
Hunk #2 succeeded at 3866 (offset 354 lines).
patching file gcc-3.1/gcc/except.h
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 137 with fuzz 1 (offset -9 lines).
patching file gcc-3.1/gcc/unwind-pe.h
Reversed (or previously applied) patch detected!  Assume -R? [n] y
patching file gcc-3.1/gcc/version.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 1 with fuzz 1.
make[1]: *** [stmp-gcc-apply-patch] Error 1
make[1]: Leaving directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv'
make: *** [stmp-gcc-configure] Error 2


``` since all the other "Hunks" (whatever they are) succeed.

EDIT

The makefile did say this:
```
## FOR THIS TO WORK CREATE A LINK TO /usr/bin/strip IN /bin ##
## YOU MAY ALSO NEED TO ADD /devkitadv/lib TO /etc/ld.so.conf AND RUN ldconfig AS ROOT ##
## configuration ##
```
But I dont know how to do that

---

### Post by searchfgold6789 on 2011-12-12
> ```
## FOR THIS TO WORK CREATE A LINK TO /usr/bin/strip IN /bin ## ## YOU MAY ALSO NEED TO ADD /devkitadv/lib TO /etc/ld.so.conf AND RUN ldconfig AS ROOT ## ## configuration ##
```To do that, I think you have to run these commands: ```
cd /bin
ln -s /usr/bin/strip
```You can contact the developer for help; he'll gladly offer all the support he can. His email address can be found on this page: [http://devkitadv.sourceforge.net/](http://devkitadv.sourceforge.net/) 
Also, it looks like there are some highly pertinent FAQ's here: [http://devkitadv.sourceforge.net/faq.html#rebuilding](http://devkitadv.sourceforge.net/faq.html#rebuilding)
I can't believe a Mod has not moved this thread to "Packing and Compiling Programs" yet. Perhaps you should make a request for this to happen, because the people who check there frequently can probably offer you some pretty good advice.

---

### Post by dirkwillem on 2011-12-13
then it gives this:
```
dirk@ubuntu:~$ cd /bin
dirk@ubuntu:/bin$ ln -s /usr/bin/strip
ln: creating symbolic link `./strip': Permission denied

```(how can one computer have so many issues?, ah, guess its just that horrible Vista)

and really, really, really thanks for searching those links, but the thing is that DevkitAdvance is pretty, well eh, ancient. So the support isnt good. I read one topic dating from 2006, and he didnt get any help; so Ill give it a go, but I dont expect much. And the FAQ is for Windows, so that is pretty worthless too. (strange they do explain  how to emulate a linux environment, but dont give any help for linux users=D>, great going people!)

---

### Post by searchfgold6789 on 2011-12-13
Ok instead of```
cd /bin
ln -s /usr/bin/strip
```Type this:```
cd /bin
sudo ln -s /usr/bin/strip
```

---

