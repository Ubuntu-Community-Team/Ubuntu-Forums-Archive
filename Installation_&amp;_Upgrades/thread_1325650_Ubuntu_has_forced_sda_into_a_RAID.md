---
title: "Ubuntu has forced sda into a RAID"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by smudge12b on 2009-11-13
Last night my PC was working fine, I allowed some updates to be added but this morning when I switched it on I could not access my Windows partiton after accessing the Ubuntu partition. Fortunately the partition is backed up daily with Ghost so nothing much was lost.

I did a blkid and got this result;

dev/sda: TYPE="nvidia_raid_member"
/dev/sdb: TYPE="nvidia_raid_member"
/dev/mapper/nvidia_bjcedagc1: UUID="427a4888-dde0-4f51-8f4d-f8c1c414eed9" TYPE="ext4"
/dev/mapper/nvidia_bjcedagc6: UUID="acf62ee1-dd77-4990-afb9-06b23e999a58" TYPE="ext4"
/dev/sdc5: UUID="5E04774C047725E5" LABEL="Western Digital USB" TYPE="ntfs"

I was quite surprised as I had at no point instructed the system to use the disks as a RAID. Any ideas on how to turn them back into 2 seperate entities?

---

### Post by lemming465 on 2009-11-15
Did the updates happy to include going from 9.04 jaunty to 9.10 karmic?  Karmic's use of "dmraid" is much more aggressive than previous systems, and it's tending to pick up on false positive remnants of software "fakeraid" setups long dead, e.g. from OEM vendor windows installs.  Things that might help:
* turn off RAID in your BIOS, if it's on
* if you ever reinstall from scratch, from a live linux CD prior to installing any operating systems zero out the beginning of the disks with something like *for d in sda sdb; do sudo dd if=/dev/zero of=/dev/$d bs=64k count=1000; fi*  **WARNING!**  Zeroing out the start of the disks will wipe out the partition table, boot loader, and file system metadata, and some files, rendering the PC into a blank slate.  But it will get rid of any lingering software RAID configuration.
* you could try disabling mistaken software raid by booting a live CD, running *sudo apt-get remove dmraid* in a terminal window, and seeing if *fdisk -lu* shows your real disk partitions.  If so, mount your filesystems by hand, and then use chroot to repeat the dmraid removal.  E.g. if you have one root partition on sda1, something like```

sudo -i
apt-get remove dmraid
fdisk -l
mkdir /media/sda1
mount /dev/sda1 /media/sda1
cd /media/sda1
for m in dev proc sys; do mount -o bind /$m $m; done
chroot .
apt-get remove dmraid
```

---

### Post by smudge12b on 2009-11-17
Unfortunately I was forced into a complete reinstall of both Windows and XP but did as you suggested, zeroed both HDDs and removed DMRAID prior to install, everything seems ok now. I have read elsewhere that gparted will install DMRAID if you use that so that is something to be aware of.
 
I think the future for me lies with two seperate PCs networked together to prevent anything like this accidentally happening again.

---

### Post by presence1960 on 2009-11-17
I did this taken from another thread to which I lost the link. fortunately I saved the instructions to a file:

Also there is a bug in 9.10 that mounts raid arrays that you have deleted. To fix it first turn off raid in your bios.  Then load up the 9.10 live CD and open gparted.  If you get a drive with a funny name like nvidia_ahahdhjdfsjkf then you have mounted a raid drive that you don't want.

To get rid of it, Open a terminal and type ```
sudo dmraid -E -r /dev/name_of_your_disk
```.  Note you want the disk name not the partition name.  You can see your disk names in gparted.  Mine was sda and sdb and my partition names were sda1 and sda5 and sdb1.  I had to do both sda and sdb.

Once you have erased the raid meta data you should see the funny named disk disappear after restarting gparted.

Once you have verified the raid disk is gone reboot and your OS should boot.

---

### Post by darkod on 2009-11-17
@presence, was the data on the drives still there? I was trying to help someone with this problem and wish I knew this before. For things to be even stranger, he had only one drive and still marked as raid.
If he executes those commands will he have to reinstall everything?

---

### Post by presence1960 on 2009-11-17
> **darkod said:**
> @presence, was the data on the drives still there? I was trying to help someone with this problem and wish I knew this before. For things to be even stranger, he had only one drive and still marked as raid.
If he executes those commands will he have to reinstall everything?

Yes all data remained intact! I only had one disk marked as RAID also. I have 3 internal disks: 160 Gb IDE , 250 GB & 500 GB SATA. All are seagate. The 250 GB was marked as RAID

---

### Post by jcmoore on 2009-11-18
For everyone who experiences this problem here's some help on
recovering the Windows partition without a re-install.

[http://support.microsoft.com/kb/927392]("http://support.microsoft.com/kb/927392")

The included note was key for me.

[COLOR="Blue"]Note If rebuilding the BCD does not resolve the startup issue, you can export and delete the BCD, and then run this option again. By doing this, you make sure that the BCD is completely rebuilt. To do this, type the following commands at the Windows RE command prompt:

    * bcdedit /export C:\BCD_Backup
    * c:
    * cd boot
    * attrib bcd -s -h -r
    * ren c:\boot\bcd bcd.old
    * bootrec /RebuildBcd
[/COLOR]

Of course if you haven't created a recovery disk already (or have the install disk)
you're in the weeds...

A caveat worth mentioning...

This erases the grub bootstrap allowing you to boot Windows and I can tell from
using the Ubuntu recovery mode that the linux partitions are still intact if not
bootable. 

I needed the Windows partition ASAP and am now tracking the Ubuntu end for an appropiate
grub fix...

Thanks for the help!

---

### Post by smudge12b on 2009-11-19
> **presence1960 said:**
> I did this taken from another thread to which I lost the link. fortunately I saved the instructions to a file:

Also there is a bug in 9.10 that mounts raid arrays that you have deleted. To fix it first turn off raid in your bios.  Then load up the 9.10 live CD and open gparted.  If you get a drive with a funny name like nvidia_ahahdhjdfsjkf then you have mounted a raid drive that you don't want.

To get rid of it, Open a terminal and type ```
sudo dmraid -E -r /dev/name_of_your_disk
```.  Note you want the disk name not the partition name.  You can see your disk names in gparted.  Mine was sda and sdb and my partition names were sda1 and sda5 and sdb1.  I had to do both sda and sdb.

Once you have erased the raid meta data you should see the funny named disk disappear after restarting gparted.

Once you have verified the raid disk is gone reboot and your OS should boot.

This has solved another problem for me as well. When I've been trying to install other distros they have all failed or hung at the partitioning part of the install. That has gone now and I have Sabayon and Mandriva installed and running happily. :P

---

