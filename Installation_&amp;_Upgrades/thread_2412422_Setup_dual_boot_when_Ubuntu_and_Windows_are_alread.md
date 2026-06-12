---
title: "Setup dual boot when Ubuntu and Windows are already installed"
date: 2019-02-12
forum: Installation &amp; Upgrades
---

### Post by eddyq on 2019-02-12
I installed Ubuntu on my first partition. Then I restored a Windows system + another partition using Acronis on the 2nd and 3rd partitions.

Now I want to setup a dual boot. I tried running grub-install but it seems to not work with a GPT:
    eddyq@eddys-ubuntu:~$ sudo grub-install /dev/sda
    Installing for i386-pc platform.
    grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
    grub-install: error: embedding is not possible, but this is required for cross-disk install.

Is there a way?

---

### Post by yancek on 2019-02-12
You need to read through the Ubuntu documentation at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> I tried running grub-install but it seems to not work with a GPT:

Incorrect assumption.  Ubuntu and other Linux systems can do a Legacy install on a GPT or an EFI install on a GPT drive.
Windows can only do an EFI install if you have a GPT drive
If your drive is GPT and windows is installed and functioning then it is EFI and you need to install UBuntu EFI.  The message you are getting is indicating that you are trying to do a Legacy install on a GPT partitiion without creating the bios_grub partition.  That is explained at the link above.

---

