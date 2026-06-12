---
title: "PLease help, Ubuntu install and grub"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by fake_punk on 2008-03-23
Hello all,

I am trying to install Ubuntu to my new Lenovo Thinkpad T61.  However, In order to maintain my recovery partition, I must us the NTLDR, and fdisk /mbr will not make it work, so I have to keep my NTLDR completely in tact.  During the Ubuntu 7.10 install, I chose not to install grub.  Now when I boot the LiveCD to try to install grub to the partition, I go in to sudo grub, and when i try to find /boot/rub/stage1 I cant find it.  I am at a loss...

---

### Post by buntu_Geek on 2008-03-23
Yeah .. its obvious...
Since you didnt install grub into your Ubuntu partition ...it hasnt installed any of the bootloader stages into your partition...

I suggest you SuperGrubDisk as a solution....

There are many how tos for installing SuperGrubDisk...

---

### Post by fake_punk on 2008-03-23
ya, I kind of thought so... now, can I put supergrub into the NTLDR the same way, or will I have to find a seperate guide for that too?

---

### Post by buntu_Geek on 2008-03-23
Oh... no... 
I forgot to say this... your windows boot loader will be over written.... 

The next solutions is.. you can include as an in your windows boot loader...
there are many threads running on this topic...

---

### Post by Pumalite on 2008-03-23
Take a look at this:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61#Intel_Graphics_Media_Accelerator_X3100_.28Chipset_GM965.29_.28Solved.29](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61#Intel_Graphics_Media_Accelerator_X3100_.28Chipset_GM965.29_.28Solved.29)

---

