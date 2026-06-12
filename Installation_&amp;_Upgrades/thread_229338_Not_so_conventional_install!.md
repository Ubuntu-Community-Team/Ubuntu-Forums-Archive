---
title: "Not so conventional install!"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by irv on 2006-08-04
I am running Ubuntu Dapper Drake on 6.06 on four PC's now, and have had no problems with installs. But I am trying something that not conventional. I have one test PC that I use for testing different thing an am trying to install 6.06 on some extra hard drives I have and moving them to other PC's. The problem I am having is when I install the hard drive in other PCs I get a Grub error 18 when booting. My question is, is there a way to put the install CD in the PC and fix the Grub error 18 so the install 6.06 will boot from the newly installed hard drive? 
At the point when I install the hard drive I don't get to a prompt to enter any commands. The PC is not even gone through the boot process yet.

---

### Post by wombat20 on 2006-08-04
[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

---

### Post by FenrisAbraxas on 2006-08-04
> **irv said:**
> I am running Ubuntu Dapper Drake on 6.06 on four PC's now, and have had no problems with installs. But I am trying something that not conventional. I have one test PC that I use for testing different thing an am trying to install 6.06 on some extra hard drives I have and moving them to other PC's. The problem I am having is when I install the hard drive in other PCs I get a Grub error 18 when booting. My question is, is there a way to put the install CD in the PC and fix the Grub error 18 so the install 6.06 will boot from the newly installed hard drive? 
At the point when I install the hard drive I don't get to a prompt to enter any commands. The PC is not even gone through the boot process yet.

Thats because grub think you have the same config of your disk drives (remember hdx,x)

If you installed with the drive as secondary master it will be hd2,x and if you plug it in the nw box in primary it will be hd0,x.

Good luck, probably the live cd will help you fixing GRUB.

---

### Post by irv on 2006-08-05
> **wombat20 said:**
> [http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)
Thanks
This link gave me the answer. I was trying to boot it in a machine with and old BIOS. It didn't support the drive size. There is some work arounds, but I am not sure if this older machine will run fast enought.
Thank again for your help.
Irv

---

