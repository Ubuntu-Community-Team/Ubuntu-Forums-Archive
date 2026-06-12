---
title: "How to boot an existing ubuntu partition with the cdrom"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by nesh on 2005-04-08
i have installed ubuntu and installed grub to the first boot sector of my boot partition. But at restart I have to boot it with something. I have tried passing parameters at the install prompt like root=/dev/hdb1 but it doesn't work. Any idea?

/dev/hda  winXp
/dev/hdb   ubuntu
         hdb1 root
         hdb2 swap

---

### Post by alastair on 2005-04-08
Explain - what exactly happens at boot?

Do you see a GRUB menu? i.e. a list of things to boot?
Do you end up in a GRUB prompt (grub>)?

---

### Post by nesh on 2005-04-08
I install Ubuntu, at the end it asks me where do I want to install grub. I install it on 
/dev/hdb1, I don't want to mess my MBR. But since I have windows on my main hd, the system boots directly to winxp. The only way I boot to ubuntu to finish the installation is to boot up the system with another media: a floppy or a cdrom.
I didn't install grub on a floppy. I need a way to boot into ubuntu with the cdrom, if it is possible. 
For example, in slack , it offers you to install the boot loader where you want and make a boot floppy. So I boot with my floppy copy the first 512k of my boot partition and copy it to windows. Then I have a dual boot.

Thanks for the reply.


PS: In slack, even if you don't make a boot floppy you can boot your system with the installation cdrom by specifying the parameters on the command line.

boot=/dev/hdb1 noinitrd ro

---

