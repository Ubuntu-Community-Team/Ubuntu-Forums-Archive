---
title: "Problems with GRUB"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by saurabh_190 on 2011-02-09
Hey everyone,
 I am new to ubuntu OS, I am having quiet a hard time solving out certain problems.
I have Ubuntu 10.10 and Win Xp installed on the same hard drive partition i.e C drive. Now yesterday accidently I deleted a folder from C while I was logged in to Windows. Now today when I restarted my pc I got this error message :

error : No partition found
grub rescue>

Then somehow I managed to reinstall the Grub loader. Now whenever I restart my PC I get this error message :

                GNU GRUB version 1.98+20100804-5ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

I dont know what to do next. Please help.It's really really urgent that I get this correct. Please...

---

### Post by oldfred on 2011-02-09
Welcome to the forums.

It sounds like you have the wubi install. You have to have the windows boot loader in the MBR as it uses windows to boot and is just a file inside the windows NTFS partition.

how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

[U][https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[/U][]("http://ubuntuforums.org/showthread.php?t=1639198")

---

