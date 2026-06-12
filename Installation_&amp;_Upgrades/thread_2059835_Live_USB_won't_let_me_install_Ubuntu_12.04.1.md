---
title: "Live USB won't let me install Ubuntu 12.04.1"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by gonzobilbao on 2012-09-18
Hi eveyone

I got a new laptop some days ago , an HP envy 4 1050. It came with the typical preloaded windows system, and since I had used some linux distributions before I tried to install it on this. I have tried two distributions- first Linux Mint (Ubuntu-based as many of you know) and some Ubuntu 12.04 flavors, including amd64 and the recommended 32-bit version. All of them gave the correct md5 sum and all of them were tried from an USB drive. The problem was that that no installation option showed up on the initial screen , when trying the live version (those in where you are asked if you want the full installation, the guided partition or the manual partition). Instead only a partition table appears; but it doesn't allow me to do anything on it. In conclusion, no installation is possible. I thought that creating a Ext3 partition for it would solve the problem, but it happens exactly the same thing.
So instead of getting this:


[IMG]http://www.ubuntu.com/sites/www.ubuntu.com/files/active/02_ubuntu/desktop-install-1.png[/IMG]
[IMG]http://www.ubuntu.com/sites/www.ubuntu.com/files/active/02_ubuntu/desktop-install-3.png[/IMG]

I get this and an empty partition table 
[IMG]http://www.muktware.com/sites/default/files/images/manual/ubuntu1110/02-install-language-selection.jpeg[/IMG]

Can anybody help? Thanks!!!!):P

---

### Post by jerrrys on 2012-09-19
Sure you want to erase windows?

Anyhow you don't create an ext3 partition, you just create free space.  Then the installer should see the free space and ask you if ubuntu should be installed there.

Also on a side note, ext3 has been replaced with ext4 in 12o4 :)

---

### Post by darkod on 2012-09-19
Most HP laptops come with all 4 primary partitions used. So even if you create unallocated space, you can't create 5th partition. And make sure you don't try that from windows because it will turn the disk into Dynamic.

So, you can delete either the HP_TOOLS or the Recovery partition. You can create recovery DVDs using the software on the laptop, and keep them in case you ever want to do factory restore. After that you can delete the recovery partition which will also give you few GBs more space.

You will also need to shrink the C: partition depending how much space you want for ubuntu. Do this in win7 Disk Management (NOT with the ubuntu installer). Restart windows few times in case it wants to do few disk checks.

After you have done that, you should have bunch of unallocated space on the disk and only 3 primary partitions. You can install ubuntu either with the auto method or manually for better control. If manually, make sure you create the partitions as logical.

That's it.

---

### Post by gonzobilbao on 2012-09-19
Thanks guys!!But I did the partition that way, but the problem persisted. Ive been researching on this, starting to think that Ubiquity is not recognizing my Win7 partition...

---

### Post by darkod on 2012-09-19
Did you check in windows if the disk is already Dynamic maybe?

Sometimes if there is partition table corruption it can't detect other OSs so it will offer to wipe and use the whole disk.

Can you boot the cd in live mode and post the output of:
sudo fdisk -l (small L)

---

### Post by gonzobilbao on 2012-09-20
Thanks Darko, I dont know exactly what you mean with the Dynamic disc. The output of the command was
[FONT=Lucida Sans Unicode][SIZE=2]
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc7f55fd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   410010929   204800665    7  HPFS/NTFS/exFAT
/dev/sda3       410010930   410235839      112455    c  W95 FAT32 (LBA)
Partition 3 does not start on physical sector boundary.

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd5789ef3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    16775167     8386560   84  OS/2 hidden C: drive

Disk /dev/sdc: 3869 MB, 3869245440 bytes
120 heads, 62 sectors/track, 1015 cylinders, total 7557120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e358

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62     7551599     3775769    b  W95 FAT32


[/SIZE][/FONT]

---

