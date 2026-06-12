---
title: "Ubuntu 8.04 getopt error on install of screensaver"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by B1tgoblin on 2008-07-17
My spec's
XPS M1530
3gig mem
Dual core 2.0
NVIDA 8800 video card 
260 gig drive
Dual boot VISTA and Ubuntu 8.04 (VISTA first and Ubuntu using grub )

Alright my problem is that i want to install rss-glx_0.7.6, so i do the norm and bunzip and untar then try the "sudo ./configure" and i get this>>>>

******************************************************************
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
checking for g++... g++
checking for C++ compiler default output... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for sse... yes
checking for 3dnow... yes
checking for pow in -lm... yes
checking for BZ2_bzBuffToBuffCompress in -lbz2... no
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for X... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking for getopt... no
configure: error: getopt is missing but required.
***********************************************************************
So i tried "apt-get update">>
***********************************************************************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
***********************************************************************
Um yeah so now im lost lol. Im not new to linux but im green. Any help would be nice. If there is a forum with this in it already please dont FLAME me just redirect me :) MANY THX .

---

### Post by Pumalite on 2008-07-17
Try:
sudo apt-get install util-linux

When it asks you about removing linux32 answer yes.

That should stablize your apt scripts so you can perform adds and removes.
Hope this helps.

---

### Post by B1tgoblin on 2008-07-17
> **Pumalite said:**
> Try:
sudo apt-get install util-linux

When it asks you about removing linux32 answer yes.

That should stablize your apt scripts so you can perform adds and removes.
Hope this helps.
K ill try it now thx :)

---

### Post by B1tgoblin on 2008-07-17
> **Pumalite said:**
> Try:
sudo apt-get install util-linux

When it asks you about removing linux32 answer yes.

That should stablize your apt scripts so you can perform adds and removes.
Hope this helps.

K i used "sudo apt-get install util-linux" it said that the package was already installed. So then i tried "sudo apt-get remove util-linux" that seem to work fine. As that finished my update manager said that there was a new package to install, it was util-linux. I then installed the package.....and well same problem. I also noticed that when i open Synaptic Package Manager getopt isn't in there should it be ?? Please let me know if i can offer any other information for you to help me better.  O and it didn't ask to remove linux32 ?

---

### Post by frodon on 2008-07-18
In case you're having nightmares the following link will give you getopt binary to put in /usr/bin/ (remove the .txt extension) :
[http://ubuntuforums.org/attachment.php?attachmentid=68248&d=1209632759](http://ubuntuforums.org/attachment.php?attachmentid=68248&d=1209632759)

Once your problem solved consider trying to reinstall correctly util-linux and getopt.

---

### Post by B1tgoblin on 2008-07-19
Yeah that didn't work ?? Could it be something else ? Like bad install of ubuntu 8.04 ?

---

### Post by frodon on 2008-07-19
Sorry B1tgoblin, i was a bit quick reading your post and making my first answer.

I don't think you have any getopt issue but just that the install script shipped with your software is looking at getopt in the wrong place and reports it as not installed whereas it is actualy.
So except looking at the install script to understand where it is looking for getopt i have no solution to provide you.

---

### Post by Pumalite on 2008-07-19
Maybe you can get more information about the problem reading this thread:
[http://ubuntuforums.org/showthread.php?t=724273&page=4](http://ubuntuforums.org/showthread.php?t=724273&page=4)

---

### Post by B1tgoblin on 2008-07-20
Well last night at work at i thought i might do a new install so i wiped out my Ubuntu DVD and.... The damn thing doesn't work. So im going to download a new one today. Maybe my copy was bad ?? Ill post how the install went later.

---

