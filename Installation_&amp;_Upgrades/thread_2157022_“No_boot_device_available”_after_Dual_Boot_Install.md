---
title: "“No boot device available” after Dual Boot Install Attempt with Windows 8"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by lewis0518 on 2013-06-24
I was trying to install 13.04 Ubuntu to my Dell Inspirion desktop that already has Windows 8 (machine is a couple months old).

  Here's the string of events as they played out:
  
[LIST=1]
[*]I followed the instructions here to create two new partitions (swap space & primary) as described here: [http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/)  and finished the install wizard.
[*]After which, Windows 8 was loading as it normally had in the past.  (i.e. nothing appeared to have changed from a boot perspective)
[*]Ran boot-repair off Ubuntu 13.04 CD & received Locked-ESP detected error message
[*]Saw this site:  hxxp://ubuntuforums.org/archive/index.php/t-2112273.html, so removed the  boot flag for /dev/sda1 & restarted with the intention of following  the rest of the steps.
[*]Nothing now loads.   Following message displays on load:  No boot device available SATA0: Installed. SATA1: Installed.
[*]I tried going to legacy boot but ultimately switched back to UEFI as I didn't think it was accomplishing anything
[*]I have also disabled SECURE Boot in the BIOS --- with no perceived affect.
[*]I also tried setting gparted boot flag to the ubuntu partition vice Windows partition with no affect.
[/LIST]
  I'm kind of lost here, as this is beyond my technical knowledge -- so any assistance or tips would be greatly appreciated.  
  Here is my pastebin from bootrepair:
  [http://paste.ubuntu.com/5794027/](http://paste.ubuntu.com/5794027/)

---

### Post by oldfred on 2013-06-24
UEFI only boots from efi partition. And the boot flag is what defines the efi partition, so turning off boot flag prevents booting. Also with gpt partitioning the boot flag can only be on the efi partition, never any place else.

Some with locked efi partition were able to run chkdsk from Windows and fix it. Most had to fully back it up (which is a good idea anyway), delete it, and recreate a new FAT32 formatted partition with the boot flag and restore the efi files from backup.

       grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)

Lots of UEFI info in link in my signature.

---

