---
title: "kernel panic after upgrade from 14.04lts to 15.04/15.10"
date: 2016-01-29
forum: Installation &amp; Upgrades
---

### Post by cvgaviao on 2016-01-29
I`m writing this using 15.10 live from a usb stick.

I'm using a dual boot (UEFI) machine with windows 8.1 and ubuntu 14.04Lts.

I decided to update because my work. I need to build a VM with new version of Vagrant and need to create systemd files for a product installation. 

Yesterday I changed the 'software & updates' notification combobox from long-term to new version. then I used the update manager to do the install.

I had some problems with package versions that prevents ubuntu-desktop to be upgrade. but that I was able to fix using synaptic to fix package versions.

and the installations process go on, ok apparently. but after reboot I was surprised by a kernel panic message.  

in the grub menu I can see only 2 old versions: vmlinuz-3.13.0-76-generic and vmlinuz-3.13.0-77-generic. and both has the same problem.

I have daily backups made by dejadup. 

I started an install process with this usb stick but it asked me to set something related to EFI that I did't understand. I got scared to mess with the windows and abort.

> The partition table format in use on your disks normally requires you to create a separate partition for boot loader code. This partition should be marked for use as an "EFI boot partition" and should be at least 35 MB in size. Note that this is not the same as a partition mounted on /boot.

If you do not go back to the partitioning menu and correct this error, boot loader installation may fail later, although it may still be possible to install the boot loader to a partition.

could someone please give me a help ? what options I have?

[http://paste.ubuntu.com/14697275/](http://paste.ubuntu.com/14697275/)

---

