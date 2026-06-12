---
title: "Control placement of Boot Loader during install"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by billmccl on 2007-05-19
I am configuring a machine to perform some software development, and I want to install Ubuntu into a multi-OS environment.  I will be using Acronis Disk Director 10.0 as the boot loader, and plan to have Win XP, Win Vista, Ubuntu, Fedora 6, and Mandriva on the machine.

The question is how to install Ubuntu so that it places its boot loader on the partition where it is installed rather than the MBR of the hard drive.  This is simply done in Fedora and Mandriva by  selecting the advanced or custom partioning option.  I do not find a similar option for Ubuntu.

As I go through the Ubuntu installation process,  I am never given an option to install the boot loader at the beginning of its partition where I need it.

Anyone know how to do this?

Thanks....

---

### Post by shamreez on 2007-05-22
In Fiesta 7.4 there is an option for it.

Once you finish giving all the requirements for ubuntu to install it takes you to a screen showing you the details like where it is going to install there is an option over there called "advanced" where you can specify where to load the grub loader

---

### Post by phidia on 2007-05-22
You need the alternate cd which is a text based installer. 
The desktop or live cd doesn't have the option anymore AFAIK.

---

