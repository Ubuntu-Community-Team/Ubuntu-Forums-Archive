---
title: "Cannot boot after installtion 1st stage"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by carytid9 on 2005-05-11
I have an Installation problem, associated with the Grub Boot Loader.  The first part of the installation goes perfectly, and I request Grub to be loaded in the root (/) logical partition (hdb5).  The /boot partition is primary (hdb1).  When the system reboots, I see the first few lines up tp and including "savedefault", and then the message "Error 1: Filename must be an absolute pathname or blocklist.   Press any key to continue" appears.  On pressing a key I am returned to the boot menu.  The result is the same if I choose the "recovery mode" option on the Grub menu.

The reason that I don't want Grub to use the MBR is that I use a Windows multi-boot program, "Boot Magic".

I have repeated the installation procedure, with exactly the same result.  I had already installed Ubuntu successfully on another PC, with a very similar setup (including "Boot Magic", except that hard drive "hda" was used.  I tried to find some difference in the configuration, without success.  The next command in the Grub file is "boot", but doesn't seem to be reached. 

Both machines can be booted into Fedora Core 3, so that I can access the Ubuntu files; I have a CD with Knoppix if required.  I also have Win98 on both machines.

---

### Post by carytid9 on 2005-05-12
I have partially resolved the problem.

It now appears that the Grub command "savedefault" is stopping Ubuntu from booting. If this command is removed from the file /boot/grub/menu.lst, boot goes ahead and there does not seem to be any adverse effects.  It's not clear to me what the function of "savedefault" is; I couldn't find anything in "info grub".

Is this a bug, and should it be reported as such? 

Please advise.

---

