---
title: "Intalling encryptd Kubuntu"
date: 2023-07-07
forum: Installation &amp; Upgrades
---

### Post by bjngchn on 2023-07-07
I want to install encrypted kubuntu.

So what do I do. Can I start from any kubuntu download? Do I need alternative download?
When burning ISO file, do I need empty USB flash disk , or will any work (may be erased, this is ok). 
When burning do I need another program like Rufus? 
Does it matter whether I download ISO file on a Windows computer or a Linux computer?

Everyone says, for fully encrypted disk, I need LVM, but last time LVM and encryption
were different selections. I chose encryption (Ubuntu download from Windows),
 and when installation was compelte, there was only 2GB of encrypted space.
So I will start over, possibly with a kubuntu  download from a linux laptop.

---

### Post by Frogs Hair on 2023-07-07
> When burning do I need another program like Rufus?  Yes

> When burning ISO file, do I need empty USB flash disk , or will any work (may be erased, this is ok).  Use What you have on hand as long as it has enough space for the ISO. 

> Does it matter whether I download ISO file on a Windows computer or a Linux computer? Not really except for the software used to create the USB. Rufus is not available for Linux, so an alternative would be required .

You'll e have to wait for more input on the encryption questions.

---

### Post by Impavidus on 2023-07-08
"Can I start from any kubuntu download?"
Yes. Is there even an alternative download for Kubuntu?

"When burning ISO file, do I need empty USB flash disk , or will any work (may be erased, this is ok)"
Any sufficiently large usb drive will work. It will be erased in the process.

"When burning do I need another program like Rufus?"
Only if you do the burning on a Windows system. If you use a Linux system, the required tools are present already. You only really need a file copy tool. dd, cp, even cat will work.

"Does it matter whether I download ISO file on a Windows computer or a Linux computer?"
Only in the sense that the computer on wich you download is probably the same as the one where you burn the live disk.

---

### Post by aljames2 on 2023-07-08
> **bjngchn said:**
> Everyone says, for fully encrypted disk, I need LVM, but last time LVM and encryption
were different selections. I chose encryption (Ubuntu download from Windows),
 and when installation was compelte, there was only 2GB of encrypted space.
So I will start over, possibly with a kubuntu  download from a linux laptop.

LVM is a logical volume management tool.  Allows you to place specific groups of data within logical volumes to create separation. These LVs can be expanded as needed to help use only the storage that is needed, and LVM allows for snapshotting which is a useful tool for staging your data, so you can make backups.  The snapshot itself is not a backup, but a tool to help you with creating backups.

Encryption in the installer is whole disk LUKS encryption, unless you have first prepared your disk by pre-setting up individual LUKS partitions using cryptsetup from a command line before running the installer.

LUKS + LVM is possible, and very common, if you want both.  However, one is not a prerequisite to the other.  You can use either, without the other.

---

### Post by MAFoElffen on 2023-07-10
> **aljames2 said:**
> Encryption in the installer is whole disk LUKS encryption, unless you have first prepared your disk by pre-setting up individual LUKS partitions using cryptsetup from a command line before running the installer.

LUKS + LVM is possible, and very common, if you want both.  However, one is not a prerequisite to the other.  You can use either, without the other.
1st sentence: Well, sort of true. But not the whole disk persya, but rather the Device, which is the whole 'root partition'.

2nd sentence = true, but needs further explanation.

My comments. 
LUKS, if created, is an encrypted storage container that resides just within the confines of the partition. Inside it could go various things. An LVM container, ZFS container, Ohter Volume mangers or a just a filesystem. If LVM, then a Volume Groups -> Logical Volume -> Then filesystem. If ZFS, then pool -> Dataset. BTRFS is sort of the methodology of LVM and ZFS. Then it could be just a filesystem within the LUKS container.

But visualize all those just like Russian Nested Dolls. Shells or layers, that reside within the next layer.

The cann'ed scripts on the 22.04 Installer, for encrypted, there are two: LVM and ZFS. Both are a good implemetation for someone starting out. Who just need something simple, and will work, with very little skills required to make it work. They just work out of the box. A few checkboxes and everything is done for you.

For my test-bed, for testing my contributions to boot-repair and boot-info, I create my installs manually... Creating the partitions I want, the LUKS containers, Then after unlocking the created LUKS volumes, I create whatever other structure within them... Then finish the install.

You can do what you want... But easiest for newer users, to use the canned scripts then modify the system after that install to personalize it or to expand that installation. (like adding a mounted Home, instead of it being inside the root / OS container.)

---

