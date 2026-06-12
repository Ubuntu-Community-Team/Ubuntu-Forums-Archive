---
title: "UEFI install: where to install boot loader"
date: 2021-03-24
forum: Installation &amp; Upgrades
---

### Post by DavidS on 2021-03-24
My partner's computer has Ubuntu 16.04 installed, and I now want to put 20.04 on to another partition.

The computer is set up for UEFI boot only, and it is definitely booting from the hard drive in UEFI mode, and also from my live 20.04 drive (USB).

According to [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) "in a UEFI-mode installation, Ubuntu will not ask you where to install the boot loader".

But it *does* ask, and it gives me the options of installing on the disk or on any of the various partitions apart from the swap area.  /dev/sda1 is the EFI partition, and /dev/sda4 will be the root partition of the new installation.

So where should I tell the installer to put the boot loader?  /dev/sda, /dev/sda1 or (unlikely, I think) /dev/sda4?

David

---

### Post by tea for one on 2021-03-24
Ubuntu will install the bootloader in the first drive that is available - dev/sda in your case.

There is a bug (or possibly feature) in the installer where it ignores user choices [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

The last installation (i.e. Ubuntu 20.04) will then take control of grub and should add your partner's 16.04 OS.

---

### Post by DavidS on 2021-03-24
Thanks for your quick response.  I suspected that perhaps it didn't matter what I did, but it's nice to have that confirmed.

I looked at the bug report you linked to, and really does sound like time somebody managed to fix this!

David

---

### Post by ubfan1 on 2021-03-24
I hope you did add yourself to the "Does this affect me?" list in the upper left corner of the bug window.  Old as the bug is, it is a superset of an even older USB specific bug, which  was then declared a duplicate, and the "Does..." numbers got restarted at 0 for the new bug.:^(

---

### Post by Dennis N on 2021-03-24
That selector box (where to install the bootloader) works only in BIOS installation mode. Otherwise, as already mentioned, it's ignored for UEFI.

Installing 20.04 and also keeping 16.04 will result in the computer booting to 20.04 on startup since it replaces the 16.04 boot files in the EFI system partition (ESP) with its own. If you want keep booting to 16.04, you can backup the Ubuntu folder from the ESP somewhere else before installing 20.04, and copy it back after 20.04 is installed.

---

