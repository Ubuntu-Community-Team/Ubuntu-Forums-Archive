---
title: "Grub files failed to install, with LVM single HD"
date: 2017-10-29
forum: Installation &amp; Upgrades
---

### Post by ddjohnson40 on 2017-10-29
I have tried to install Ubuntu 17.04 & Kubuntu 17.10 using LVM onto a 4TB WD drive, pc has AMD 64bit. Every time there is a fatal error with the install of grub. When I run (Supper) GNU GRUB 2.02 it list that no grub.cfg, menu.lst, core.img, files detected. 
Under ----disk and Partitions it lists 
             (proc); error: beyond total sectors & 
             (hd0) attempt to read or write outside of disk hd0. 
Then it lists  (hd0,gpt2); invalid signature
                  (hd0,gpt1); invalid signature
----Bootable IOSs (in /boot-isos or /boot/boot-isos) nothing is returned. 
I have read many post and tried using their fixes. Every time part way through the sequence failed. I have removed the LVM partition and started fresh again. I received the fatal error and and this past was given for possible help. [http://paste.ubuntu.com/25828517/](http://paste.ubuntu.com/25828517/). any advise is appreciated. 
I have Beginner Linux knowledge, Don’t understand Grub at all.

3/Nov/2017
 I have tryed to reinstall Kubuntu 17.10 with LVM once again. this time I didn’t get any error messages and still on reboot the system dropes out to a Grub rescue prompt.
I have been working on this every day for two weeks reading bug reports and other peoples fixes but none have helped me understand what is going on with my install or how to fix it. Can anyone please give me a hand.

---

