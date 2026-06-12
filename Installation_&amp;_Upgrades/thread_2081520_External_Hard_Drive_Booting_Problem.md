---
title: "External Hard Drive Booting Problem"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by Zaldabus on 2012-11-07
I recently setup Ubuntu 12.10 on an external hard drive.  

Here’s my setup:


HP Dragon Laptop

 - Internal drive(sda) : 200GB (Windows Vista)
- External drive 1(sdb): USB hard drive (Buffalo 1.5TB)
- External drive 2(sdc): USB hard drive (Buffalo 1.5TB)
- External drive 3(sdd): USB hard drive with Linux partitions at the beginning (/boot, /, swap) followed by NTFS data partition, and with sdd set as the boot loader  device (Buffalo 2.0TB)



When I first went to boot up from the external hard drive, I got the following error:


Non-system disc or disc error
replace and strike any key when ready


However, after disconnecting my other external hard drives I got the computer to boot into Ubuntu.  Considering I have next to no experience with a Linux distro I'm quite pleased I got it to work at all.  But if possible I would like to be able to boot into Ubuntu without having to unplug my other hard drives first.  



My guess at the moment is that something that was pre-installed on one of the other drives is messing with the boot sequence causing problems booting up.  Any one have an idea of how to fix this problem?

---

### Post by oldfred on 2012-11-08
Some BIOS will only see one bootable external device?
Does you system show external bootable devices as hard drives? 

My laptop will only boot with one USB port used. But my Desktop will show all the flash drives installed but as hard drives.

---

