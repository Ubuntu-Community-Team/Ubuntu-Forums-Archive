---
title: "Installation from USB stick"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by totalalbedo on 2007-04-20
I currently dont have the possibility to use a CD or DVD to install ubuntu. Is there any guide on how to install from a USB stick out there? Its version 7.04 I want to install.

---

### Post by JeRa on 2007-04-20
It's quite simple if you follow the guidelines on [this page](https://help.ubuntu.com/community/Installation/FromUSBStick). Basically it's:
1) Format a 1GB+ USB stick as FAT16
2) Run syslinux on it so it becomes bootable
3) Copy the **contents** of the CD/ISO onto the USB drive
4) Move everything from /isolinux/ and /install/ into the root of your USB drive
5) Move vmlinuz and initrd.gz from /casper/ to the root of your USB drive
6) Rename /isolinux.cfg to /syslinux.cfg
7) Edit /syslinux.cfg and remove every occurence of '/casper/' and '/install/' (**not** 'casper')
8) Reboot :) it should work.

That being said, I haven't gotten it to boot the graphical setup myself :D somehow previous versions of (k)ubuntu up until feisty always worked perfectly, feisty however shows a black screen for a second and then jumps back to the kernel messages and hangs/loops (last message was the initialization of the squashfs filesystem).

---

### Post by JeRa on 2007-04-20
> **JeRa said:**
> It's quite simple if you follow the guidelines on [this page](https://help.ubuntu.com/community/Installation/FromUSBStick). Basically it's:
That being said, I haven't gotten it to boot the graphical setup myself :D somehow previous versions of (k)ubuntu up until feisty always worked perfectly, feisty however shows a black screen for a second and then jumps back to the kernel messages and hangs/loops (last message was the initialization of the squashfs filesystem).
I've managed to work around this problem by not using the kubuntu ISO (i386) but the ubuntu ISO. Using the steps provided above, this should work perfectly :)

---

### Post by jcpeart on 2007-04-20
i have followed the instructions to the best of my ability and think i have done everything correctly including running syslinux.  When I reboot with the USB stick in, it says "Error loading operating system"  I am using a Corsair 8GB USB stick.  any ideas on what i have done wrong?

---

### Post by paulieman on 2007-04-20
I will float this out as a suggestion, only because I have been burned by these kinds of details in the past:)  Did you copy hidden files/directories?  Press control + h to view hidden files.

---

### Post by jcpeart on 2007-04-20
The hidden files and folders were copied

could it be something with syslinux?

---

### Post by jcpeart on 2007-04-22
I think it is my computer.  Took the USB stick to my son-in-law's and it booted fine on his computer.    My computers are dells and the bios is set to boot from USB first, but no go.

Jim
:(

---