### Post by darkod on 2012-09-20
You seem to have the hybrid disk, combination of hdd and ssd. See:
/dev/sda of 500GB and /dev/sdb of 32GB.

In windows they are combined with something called Intel SRT.

From what people have posted here, the only way to install is to "break" the ISRT setup. For that, you need to disable Intel SRT in windows, go into BIOS and change the SATA mode to AHCI, then remove any remainings of meta data on the disks with:
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

You can run that from live mode.

After that you can use the disks as separate. You can install uubntu on the 500GB disk after you make space for it, or even better install it on the faster ssd.

Here is a recent thread of someone who did the same:
[http://ubuntuforums.org/showthread.php?t=2060108](http://ubuntuforums.org/showthread.php?t=2060108)

It's up to you if you want to do it or not.

---

### Post by gonzobilbao on 2012-09-22
thanks for your help Darko, I've seen that there is an option in BIOS to disable the iRST, instead of doing it via Win GUI, is that the same?

---

### Post by darkod on 2012-09-22
I am not sure about that, I have never used IRST so far. It might be better to disable it in windows first, and then in BIOS because if you disable it in BIOS now windows might complain and look for it expecting to find it.

---

### Post by gonzobilbao on 2012-09-24
Ok, so far it happens as follows

-I do not have the option to change the SATA mode in BIOS to AHCI- i'm trying to figure out if my laptop is preconfigured by default to AHCI, but so far I do not know how to check that out. i've read that you can change that via win7 GUI using RegEdit. I've done that, but not sure if it will work... any ideas?updating/ rolling back BIOS maybe? I remember that my old HP 6730s used to have this ooption in BIOS.

-I cannot reach any "Intel Rapid Start Tech Manager" in my Win 7, i've been researching on this, it looks that some other users can access it with no problems just typing that on the search bar- not my case. So i've done it via BIOS.

-My ssd drive appears to have into it something called the "Hybernation partition", should I delete it before going ahead with the commands for removing RAID metadata? Should I create an extended partition to instal the / directory there?

Cheers):P

---

### Post by darkod on 2012-09-24
If you are installing only ubuntu on the ssd there is no need to create the extended (logical) partition as first. You can have three primary partition before you need to start creating logical ones, so that's fine.

If the hybernation file is on the ssd, first disable the function in windows and then delete it.

You can't really change AHCI mode in windows registry. I guess what you read was tutorial what to change in the registry if you switch the sata mode after windows is installed.

As for your laptop having the AHCI option in BIOS or not, can't help you there.

---

### Post by gonzobilbao on 2012-09-25
I've been researching on this in the last days. It happens that my laptop is preset to AHCI, no possibility to change that in BIOS at least. Does it make sense to run those commands to remove RAID metadata if apparently the laptop cannot be set to RAID? Should I still run those commands?

Anyways, there was a iSRT going on and I disabled it

Cheers):P

---

### Post by darkod on 2012-09-25
I am not sure if IRST itself is configured as sort of raid. In any case there is no damage running the commands since if there is no meta data present it will simply tell you that.

On the other hand, if it asks you to confirm you want to remove the meta data, that means it found it, and simply confirm to remove it.

---

### Post by BrianBlaze on 2012-09-25
I know this is npot really a solution but I had the same problem (almost) with my PC. I would try to install ubuntu and it would just see my whole drive and not my partitions so if I was to install ubuntu I would have had to remove windows... My only solution... Install Fedora which recognized everything properlly lol

---

### Post by gonzobilbao on 2012-09-29
Well, problem solved!!! After removing RAID metadata on sdb everything went smooth, thanks!! After that ubiquity recognized perfectly the partitions and so i started the installation. Anyways I installed everything on sda ( I was expecting ubiquity to offer me whether I wanted to install boot files on sda or sdb, but that didn't happened and I couldn't hit back) so I will try to do that. Can I migrate the boot files/partitions to my sdb? Should I delete ubuntu's partition from windows and start over?


Cheers!!

---

