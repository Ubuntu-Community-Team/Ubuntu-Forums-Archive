---
title: "Help, can't install 10.10 as a dual-boot??"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by valmiki9 on 2010-12-02
Hi,

I have a 2 year old Sony Vaio running Vista Home Premium.

I downloaded Ubuntu 10.10 onto a USB stick, and I'm trying to install it alongside Vista.

Boots OK into the installer, etc. but I never get the option to install ubuntu side-by-side with Vista? I've tried defragging the hard-drive, and also tried installing via CD-ISO but the option never appears. I've also checked and there are no other partitions on the drive, just the C: (and also the 'hidden partition' used to re-install back to factory image).

I've tried searching everywhere, but the search words understandably only brings up results that walk you through the install, not the problem I have.

I'm not keen on plowing through info on setting up my own partitions, etc. I was hoping that this would all be easier than that! 

Is this a bug or an issue?

Any help would be appreciated, thanks
valmiki

---

### Post by wayne128 on 2010-12-02
Lets take a close look at the hard disk partition.
Use your Live CD and boot up the computer, then on terminal, type sudo fdisk -l <enter> then post the results.

---

### Post by Quackers on 2010-12-02
Is there any free space on the hard drive? Or does the recovery and the C: partition take up all of it? If so, you will need to reduce the size of the C: partition to leave space for Ubuntu to install in.

---

### Post by matt_symes on 2010-12-02
Hi

+1 quackers. Use the vista tools to shrink the partition to create some space. You might want to consider a separate partition for your home directory as well.

Kind regards

---

### Post by Sef on 2010-12-02
> Use the vista tools to shrink the partition to create some space.

With Vista and Windows 7, use MS partitioning tool. If you use another partitioning tool, you would most likely need to reinstall Windows.

---

### Post by matt_symes on 2010-12-02
Hi

> **Sef said:**
> With Vista and Windows 7, use MS partitioning tool. If you use another partitioning tool, you would most likely need to reinstall Windows.

Yes. Learnt that the hard way ;)

Kind regards

---

### Post by kansasnoob on 2010-12-02
> **valmiki9 said:**
> Hi,

I have a 2 year old Sony Vaio running Vista Home Premium.

I downloaded Ubuntu 10.10 onto a USB stick, and I'm trying to install it alongside Vista.

Boots OK into the installer, etc. but I never get the option to install ubuntu side-by-side with Vista? I've tried defragging the hard-drive, and also tried installing via CD-ISO but the option never appears. I've also checked and there are no other partitions on the drive, just the C: (and also the 'hidden partition' used to re-install back to factory image).

I've tried searching everywhere, but the search words understandably only brings up results that walk you through the install, not the problem I have.

I'm not keen on plowing through info on setting up my own partitions, etc. I was hoping that this would all be easier than that! 

**[COLOR="Red"]Is this a bug or an issue?[/COLOR]**

Any help would be appreciated, thanks
valmiki

Well the Live Installer (aka: ubiquity) got a complete redo in 10.10. Some of the info here may be helpful:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Be sure to check out post #15:

[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)

So, there are bugs besides it creating new issues. I also suspect that parted may have a bug but I've not been able to reproduce it on my machine.

In order for us to help you please boot the Live CD/USB and choose Try Ubuntu instead of Install, then from the Live Desktop open the Terminal and post the output of these commands:

```
sudo fdisk -l
```

```
sudo parted /dev/sda print
```

Then we can try to make some recommendations.

---

### Post by valmiki9 on 2010-12-02
Hi, thanks for the replies.

I should have mentioned that I had tried partitioning (in Vista), so that I had 50GB unallocated space on the drive, but that didn't work either.

Anyhow, here goes.

sudo fdisk-l :


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a62ec17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1337    10732544   27  Unknown
/dev/sda2   *        1337       24028   182263900    7  HPFS/NTFS

Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984      991747+   6  FAT16

Disk /dev/sdb: 2032 MB, 2032664576 bytes
41 heads, 40 sectors/track, 2420 cylinders
Units = cylinders of 1640 * 512 = 839680 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2421     1984992+   b  W95 FAT32



sudo parted /dev/sda print :


Model: ATA Hitachi HTS54252 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

hope this helps!

