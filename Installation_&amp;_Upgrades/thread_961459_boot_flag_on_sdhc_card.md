---
title: "boot flag on sdhc card"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2008-10-28
I'm using an eee 901, attempted to install XP on a 16 GB sdhc card and it seemed to go alright, however will still not boot.  I have just tried using gparted to check and set the boot flag and it doesn't seem to be able to do it.  When I put the card in the drive, ubuntu 8.10 reads it just fine and shows me all the files on the disk, yet gparted gives error messages.  Is gparted robust or might it miss something?  Is there another way to turn on the bootable flag?  The sdhc is formatted to fat32.

Thanks

Jim

---

### Post by caljohnsmith on 2008-10-28
What kind of error messages does gparted give you? That is not a good sign, but it might not be anything important depending on the error messages. You can use "fdisk" to set the boot flag on a partition by first doing the following from a terminal (applications > accessories > terminal):
```
sudo fdisk -l

```
See what drive your card is, like sdb for example, and then do:
```
sudo fdisk /dev/sdb
```
Then type "a" and return, enter the partition number for Windows (probably "1" if only Windows is on the SDHC card), then "w" to write the change to disk. Then use the "sudo fdisk -l" command again to see if the Windows partition is now marked as bootable. Please post the output of the first command above if you need any help, otherwise let me know how it goes. :)

---

### Post by jamaas on 2008-10-29
Thanks caljohnsmith

No luck but fdisk tells me I have 4 partitions on this 16 GB sdhc card and they are not clearly defined at sectors divisions or something ... news to me!  I might have to reformat it and try to install the os on it again.  Thanks for help, might be back to you!

Jim

---

