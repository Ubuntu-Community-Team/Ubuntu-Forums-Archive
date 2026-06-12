---
title: "Installing Ubuntu Live CD to Flash Drive using casper-rw partition not file"
date: 2015-03-21
forum: Installation &amp; Upgrades
---

### Post by vas2 on 2015-03-21
Ok, so here is the situation.  I've preformatted my 64GB Flash drive with a Live CD directory that is an exact specific size to contain the entire live CD without any extra free space at all.  I've also pre-formatted for an exactly 24GB casper-rw partition with 34.76GB storage partition after.

However, if I try to use UNetBootin, it wants to create a casper-rw FILE, instead of using the partition I made.  I would rather not go through hours of trouble doing this all over again.  The last time, I had to create the 8GB casper-rw file, then edit the drive by deleting the file and making an 8GB casper-rw partiton after that and keep trying to shrink the old volume over and over again which didn't want to shrink properly for a while.

Is there linux software I can use to install a Linux Live CD to my pre-partitioned flash drive so I don't have to do the pain in the ass method of editing all the files all over again just to make casper-rw use a partition rather than a file?

EDIT: I forgot to mention, I'm using a VM with LiveCD running in it to do all this.

---

### Post by ubfan1 on 2015-03-21
You can make a minimal casper-rw (1G is the current min default), then just delete the casper-rw file. The partition labeled casper-rw with an ext filesystem will be automatically used.  To avoid even losing the 1G, you can create a  non-persistent install, then just edit the word "persistent" onto the "linux" line in one of the syslinux config files (forgot  which one, should be easy to find). Then the casper-rw partition will be used, and no space wasted on the FAT partition.

---

### Post by vas2 on 2015-03-22
I was hoping there was software that could just use the partition rather than require pain in the ass method of editing files all over the drive after you install then re-shrinking the volume after and such.  Last time, I had to delete several files then edit some more to get it to work right.  Just a big hassle really.

Another issue I had was when I installed Linux, not as a LiveCD, all the LiveCD things didn't install with it, including gparted and such.  Would be nice to have Ubuntu completely writable on my flash drive and all, not as a LiveCD, but with all the LiveCD diagnostic tools and such.  :P

---

### Post by ubfan1 on 2015-03-22
I prefer having some free space on the FAT partition, so Windows can see it if necessary.  You can reduce the casper-rw file size  to below 1M by editing  the MIN_PERSISTENCE line in the /usr/lib/python3/dist-packages/usbcreator/misc.py file.  Since the partition gets picked up if the file is not present, I don't know what sorts of edits you are referring to, although I never tried to resize the FAT partition.  Of course, you can install any packages you like on a full install.

---

### Post by vas2 on 2015-03-23
I'm not using FAT.  Windows can't see partitioned flash drives anyway so partitioning a flash drive in FAT is useless.  I use ext4 for every partition on the flash drive.

The problem is that when I install Linux full install, nothing is installed on it and it can't use my wireless network to connect and I have no clue what other important things I am missing.

---

### Post by sudodus on 2015-03-23
There are tips in the following links for creating a persistent live system with a casper-rw partition.
[URL="http://ubuntuforums.org/showthread.php?t=2259682"]
One pendrive for all PC (Intel/AMD) computers[/URL]

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by oldfred on 2015-03-23
Not sure what issues you are having with full install. You should be able to just install Ubuntu to a 64GB flash drive just like you would any external drive. Only use Something else. With 64GB having one larger / (root) or a smaller 20GB root and separate data partition is totally optional.

I then in my data partitions on my flash drives use grub2 to directly boot ISO files. I then have a multi-purpose install/repair/emergency boot flash drive.  I now only use gpt partitioning for all drives, so I can have either or both a bios_grub for BIOS or an efi partition for UEFI boot.

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

      Multiboot flash drive with second partition 
[http://ubuntuforums.org/showthread.php?t=2260697](http://ubuntuforums.org/showthread.php?t=2260697)

 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

      [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

