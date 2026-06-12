---
title: "Ubuntu 12.10 dualboot separate drives - ubuntu not starting"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by Devert on 2012-11-01
Hi, im trying to install Ubuntu on my computer. I have already a windows on my computer, trying to install Ubuntu on a new SSD harddrive. Im not getting GRUB to work, windows boot fine but if i change boot priority to my Ubuntu disk nothing happens.

Here is a link to my Boot Info Script: [http://paste.ubuntu.com/1325072/](http://paste.ubuntu.com/1325072/)

How do I get this thing working?

---

### Post by oldfred on 2012-11-01
Install grub2's boot loader to sdc's MBR. Do not install to all the others. And then set BIOS to boot drive that is sdc. Boot Repair should be able to do that.

Your bios_grub is huge. It just needs to be 1MB as it is a place in gpt partitioned systems for grub2's core.img which is about 32KB. 

Update - I was wondering why it was blocking grub install. It looks like you formatted your bios_grub, it has to be unformated. Use gparted and change to unformated.

Other ways to install grub2's boot loader.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

---

### Post by Devert on 2012-11-02
Thanks! After a final try with Boot-repair and GParted i got it working.

---

