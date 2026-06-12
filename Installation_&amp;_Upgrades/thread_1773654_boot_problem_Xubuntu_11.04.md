---
title: "boot problem Xubuntu 11.04"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by jcribas on 2011-06-02
Hi,

I'm having some trouble putting to work Xubuntu on a Acer Travelmate 290 (512Mb RAM, 100Gb disk).

I have installed it without any problem, in a 60Gb ext2 partition made during the installation process. 

When I boot the computer it seems that some letters appear but very blurred. If I try to enter grub menu and boot in recovery mode, this is what I get:
[IMG]http://img715.imageshack.us/img715/2988/dsc00070c.jpg[/IMG] 
All the text seems to be blurred. 
Curiously though, after trying to boot in recovery mode and turning off the PC, I am able to reboot it, choose the linux in grub menu and it works! 


Any suggestion to make this work out? Can this be a problem of graphic processor or screen drivers??

Thnks,
JCR

---

### Post by ronparent on 2011-06-02
As long as I was trying to boot from the grub installed with Natty I was getting the same thing. I believe the characters are printed in a graphics mode making them unintelligible. In my case I fixed it by reinstalling grub to a mint install on the same unit! I believe it is a bug but haven't got around to reporting it.

---

### Post by jcribas on 2011-06-02
SOLVED THE PROBLEM

Solution:

Use startup-manager to change Grub configuration:
Changed to 1024x728 resolution and graphical boot instead of text boot. Works perfectly now :)

JCR

---

