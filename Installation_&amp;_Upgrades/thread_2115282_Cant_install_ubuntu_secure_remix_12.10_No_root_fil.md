---
title: "Cant install ubuntu secure remix 12.10: No root file system is defined"
date: 2013-02-12
forum: Installation &amp; Upgrades
---

### Post by timgtim on 2013-02-12
Hi!

I'm trying to install ubuntu secure remix 12.10. I have pre-installed windows 8 on my Asus zenbook and i want to be able to dualboot with the two os. I'm booting from the live usb and when i try to install by choosing the installation type "something else" i get the following error msg:

[I]No root file system is defined.
Please correct this from the partitioning menu.[/I]

So i assume i need to create some kind of boot partition for ubuntu. In GParted i see many partitions but i don't know what to do as i'm new to this. A screenshot of the installation window and the gparted is in the attachement. Pls advise me of what to do :) Thx!

---

### Post by darkod on 2013-02-12
That message appears because you are trying to continue the install without specifying a root partition. That is the main system partition where it installs.

The disk doesn't have any unallocated space. You can't install until you create some.

For example, boot win8 and open Disk Management and shrink one of the ntfs partitions (for example the big 260GB) partition. How much you shrink it depends on how much space you want to allocate to ubuntu.

Leave the newly created space as unallocated, don't create ntfs partition in it.

Reboot win8 few times.

I'm not sure if you are aware, but for win8 and UEFI you need to install in a particular way, you need to boot the ubuntu cd in uefi mode too.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Also for many win8 machines you may need to go into bios and disable secure boot and fast boot.

Google around installing dual boot with win8 because it's not the same as before due to changes done by Microsoft and the new UEFI system.

---

### Post by oldfred on 2013-02-12
Several threads with different models of Asus. I assume all Asus use similar UEFI, but customize it a bit for each model.

       Asus N56VJ-SH71-CD - shows partitions after install
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

---

### Post by timgtim on 2013-02-12
Thx for your replies! Problem solved! :) I had to reserve some free space for ubuntu (disk manager in windows, shrinked an existing partition). Installation went well after that. Got ubuntu working but instead i couldn't boot windows. This was solved easily by running boot-repair in ubuntu! :)

---

