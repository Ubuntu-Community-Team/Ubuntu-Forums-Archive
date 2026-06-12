---
title: "Kernel trouble in Hardy upgrade"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by lwpack on 2008-04-29
Hello. I have had a few troubles with the hardy upgrade. When I upgraded, the kernel did not properly install and I had to install from the command line while on a live cd (I'm a newbie, so I don't entirely know what I'm doing, I just followed the instructions of someone on Linux forums ([http://www.linuxforums.org/forum/installation/120279-solved-unable-boot.html](http://www.linuxforums.org/forum/installation/120279-solved-unable-boot.html)).

Everything seemed to work after this except that I would get an error when trying to install things.  I was told to run the command sudo dpkg -l linux-image-2.6*

Below are the results, but I don't know how to remedy it.  Any help would be greatly appreciated.  Thanks!

lwpack@lwpack-pc:~$ sudo dpkg -l linux-image-2.6*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-==============-============================================
un linux-image-2. <none> (no description available)
rc linux-image-2. 2.6.17.1-10.34 Linux kernel image for version 2.6.17 on x86
rc linux-image-2. 2.6.17.1-11.38 Linux kernel image for version 2.6.17 on x86
rc linux-image-2. 2.6.20-16.35 Linux kernel image for version 2.6.20 on x86
rc linux-image-2. 2.6.22-14.52 Linux kernel image for version 2.6.22 on x86
iF linux-image-2. 2.6.24-16.30 Linux kernel image for version 2.6.24 on x86
lwpack@lwpack-pc:~$

---

### Post by tobydeemer on 2008-04-30
Try it this way, and see if it works:

[HTML]sudo dpkg -l linux-image-2.6.24-16.30[/HTML]

---

