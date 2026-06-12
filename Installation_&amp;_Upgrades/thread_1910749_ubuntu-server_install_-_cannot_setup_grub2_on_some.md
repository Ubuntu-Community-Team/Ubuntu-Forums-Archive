---
title: "ubuntu-server install - cannot setup grub2 on something different than /dev/sda"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by fabrica64 on 2012-01-17
I tried to install ubuntu server 11.10 from a USB key to an internal HD.

The USB key is handled by the system as a normal HD and assigned to /dev/sda

The "real" HD where ubuntu is being installed is assigned to /dev/sdb

When grub 2 is setup the ubuntu installer tries to put grub 2 to the master sector of /dev/sda, not to the master sector of the "real" HD (/dev/sdb), it gets an error and grub 2 is not installed, preventing boot of the fresh installed system

I don't know how to force the grub 2 installer to use /dev/sdb instead of /dev/sda

The same error happens if I have a lot of HD and I try to install ubuntu to any HD not being the first (/dev/sda)

In all these cases I end up having ubuntu installed on a disk that is the boot disk in the BIOS but it does not have grub 2 in the master sector

The only way to install ubuntu server without errors is to have it installed from a CD, that is not mapped to /dev/sda, and have a single HD in the system, so I am sure it is /dev/sda and grub 2 installer is not fooled...

It seems a very bad error, especially for servers that have many disks and in most of the cases the boot disk is not /dev/sda...

How can I fix this without resorting to use a CD for the installation?

---

### Post by darkod on 2012-01-17
If I am not mistaken, when it defaults installing to /dev/sda you can hit Cancel (or similar) in that step. In that case the next screen will ask you where you want to install, and you will be able to type it yourself. So you can change sda with sdb.

---

### Post by coffeecat on 2012-01-17
EDIT - sorry. Posted in error.

---

### Post by grahammechanical on 2012-01-17
If you cannot find a way of doing this during the install then check out Grub Customizer.

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

That allows you to make modifications to the Grub configuration and it has an option to save Grub to MBR and I am sure that you can select which hard disk to use. I have not done this myself as I only have 1 HD.

Regards.

---