thanks again
valmiki

---

### Post by valmiki9 on 2010-12-03
Guys, can anyone help, or should I just wait until 11.04 :(

---

### Post by Quackers on 2010-12-03
If you are presently booted into Windows Vista please post a screenshot of your Disk Management Console (Start > right-click Computer > select Manage > then select Disk Management)

---

### Post by valmiki9 on 2010-12-03
Here goes:

---

### Post by oldfred on 2010-12-03
Are you or have you run RAID or turned RAID on in BIOS.

/dev/mmcblk0
You do not normally have a dev like the above unless you have some form or RAID or LVM logical volume manager.

If it had RAID and does not the drive still has meta-data that interfers with the install.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by Quackers on 2010-12-03
That looks ok to me. 
If you boot from the live cd and choose Install and then proceed to the partitioning section you should choose the manual option (may be called "specify").
When the partitioning screen has scanned your hard drive you will see sda1, sda2 etc and then "unallocated space". Double click on the unallocated space and a pop up will appear. Don't select Primary as partition type, select the other one (can't remember what it is) then select ext4 as the file system and check the box to format it then choose "/" as the mount point and away you go :-)

Edit after following oldfred's advice :-)

---

### Post by kansasnoob on 2010-12-03
Sorry, I'm a cranky old man :(

Your fdisk -l output shows:

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a62ec17

Device Boot Start End Blocks Id System
/dev/sda1 1 1337 10732544 27 Unknown
/dev/sda2 * 1337 24028 182263900 7 HPFS/NTFS

Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/mmcblk0p1 1 984 991747+ 6 FAT16

Disk /dev/sdb: 2032 MB, 2032664576 bytes
41 heads, 40 sectors/track, 2420 cylinders
Units = cylinders of 1640 * 512 = 839680 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 2421 1984992+ b W95 FAT32


BTW that would be much easier to read if you used code tags, but regardless you cut off the parted output:

> sudo parted /dev/sda print :


Model: ATA Hitachi HTS54252 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


You cut off the part about the partitions! But it doesn't matter.

I can't be absolutely certain which is which but you show two external drives:

> Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes

And:

> Disk /dev/sdb: 2032 MB, 2032664576 bytes

I'd guess the first one is some data card that was mistakenly left in :confused:

Check for a memory card that was left in, then look at what I've been working on here very closely if you're installing 10.10:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by jplo on 2010-12-03
If you're really stuck, try installing Lucid (Version 10.04) instead, as it is a LTS (Long Term Support) release. You will then be able to upgrade to Version 10.10 using update-manger (if you have a fair internet speed)

ALTERNATE INSTALLER CD
 or by using the alternate install CD, available from [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate) , then from the page that appears choose 'Ubuntu 10.10 (Maverick Meerkat)' then scroll down until you see '[PC (Intel x86) alternate install CD' (this is also a link to the same file) ]("http://ubuntu.virginmedia.com/releases//lucid/ubuntu-10.04.1-alternate-i386.iso")Then follow the instructions at [The Ubuntu Documentation]("https://help.ubuntu.com/community/MaverickUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD") to upgrade.


Hope this helps - even as a backup plan

---

### Post by valmiki9 on 2010-12-03
Guys, this looks very complicated - I think I'm going to go with gerbilschool's suggestion and download 10.04, hopefully this should go better!

I'll be back 8)

thanks again everyone

---

### Post by valmiki9 on 2010-12-03
...and I'm here, installed 10.04, no issues at all during install ;-)

---

### Post by jplo on 2010-12-03
> **valmiki9 said:**
> ...and I'm here, installed 10.04, no issues at all during install ;-)

Now just see if you can Upgrade. Start by going to Update Manage (System > administration > Update Manager) **Do not upgrade immediately.** First you must click on 'check' and when the check is complete, you must install any updates by clicking Install Updates. This process will take a long time.

When this is complete, you may be prompted to restart your computer, if you are you must restart. If you are not, just click the **upgrade** button (top-right) and your upgrade will begin. **Upgrades can take between 1 and 6 hours (**the speed depends on your internet connection**). Occasionally a Dialogue Box will appear, the setup will not continue until you have completed the dialogue box.**

Hope this helps:KS

---

