---
title: "I'm starting a clean slate."
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by XtremeGamer99 on 2005-10-03
Thanks to a few people, I managed to copy all my important files from my busted Windows/Ubuntu Hard Drive (the boot never finished installation, rendering it impossible to boot into either one). Now that I have all my important file on my secondary 20 GB HDD, which has a working Ubuntu on it, I would like to start clean on my 120 GB HDD. However, I've never had a dual-boot system. I've never worked with partitions. I don't know how to install Ubuntu on one partition, and Windows on another.

So, I've come to ask. I remember when installing Ubuntu, it asked about partitions and what to do with them and what-not. Never really payed close attention to it. However, I do not remember Windows ever mentioning it on the XP Pro setup. So, I need to know how I can have Ubuntu on a 40 GB partition, and my Windows XP Pro on the remaining space. If I can get step-by-step instructions, that would be great and I will love you for life. =)

Anyway, since I remember Windows setup not saying anything about partitions, I need to know what OS I need to set up first. Can anyone help?

---

### Post by bhagabhi on 2005-10-03
Install Windows first.
Though make room after the windows-partition so you will have space for Ubuntu.

Then Ubuntu - who will ask if it should install grub at the end of its installation - it will say what OS's it finds - and if it finds Windows there should be no problem writing the Grub - thus making it possible to boot either OS.

Theres an option in the Ubuntu installation to "install in biggest free space" or something like that.

Has worked for me every time - I don't think there is more to it.

[EDIT]
If you install Windows _after_ the Ubuntu it will most certainly remove the boot-sector - thus making the Ubuntu unreachable.
[/EDIT]

---

### Post by XtremeGamer99 on 2005-10-03
I've already run into problems. I installed Windows XP Pro, then tried to install Ubuntu. However, it said that it was to erase all data on Partition #1, which is 116 GB, and use Partition #5 as swap with 4 GB. I thought Windows was on Partition #1, but I decided to go on ahead, because I had done it before and it kept my Windows and the files even though it siad to erase them all. Well, now nothing works. My Ubuntu froze when installing Grub.

Should I try it again? Or am I doing something wrong?

---

### Post by XtremeGamer99 on 2005-10-03
Anyone?

---

### Post by SilentCacophony on 2005-10-03
Hello. It looks as if you let winXP take the entire drive, which is not what you want. As painful as this probably is for you right now, what you need to do is learn how to partition your drive. There are many ways you can do this.

I'll have to add a disclaimer here: I have never installed Windows XP, and I've only ever used 2 different partitioners (fdisk and ranish partition manager, both dos.) That said, I can give you some general info, and how I'd deal with it given my experience.

What I find to be the best way to partition is to have a rescue disc/disk with the basic tools, and do it before starting an installation. Personally, I've used a simple bootable dos floppy disk with scandisk, fdisk, format, and part244 ([Ranish Partition Manager]("http://www.ranish.com/part/").) I have used that for years for partitioning, but it is an old dos tool, which some might find off-putting. Another, probably better option would be [SystemRescueCD]("http://www.sysresccd.org/index.en.php"), which has a lot of linux tools, including QTParted. Explaining these  tools is beyond the scope of a forum post, so the manuals and Google are your friends there. Starting fresh is a good time to experiment and learn.

Then decide how you want to split the drive up. Generally, you'll want Windows on the first partition of the first harddrive, and you'll need the partition to be formatted either FAT32 or NTFS so that Windows recognises it as a partition. It's a good Idea to make another partition to store data for access by windows as well as linux (for music, etc...) You'll want this to be FAT32, so both OSes can work with it. A partition for linux formatted as ext3 and one swap partition would finish it. So, you could setup like so:

Windows XP (NTFS)
Linux (ext3)
Swap (swap)
Storage (FAT32)

The amounts would depend on your preference, and how many software packages you may install on either. I would probably set about 20GB for Windows, 10GB for Ubuntu, 1.5 * (you ram amount) for swap, and the rest for storage. You can use the Storage partition for large data files and such.

Partition and format them as above using your chosen tool. If the partitioner won't do NTFS, then format the XP partition using FAT32 for now.

Install Windows XP, and have it reformat the first partition as NTFS if necessary. It's easier to do this first, so that when Windows wipes out the MBR of the drive, it won't be wiping out grub, which will be installed with Ubuntu.

Install Ubuntu, choosing the 'manually edit partition tables' option when it gets to the partition setup. Select the Linux partition, set the mount point as /, make it bootable, and select ext3 filesystem if not already. If the swap partition was already formatted as swap, then ubuntu will likely select it as swap automatically. If not, then do that manualy. Then you'd scroll down and select the finished option, at which point it'll ask you to verify the changes, and you're off. When it gets to the grub installation, it should detect both OSes, and ask you to verify that. At that point, install grub to the MBR, and finish the installation.

The storage partition can be mounted later from Ubuntu as outlined in the ubuntuguide.

Just for a different perspective, I make do with a 20 & 10 GB drive setup like so:

```
Disk /dev/hda: 20.4 GB, 20493656064 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2         312     2498107+   b  W95 FAT32 <- Windows 98
/dev/hda2             313         697     3092512+  83  Linux <- Linux Distro of the Week
/dev/hda3             698        1338     5148832+  83  Linux <- Ubuntu
/dev/hda4            1339        2491     9261472+   f  W95 Ext'd (LBA)
/dev/hda5            1339        1851     4120641   83  Linux <- Linux Storage
/dev/hda6            1852        2364     4120641   83  Linux <- Linux Backup
/dev/hda7            2365        2491     1020096   82  Linux swap / Solaris

Disk /dev/hdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1247    10016496    c  W95 FAT32 (LBA) <- Shared Storage

```

Good luck.

---

### Post by eXcentra on 2005-10-03
[QUOTE=XtremeGamer99]Thanks to a few people, I managed to copy all my important files from my busted Windows/Ubuntu Hard Drive.[/QUOTE]
Would you mind telling me how you retrieved the files from your Windows partition? I can't boot back into Windows and I need some files from it...
:)

---

### Post by XtremeGamer99 on 2005-10-05
Thanks SilentCacophony

You have to do a mount. Here how I found out: [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

