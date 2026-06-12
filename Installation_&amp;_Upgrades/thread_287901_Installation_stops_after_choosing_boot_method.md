---
title: "Installation stops after choosing boot method"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Milenacroft on 2006-10-29
Please! Help me...

I've already created partitions Ext3 in my HD Seagate (using Partition Magic), and have installed WinXP Pro as the active OS in the NTFS partition.
Then, when I've tried to install Ubuntu 6.06, it stopped before Mount the root file system, and I've needed again and again to reboot the system by Reset button.
Later, without any hopes, I've burried a DVD Reader (because I've just a CD Reader in my PC) and have tried to install Fedora Core 5 in a DVD Media three times.

At first, I needed to create a SWAP partition that was required to go on with the configurations.. until here was ok.
Then, the installation was completed and seemed alright, but when GRUB runned and Fedora was chosen, after to pass by kernel part, the message: "buffer I/O error on device hdd, logical block 2" started to run again and again.

In the second trying, I've organized the partitions in another way, letting a NTFS w/ 10GB, 1 SWAP w/ 512MB, 1 Ext3 w/ 10GB, and and extended partition containing 2 NTFS parts and 1 Ext3. And installed Fedora again (by the beginning) in the 3rd primary partition. It installed normally as the 1st time.
The message about I/O error persisted.

Finally, in my 3rd trying, I've decided to put the SWAP partition as logical, inside the Extended partition. The settings was: 1 NTFS primary partition - 10GB, 1 Ext3 primary - 10,5GB, 1 Ext3 pri - 10GB, 1 Extended containing: 1 Ext3 w/ 8GB, 2 NTFS w/ +/-15GB each, and the last, a SWAP w/ 640MB.
After the installation, I was really excited to run Fedora finally, but the message persisted!

The UBUNTU installation went on after Mounting root file system, but just when I've tried to install it w/ Fedora installed.
The bad new is that always stops when it's entering in the graphic method of installing, in the natural way and safe mode.

Can it be my machine, that's a Celeron 400MHz, 256MB Ram, 8MB Video Onboard?
After choosing GRUB as the method to get inside some system, without Fedora it doesn't run.

My Kurumin CD doesn't work after I tried to install Linux in the PC.

I hope to have written clearly and have given all the necessary informations...

---

