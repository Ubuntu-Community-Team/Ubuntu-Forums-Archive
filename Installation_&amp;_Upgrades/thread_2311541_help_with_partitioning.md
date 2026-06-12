---
title: "help with partitioning"
date: 2016-01-28
forum: Installation &amp; Upgrades
---

### Post by Hotchilli on 2016-01-28
here is my partition at the moment 
gtp partition table



  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    System             100 MB  1024 KB--GPT,EFI
  Partition 6    Primary              8 MB   101 MB-free
  Partition 3    Primary             70 GB   117 MB---win10-can delete
  Partition 5    Primary            405 GB    70 GB--vmware DATA  need to KEEP 250gb
  Partition 2    Primary            456 GB   475 GB-free

I am following a howto that encrypts the hard drive the recommened format is below please make suggestions how to amend my current partition scheme 



The installation here described assume:

Installation of Linux on: /dev/sda

Physical volume for encryption build on: /dev/sda2

Boot loader installation point: /boot/efi (inside EFI partition)

EFI Partition: /dev/sda1

Physical Volume: /dev/mapper/sda2_crypt

Volume Group: ubuntu

Logical Volume for swap: swap

Logical Volume for root: root


thanks
hotchilli

---

### Post by ajgreeny on 2016-01-28
With the info you have given it is not easy to know exactly what you're asking, nor what the current situation is.

Do you have any OS at present that you want to keep or is this a new install that will use the whole hard disk?  You mention Win 10 but say it can be deleted; you could however dual boot if that makes more sense to you, but I am not able to help with encryption as I've never used it.

Tell us more and if possible show a screenshot from gparted of the disk as it is at present.

---

### Post by Hotchilli on 2016-01-28
thanks for your post

no I am sorry but win 10 is on a rescue usb if i need it has to go the only data I need is vmware data on E partition size 250gb--E is in fact bigger than 250gb but that is the size of the vmware data
 the rest can be for linux 

here is a capture

---

### Post by ajgreeny on 2016-01-28
Sorry but that is from Windows and it doesn't really help much; not me anyway as I don't use Windows any more.

The disk seems to be totally used by NTFS (Windows) partitions at the moment, except for the small fat32 EFI partition at the start.  I presume you mean that Disk E: has 250GB of data on it, ie, your vmware data, that you nee4d to keep and the rest can all be deleted to make room for the Ubuntu installation; correct?

If that is right you can simply boot to the Ubuntu install USB (in UEFI mode as the machine is set up that way), choose the "Something Else" option at partitioning, and either delete all the partitions, having backed up the data in E: first, or delete all but E: leaving free unallocated space in place of whichever partitions have been deleted.

I know nothing of vmware as I use VirtualBox for my VMs, and I do not know if it's possible with a Linux host to run a VM on an NTFS partition, but I can not see why that should not be possible; others may be able to help with that uncertainty.

Why not keep Disk E: untouched with all its vmware data and install Ubuntu into the remaining unallocated space; that would seem the most appropriate way to go.

---

### Post by Hotchilli on 2016-01-28
sorry here a screenshot on linux

could you relate your reply to the partition scheme in the first post I agree leaving the vmware data as it is.

---

### Post by grahammechanical on 2016-01-28
> Physical volume for encryption build on: /dev/sda2

That would be impossible. The partition is too small to install Ubuntu into whether using encryption or not. You need to create space for Ubuntu by resizing/moving the existing partitions. It is best to use Windows utilities to work with Windows partitions and Linux utilities to work with Linux partitions.

You have GPT which means that you do not necessarily need to delete partitions. Unlike an MBR partition table with its 4 primary partition limit with GPT we can create many, many more primary partitions. Once we start deleting and creating partitions then labels such as sda2 & sda5 change. 

You have 2 partitions that can be resized.

G: (sda4) ntfs 405 GB used 143 MB
E: (sda5) ntfs 456 GB used 257 GB

Which one you choose is up to you. You know what is in them. We do not install Ubuntu on an ntfs partition. We create unallocated space for Ubuntu and let the Ubuntu installer format the partition, even creating the necessary partitions out of the unallocated space.

sda1 fat 32 ESP should not be deleted. Install Ubuntu in EFI mode and the Ubuntu installer will make use of the ESP partition to put Ubuntu efi boot files in. Install Ubuntu in BIOS/Legacy/Compatibility mode and you will need to create a bios boot partition. So, make sure that the Ubuntu live session is loading in efi mode then Ubuntu will be installed in efi mode.

Regards.

---

### Post by Hotchilli on 2016-01-28
ok thanks for your post

I can use the whole of the disk but not the vmware data part

here is the first part of howto

The procedure described in this guide/tutorial is divided in 4 steps:


Step 1 – Set up the target HDD, require Ubiquity

Step 2 –  Set up the LVM, Physical Volume, Volume Group and Logical Volumes for root and swap,
                require a few Terminal commands

Step 3 – Set up of the Linux installation, require Ubiquity

Step 4 – Fixing, patching and updating of the Linux installation made with Ubiquity, require a lot of
               Terminal commands. Only if necessary configuration of EFI default boot entry (facoltative).



Appendix B – Emergency tools - How to access your encrypted partition with your  Ubuntu Live CD

 

The Terminal commands listed in this guide/tutorial are typed in RED COLOR.


hotchilli

---

### Post by ajgreeny on 2016-01-28
Do you really **have** to have LVM and encryption?

I have no knowledge of either of those so will leave you in the care of others from now on if you must use those two installation modes.

---

### Post by oldfred on 2016-01-28
If not including the vmware partition, then you do not have full drive encryption. 

The default install of full drive encryption erases entire hard drive and creates the ESP - efi system partition and /boot partition as they cannot be encrypted and the rest of the drive is LVM and encrypted. You have to do all that manually if you want to exclude part of the drive.

There also is an option to just encrypt /home. Or if you just have some data to encrypt to can manually encrypt that also. I do not use encryption except for my password file.\

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by Hotchilli on 2016-01-28
thanks for your reply

yes your correct its not full disk encryption if the data partition is not included
also many thanks to other posters for your valuable contibution

thanks

hotchilli

---

### Post by oldfred on 2016-01-29
This was your reference.
 Manually create
[http://community.linuxmint.com/tutorial/view/2061](http://community.linuxmint.com/tutorial/view/2061)

I do not use LVM nor encryption, so I do not know if totally valid. What seems different is that it does not use a /boot partition. It was my understanding that neither the ESP nor the /boot partitions could be encrypted as they have to be loaded before the software to unencrypt file is loaded.

But grub does work from FAT32 as Ubuntu installer is only on FAT32. And I have seen in Rod Smith's rEFInd instructions ways to use UEFI to directly boot or have more boot files in the ESP. I believe that is why he normally suggests larger ESP of 500 or 600MB where Windows is often 100MB, but normal installs do not use much.
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

### Post by Hotchilli on 2016-01-29
Thank you for posting the link to the howto as mentioned he seems to be installing on oracle , which is good as its new and anything could happen.

I think the howto which he claims would work on Ubuntu was written in june 2015 and has been updated from time to time. He has written another one but for a MBR 
partitioning  scheme here [http://community.linuxmint.com/tutorial/view/2026](http://community.linuxmint.com/tutorial/view/2026) - the one you kindly posted is for UEFI.

I will have a closer look at it over the weekend

hotchilli

---

