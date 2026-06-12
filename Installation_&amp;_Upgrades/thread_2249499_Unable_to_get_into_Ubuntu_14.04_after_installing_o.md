---
title: "Unable to get into Ubuntu 14.04 after installing on dell 15r"
date: 2014-10-22
forum: Installation &amp; Upgrades
---

### Post by praroh1 on 2014-10-22
Hi, I freed about 75GB from my hard disk for Ubuntu using win8 memory mgmt. I then installed Ubuntu using a live DVD. I selected "Something else" and allocated 68GB as ext4 (root partition. mount point: /), 10MB as Boot (memory? area? something..), 12GB as SWAP Area. Device for boot loader installation: the newly created ext4 partition.

The installation completed and I was asked to restart.

Here's where things start going wrong. I am not getting the option to get into Ubuntu. I can use win8, and if I try to boot from hard disk or anything it fails and shows "No bootable media found" (or something like that, guess its not important).

The memory which I freed and used is no longer shown as free memory in win* memory mgmt neither is it accessible from "My Computer".

Question1) What can I do to repair the installation?
Question2) Should I just free that memory again using win8 memory mgmt and start over? O_o

Please help me out!!

---

### Post by fantab on 2014-10-22
If Win8 came pre-installed there is 99.9% chance that you have UEFI with EFI system Partition [ESP].
If Windows is installed in UEFI mode then Ubuntu must also be installed in UEFI.

To start diagnosing, boot from Ubuntu DVD/USB and "Try Ubuntu"... Download and install [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") tool.
Run the 'create bootinfo summary' option in Boot-Repair tool (don't run any repair at this stage).. note the url link BR creates to the bootinfo file and post the link here.

I'd also recommend that you go through this [Wiki page]("https://help.ubuntu.com/community/UEFI"), to understand more about UEFI...

---

### Post by Bucky Ball on 2014-10-22
Try this:

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

* Oops. Ninja-ed by fantab. Why not run the recommended repair then post the bootinfo if that doesn't work?

---

### Post by fantab on 2014-10-22
> 10MB as Boot (memory? area? something..),

> Why not run the recommended repair then post the bootinfo if that doesn't work?

If OP has created a separate boot partiion on a GPT disk... then BR will keep installing grub in  that partition unless forced to install in ESP from advanced options after disabling the 10MB partition. If its a UEFI machine then op has to boot his ubuntu dvd/usb in UeFI mode for boot-repair to work with ESP... its a good idea to see the Bootinfo first (since OP has not provided enough info), that is all.

---

### Post by praroh1 on 2014-10-23
Okay, I've decided to get rid of win8. If I choose to delete windows during installation of ubuntu and install ubuntu in legacy mode will it work or will I wnd up facing the same issue?

---

### Post by Bucky Ball on 2014-10-23
Should be fine. What you could do is boot to the 'Try Ubuntu' option, get to a desktop and launch Gparted, delete the Win partition then install.

Make sure you tweak the BIOS to legacy prior to booting from the Ubuntu install media. No faststart or secureboot. Good luck.

---

