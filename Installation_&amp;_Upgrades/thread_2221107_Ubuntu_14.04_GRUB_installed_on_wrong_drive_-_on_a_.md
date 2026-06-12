---
title: "Ubuntu 14.04: GRUB installed on wrong drive - on a RAID disk"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by parish on 2014-04-30
My machine has been running Ubuntu for several years now. Started with a single 250GB IDE drive, then added a couple of 1.5TB SATA drives configured as RAID1 with mdadm. It was running 12.04.4LTS with the OS on the 250GB and the RAID just as a data drive. The disk config was:

/dev/sda 1.5TB SATA
/dev/sdb 1.5TB SATA
/dev/sdc 250GB IDE

About a month ago I started having problems with packages. After lots of trawling the 'net and trying numerous things, without success, I found a thread where someone suggested running aptitude as it was more "thorough" in fixing problems than apt-get. Bad move! Although I followed the step-by-step instructions to the letter, it removed dozens of packages. Apps disappeared, including Ubuntu Software Centre and update-manager. Trying to re-install them (and anything else) was a nightmare; errors left, right, and centre.

After spending way too long trying to fix the mess, I decided to take the MS approach and do a clean install of 14.04 (I was worried that trying to update a trashed system would not be a good idea).

So, backed up - TWICE - everything I needed off the 250GB HDD, made a bootable USB stick and did a clean install, making 110% certain I picked the right drive.

When GRUB was installing I noticed it was doing so on /dev/sda. I just assumed the drives had been assigned differently, but the resulting system wouldn't boot. No errors, just a blank screen with the cursor flashing in the top left corner.

Using the BIOS boot selector I tried booting from the disk it considered the Primary Master - one of the 1.5TB drives - and it booted!! After a tense couple of minutes thinking the installer had goofed and trashed the array I found that it hadn't; the OS was correctly installed on the 250GB HDD.

I installed mdadm and ran

```
$ sudo mdadm --assemble --scan
```

and the array was assembled correctly. Created a mount point and added an entry in /etc/fstab

So, everything works, it's just that it will only boot from one of the RAID disks which is, at the very least, illogical but seems just plain wrong.

What I'm really concerned about is that I expect I'll need to replace the 1.5TB drives with 3TB or 4TB ones later this year which could leave me with an unbootable system.

So, why did the installer do this and, more importantly, how do I fix it?

---

### Post by oldfred on 2014-04-30
All auto install and default in manual install is sda.
And I do not think RAID uses the MBR, so it did not damage your RAID. 
I do not know RAID, but many users install grub to a drive's MBR not the RAID and have boot issues.

You want to both install the grub boot loader to the same drive and its MBR. But you also want to update the remembered location on major update on which drive it will reinstall to. You can check which drive before and after the dpkg update.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by parish on 2014-04-30
Thank you very much - that's fixed it :D

---

