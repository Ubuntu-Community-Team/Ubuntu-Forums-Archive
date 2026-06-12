---
title: "Upgrading non-OS HDD on Server build + problems mounting live usb"
date: 2016-08-25
forum: Installation &amp; Upgrades
---

### Post by folic86 on 2016-08-25
Hi folks,

So I have a server which I built a whole while back. But, I need to swap out a drive, and replace it with a bigger one. 

That seemed easy, as I just unmounted the one I didn't want. However, the new one is a 3tb WD red, so when I format it, it says the partition isn't aligned. 

I can't seem to rectify this, as I can't get my live USB stick of gparted to mount, or run. And now I'm just really confused! It says (using the report tool/log in terminal) that it is dev/sdf with a partition marked sdf1. But that will not mount.

I'm fairly n00by at Linux, but if someone could tell me what I'm doing, then I'd really appreciate it!

I just want more storage space!! &#128546;

---

### Post by oldfred on 2016-08-25
Are you trying to use the 35 year old MBR partitioning? MBR has a hard limit of 2TB as even GB was not thought of 35 years ago.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

       
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 
    
Also if USB drive, some older drive caddies do not support either gpt, or large drives.

Even if only a data drive currently, I like to include both the ESP, FAT32 formatted partition for UEFI boot and a bios_grub 1 or 2MB unformatted space for BIOS boot. Then I can install either UEFI or BIOS boot versions of Ubuntu without having to totally repartition/reformat drive.


       
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive.

---

### Post by folic86 on 2016-08-25
Thanks, sorry, maybe I wasn't clear.

I'm installing an internal HDD (details in original post) but that is formatting (as GPT) misaligned! 

The USB stick (pen drive) is to make a liveusb for installing gparted (which I can't seem to get to work).

So, the suggestion to use gparted, is helpful, but as I can't seem to install it, is less helpful!

---

### Post by folic86 on 2016-08-25
The stick is formatted as FAT32 FYI, and I intend to format the WD HDD as ext4

---

### Post by oldfred on 2016-08-25
That the flash drive is FAT32 is normally correct.

There also is gparted on the Ubuntu live installer, desktop version. 
Although I have not had issues with gparted live.
Since server does it have video? Gparted requires gui.

---

### Post by folic86 on 2016-08-25
Hi Fred, thanks for that.

I tried installimg it using sudo get-install gparted, and now that seems to have worked. 

I'm at the create new partition bit - ext4, 2,861,587MiB - but do I want to align it to MiB or to Cylinders, given the issue I had with it being misaligned due to using WDs Advanced format?

---

### Post by folic86 on 2016-08-25
Oh and yes, I have a GUI output!

---

### Post by folic86 on 2016-08-25
[h=3]I used gparted to create a partition aligned with MiB, I now try to mount it, and get this message via webmin.....

Failed to save mount : Mount failed :mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/h]

---

### Post by SeijiSensei on 2016-08-25
Try formatting it again manually with
```
sudo mkfs -t ext4 /dev/sdXN
```
where X is a drive letter and N is the partition number.  Use "sudo blkid -l" to determine which partition you want to format.

If this is the only drive in the machine, you're probably going to be formatting /dev/sda1 unless you created a separate /boot partition at installation (unlikely).

Why didn't you just leave the old drive in the machine and expand the storage by adding the new one and mounting it somewhere like /data?  If you still have the old installation, I'd put it back into the machine and make sure it is the primary drive.  That should boot up cleanly, no?  Now install the second drive and check in the BIOS to make sure the original drive is still the boot drive.  When you're back up again, format the new device and mount it into the existing directory tree.

---

