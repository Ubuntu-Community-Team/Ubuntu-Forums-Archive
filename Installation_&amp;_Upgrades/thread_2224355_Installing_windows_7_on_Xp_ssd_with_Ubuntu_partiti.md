---
title: "Installing windows 7 on Xp ssd with Ubuntu partition on d drive."
date: 2014-05-15
forum: Installation &amp; Upgrades
---

### Post by kwjorders on 2014-05-15
I'm thinking about upgrading to windows 7 since Xp is no longer supported.  My setup is I have my windows Xp on its own ssd drive designated c while I have my d drive which has a windows partition with data on it and a Linux partition on the d drive as well.  I'm wondering if there is any way to save my Linux partition when I upgrade to 7.
-Thanks

---

### Post by oldfred on 2014-05-16
If you have multiple drives, generally better/easier to have Windows on one drive and Ubuntu on another drive.

Also XP does not easily work with SSD. I found if you want trim you have to enable AHCI, but XP does not have that driver and can only 'easily' add it during install. Newer Windows have drivers for AHCI.

Windows installs often rewrite partition table and if Linux partition is in an extended partition as a logical, Windows just does not include it. Space is there there and often testdisk can restore it, but it is a bit of a hassle. Besure to backup partition table after any resize and then you can easily restore it.

If MBR, there also commands for gdisk if using UEFI & gpt partitioning.
       Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by fantab on 2014-05-16
Since you are booting XP it is unlikely that you have UEFI.
If you have a working Ubuntu already installed then post the output of the following:

```
sudo parted -l
sudo fdisk -l
```

That will tell us how your HDD/SSD and their partitions are laid out.

Check your BIOS for 'SATA MODE' or something of that sort... and set it to AHCI. 

You have to be careful during windows install/upgrade... you have to know your partitions.
Just Boot with Windows7 Install Disc and choose the same XP partition for Windows7. 

Windows Install will overwrite the MBR and as such you lose Grub and consequently Ubuntu will not boot.
The fix is to re-install grub with Live Ubuntu: [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

Like oldfred suggests, installing Windows and Linux on separate HDDs/SSDs is a good idea, that is, if you have more than one HDD/SSD.

---

### Post by Mark Phelps on 2014-05-16
Just so you know ... there is no MS-supported "upgrade path" from XP to Win7.  You might be able to find articles claiming to do that, but if you read closely, they all will result in a Clean Install, meaning, no apps will get transferred from XP to Win7.  So basically, you'll be starting from scratch with Win7.

---

