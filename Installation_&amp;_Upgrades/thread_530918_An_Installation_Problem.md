---
title: "An Installation Problem"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by ShyLight on 2007-08-21
I should preface this by saying I'm not 100% tech-savvy, so please bare with me. :) 

I just burned Ubuntu onto a CD-R disc successfully after following all of the instructions. Before doing so, however, I checked the md5sum with WinMD5Sum (since my previous operating system was Windows Vista) to make sure they were the same, and they are the same. Then I put the CD into my disc drive and it booted up. "Loading linux kernel to 100%" appeared and a little orange bar went back and forth, then the  following screen appeared:

-----------------------------------------------------------------------------------------------------------
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
-----------------------------------------------------------------------------------------------------------


I did enter "help", but I'm not sure what command I'm supposed to be looking at or how to proceed with this installation. Can anyone help me? 

Here are my laptop’s specifications, if they’ll help:

HP Compaq 2510p pre-installed with Windows Vista
Intel® Core 2 Duo ULV processor U7600 1.20 GHz 2 MB L2 cache 533 MHz
2 GB 667 MHz DDR2 SDRAM
Mobile Intel GMA X3100 Graphics Card


Thanks in advance.

---

### Post by Pumalite on 2007-08-21
Your problem has been extensively discussed in this forum. Check this thread:[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

---

### Post by blinxdk on 2007-08-21
I just installed 7.10 on a HP 2510p today.

Before the installation I pressed F6 and added noacpi nolacpi pci=noacpi generic.all_generic_ide=1 to the boot command.

However it seems that all that was needed was the generic.all_generic_ide=1 option, atleast that is all I use now that I boot from the HD

If modprobing ata_piix or ide-generic didn't work for me. ata_piix didn't affect the harddrive and ide-generic did work, but there where some irq problems that made it impossible to install (took 1 hour to mkfs.ext3 a 200MB partition).

So my bet would be:

1) Get the 7.10 tribe 4 install disk.

2) Press F6 at the boot menu and add generic.all_generic_ide=1

3) Reboot and use the generic option again, then add it to you permanent boot options in /boot/grub/menu.lst

---

### Post by CrZy_T on 2007-10-25
Anyone of you gotten the smart card reader to work?

---

