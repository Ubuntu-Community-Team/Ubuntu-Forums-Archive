---
title: "Trouble installing BRL-CAD"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by malacai on 2007-04-15
My install of BRL-CAD comes to a screeching halt every time it comes to the jove compononent. Here's the result:

Making install in jove
make[3]: Entering directory `/home/zippo/CAD/brlcad-7.10.0/src/other/jove'
make[3]: *** No rule to make target `jove-tutorial', needed by `all-am'. Stop.
make[3]: Leaving directory `/home/zippo/CAD/brlcad-7.10.0/src/other/jove'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/zippo/CAD/brlcad-7.10.0/src/other'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/zippo/CAD/brlcad-7.10.0/src'
make: *** [install-recursive] Error 1

Any suggestions? Thanks.

---

### Post by eerik on 2007-04-20
Hi!

I got the same problem when compiling **brlcad** from the source on my Ubuntu Dapper. Solution was to change 3 makefiles (*Makefile*, *Makefile.am* and *Makefile.in*) in directory *../brlcad-7.10.0/src/other/jove/*.

Open these files with text editor and remove strings "jove-tutorial" and the "\" at the end of "describe.com". 

_Before changing_: 

[B]desc_DATA = \
	describe.com \
	jove-tutorial[/B]

_After changing_:

[B]desc_DATA = \
	describe.com[/B]

Save files and then run **make** again. Compilation should continue without problems.

With best regards,

eerik

---

### Post by Ag_Smith on 2007-05-01
I have fix this tutorial work !!

---

### Post by Ag_Smith on 2007-05-01
I have fix this tutorial work !!

---

### Post by Ag_Smith on 2007-05-02
I have fix this tutorial work !!

---

### Post by john_3000 on 2007-08-17
Know all by these presents that on 17 August 2007, after many trials, errors, researches and random tinkerings, John_3000 successfully built brlcad 7.10.2 from source on an ancient 450Mhz AMD K6-2 box running default, generic Ubuntu Feisty, by means of the steps below, which he learned in these forums and which he believes necessary and sufficient. The benchmark "VGR performance metric" that resulted was 158, which greatly exceeds the 64 obtained with a version 7.8.4 .deb file obtained at [http://sourceforge.net/project/showfiles.php?group_id=105292](http://sourceforge.net/project/showfiles.php?group_id=105292)
====================

(1) # apt-get install build-essential
(2) # apt-get install xorg-dev 
(3) from the brlcad build directory:

$ ./configure --enable-optimized --disable-debug --disable-runtime-debug --with-x11=/usr/include/xorg

(4) $ make
(5) # make install
====================

For version 7.10.0 but apparently not for 7.10.2,  the jove makefile edits specified by eerik above were also necessary.

other keywords: compile,crashes,fails,bombs

---

### Post by greg73654 on 2007-08-28
I don't think mine worked, I tried 7.10.2... but I don't know what it should look like when it's running... and when I run the right program will I be able to access all the tools that are with BRL?

---

### Post by john_3000 on 2007-08-30
"and when I run the right program will I be able to access all the tools that are with BRL?"

Why not?  You want "Introduction to MGED" from brlcad.org.  Then people won't say RTFM ;-)

---

