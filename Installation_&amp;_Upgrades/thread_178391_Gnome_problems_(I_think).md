---
title: "Gnome problems (I think)"
date: 2006-05-17
forum: Installation &amp; Upgrades
---

### Post by holmj2674 on 2006-05-17
I am a complete Linux knoob. I was recomended to ubuntu as a freindly starting point for newbies. I downloaded the install, set up a partition in my secondary hard drive, install GRUB to properly boot both ubuntu and win xp, and as far as I could tell properly installed ubuntu.
When the system restarted and ubuntu loaded it completed its initialization...and then nothing. Black screen with a white cursor. My computer had done this with ubuntu, ubuntu live cd, and xandros. Can someone tell me what the problem might be and how to fix it?
 
I have a p3 1.13 gig with 512 meg ram and a 128 meg nivida video card. I have a primary 20 gig hard drive, and a secondary 20 gig hardrive with a single NTFS partition, and then the linux partitions

---

### Post by RavenOfOdin on 2006-05-17
Can you start a console session (Ctrl-Alt-F1 when you get to the black screen/white cursor) and then 

```

pico /etc/X11/Xorg.conf

```

?

List the contents of that file, please.

---

### Post by holmj2674 on 2006-05-18
ok, I figured out that the problem was my Nvidia graphics card, so I set the BIOS back to the integrated video driver and installed Ubuntu... everything worked fine. Now my question is... how do I install the Nvidia driver? I downloaded the latest driver from Nvidia and used their command (sh NVIDIA-Linux-x86-1.0-8756-pkg1.run) and theres no such thing. I tried using the suggestions from thread #3 on this topic (sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-'uname-r' (substituting my username of course)) and I get a can't find linux-restricted.... yada yada. How do I download and install a driver? Is it really necissary to use the terminal? I haven't managed to get it to do what I want once since installing or using a live version of linux.

---

