---
title: "Can't mount drives after upgrade"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by KarmicFan on 2011-03-10
I have an interesting - but extremely frustrating dilemma and I need some help...

Somehow, a few days a go I got Samba messed up and I decided to just reinstall Ubuntu.  Ubuntu resides on an 80GB drive and I have 2 1.0 TB drives that I use for storage.  At one time (pre-Ubuntu) they were connected to a VIA SATA RAID card and I had them on a software RAID under Windows XP.  Both worked absolutely fine under Ubuntu 10.04 (which had bee progressively upgraded from the original install of 9.04.

Now, both drives have been given the same label, and neither one will mount because the file system type is reported as "via_raid_array" rather than the EXT4 that they both should be.  TestDisk can read them and identifies the partition as a Linux partition, and the data seems to be there.  I have even reformatted one of them and still, it will not mount.

Does any one have any ideas?  I would really like to keep the data on them if possible.

---

### Post by NJPinator on 2011-03-10
Maybe try this and see if Ubuntu is aware of your RAID array actually containing media:
```
sudo fdisk -l
```
Note that I'm kind of a newbie to RAID stuff, so I might not be quite right. However, it's the first thing I'd try, just to see if they're there.

If they are, remember the device name (e.g. /dev/sda4) and mount it manually via Terminal using the *mount* command.

To do this, first create a directory for mounting on...
```
sudo mkdir /mnt/raid-disk
```
Then mount the drive, substituting */dev/sda4* for your drive's device identifier:
```
sudo mount /dev/sda4 /mnt/raid-disk
```
You could now open Nuatilus File Manager if all went well to view your files!
```
nautilus /mnt/raid-disk/
```

P.S. Like I mentioned earlier, the situation is vague to me, seeing as it's a RAID array. Although you mentioned using a VIA Technologies driver or something...try visiting [VIA's driver download page]("http://via.com.tw/en/support/drivers.jsp") and find a Linux driver, if any. Maybe that'll solve it.

---

### Post by KarmicFan on 2011-03-10
I'll try that, thanks!  Unfortunately, I have to reinstall Ubuntu to get the chance.  When the PC reboots after coming up the first time after installation, it is unable to mount either of those two volumes, so it kind of kills any chance of booting.  I'll try the fdisk option and let you know how it goes...

---

### Post by NJPinator on 2011-03-26
It's been two weeks, has the situation cleared up yet? If all is good, be sure to mark this thread as "Solved"!!! This makes it easier for others to get information and sort of prevents 'spam' from people who post, thinking they're helping you, when actually the issue has been resolved already.

---

