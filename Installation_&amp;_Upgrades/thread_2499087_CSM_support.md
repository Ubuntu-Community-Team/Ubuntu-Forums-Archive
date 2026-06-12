---
title: "CSM support"
date: 2024-07-11
forum: Installation &amp; Upgrades
---

### Post by zanetto on 2024-07-11
Every time I use windows 10 and then reboot to ubuntu, CSM support in bios changes from disable to enable and I can't boot to ubuntu.
Using  boot repair I receive the message: 
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic
ls: cannot access '/sys/firmware/efi/vars': No such file or directory

but boot repair can't remove the problem

---

### Post by yancek on 2024-07-11
You forgot to post the link to the output from the boot repair software when you selected the Create BootInfo Summary option.  This is what is suggested on their home page for people who are not familiar with the intricacies of the Grub bootloader so running it again and posting the link would be your first step.  Doing this would answer questions such as are both OS's installed in UEFI mode.  You haven't  posted any information on your hardware but changing settings from CSM enabled to disabled on a simple reboot seems unusual.

---

