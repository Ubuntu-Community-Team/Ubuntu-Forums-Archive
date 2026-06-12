---
title: "Boot and INstall of 7.10"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by starter1 on 2008-04-04
Hi help please - for a beginner.

I have downloaded and created a CD for 7.10 and it has been checked for errors. When I test the LIve CD on my work machine, it works fine by booting from CD.

I would like to install at home on and IBM ThinkPad iSeries (1171-l1G) which is a Pentium 111 650Mhz with 256MB RAM (currently seems to have an illegal copy of XP on it).

Machine boots from CD initially - giving the menu to Start or install Ubuntu etc.

The boot starts with the following two messages during load :

ACPI no dmi bios year
PnPBios get_dev_node : invalid handle.

The machine proceeds to boot and loads the kernel dropping down to command line and displaying:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 


Can anyone help on what I do next to get the GUI up and running to format the HDD and load Ubuntu onto it - don't want dual boot or anything.

Thanks in advance, help much appreciated.  K

---

### Post by Victormd on 2008-04-04
Have you tried booting in "safe graphics mode?" Also, I think there is a 512MB min. requirement for ubuntu (have to check). You might want to try another distro like Xubuntu, it'll be lighter on your thinkpad.

---

### Post by Midwest-Linux on 2008-04-04
The ACPI is really a non issue. You know how some older computers even after clicking windows off in the desktop, you will still have to manually shut off the machine? Thats all that is, its a older machine and it seems around 1999 or 2000 the issue was taken care of in newer computers.

 I would highly recommend using the "alternate text installer CD" version. Seems the live CD will only work with 256MB or better. (Remember some of your ram is being used by the video). Also I would do two of two things.

1. Get more RAM for your laptop.

or

2. Install Xubuntu, which runs better on lower ram. 

I would recommend 512 MB Ram to run Ubuntu on. Older laptops use PC100 SoDimms which are inexpensive on E-Bay. Its highly likely that your laptop uses that type of RAM.

I highly recommend  the 7.04 Xubuntu alternate text installer first, if you don't buy more ram and want to just install it now. You can always upgrade to a full blown Ubuntu 7.10 later on with some commands without a disc once you get the extra ram. 


I checked, the link is still good, you can download it here.

[http://cdimage.ubuntu.com/xubuntu/releases/feisty/release/xubuntu-7.04-alternate-i386.iso](http://cdimage.ubuntu.com/xubuntu/releases/feisty/release/xubuntu-7.04-alternate-i386.iso)

Good luck and always remember to burn with the lowest speed as a ISO. Keep us posted.

---

### Post by starter1 on 2008-04-04
Thanks so much  for your help - Xubuntu loaded no problem and seems to be working fine from your link! I'll play around for while before deciding if I need more RAM - only want this old machine for email and surfing so it looks to be working okay for the moment!

Thanks once again. K

---

