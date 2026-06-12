---
title: "Create multi-partition bootable external hard drive"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by unckybob on 2010-09-10
I would like to be able to boot into any of my bootable images (ubuntu, kubuntu, ubuntu-alternate, knoppix, etc...), all from the same external hard drive.

I have iso's of several bootable images (ubuntu,kubuntul,ubuntu-alternate, knoppix, etc). I would like to somehow put them all on one external USB drive. Boot into it on any computer. Then choose which image to boot from at startup.

I thought I could make several partitions on the drive. Then copy each individual image to its own partition with dd.

# dd if=/pathtoimage/file.iso of=/dev/devicenode1 bs=1M [substitute devicenode1,2,3, whatever for the correct partition]

Then if there was some utility that I could install to the external drive, I could tell it at boot time which partition to boot from. 

Of course I don't want to limit myself to just doing it this way if there's something better out there. 

Can someone please help?

---

### Post by oldfred on 2010-09-11
this is to put several ISO on one flash drive.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

This will boot an ISO from a hard drive.
Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 

Another - multibooting multiboot055.sh:
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)

---

### Post by unckybob on 2010-09-11
Those links are great, but they only work for bootable live CD iso's that grub 2 supports. 

I should have written out what I'm trying to do more clearly. 

I've got all these bootable CDs and DVDs that I use all the time. I'd like to somehow get the information from these into one small external USB hard drive that I can just carry around with me. Then when I need to, I can somehow boot off the drive and select what I want to boot into?

---

### Post by oldfred on 2010-09-11
I have not done it but if you dig into the multibootUSB script, it copies kernel and initrd or whatever is required to boot for those that grub2 does not directly boot.

---

### Post by C.S.Cameron on 2010-09-11
> **oldfred said:**
> I have not done it but if you dig into the multibootUSB script, it copies kernel and initrd or whatever is required to boot for those that grub2 does not directly boot.

+1

I'm not sure if MultiBootUSB will work with an external hard drive but you should be able to install what you want on a flash drive and then copy over to hard drive once grub2 is installed.

---

### Post by atti84it on 2010-09-25
When you loopback an iso image (for example with MultiBootUSB) are you able to write files in it? (for example saving documents.. using it as a normal operating system..)

---

### Post by C.S.Cameron on 2010-09-25
> **atti84it said:**
> When you loopback an iso image (for example with MultiBootUSB) are you able to write files in it? (for example saving documents.. using it as a normal operating system..)

It gets complicated.
The 'buntus use casper-rw, (file or partition), for persistence and do not work so well sharing a persistence file.
Puppies persistence works ok and I think will work with different versions.
I could not get persistence working with Fedora.

Persistence is discussed a bit in the MultiBootUSB thread.

---

### Post by atti84it on 2010-09-25
Thanks a lof for the answer!!

---

