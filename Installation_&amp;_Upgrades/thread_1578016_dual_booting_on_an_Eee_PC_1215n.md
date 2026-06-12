---
title: "dual booting on an Eee PC 1215n"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by gamelord12 on 2010-09-19
I got the Eee PC 1215n specifically because it was cheap, good on battery life, and came with Windows 7 Home Premium.  My old laptop, which recently died, had just Ubuntu on it, and I had few complaints.  However, there were those few times that I really wanted the ability to switch to Windows.

I'm running the Live ISO from USB, and I'm at the partition manager section of the install.  In the past, I remember there being an option where Ubuntu would specifically keep your old OS and settings intact, and you would just resize Ubuntu to the size that you needed it.  However, my only options right now are to either use the entire disc or partition it manually, which I'm not as comfortable with since I don't know if I'll be able to get this computer back to the way it was before without having a disc drive, an install disc for Windows 7, and a serial key.  The partition table reads as such:

/dev/sda1, Windows 7 (loader), 107.4 GB
/dev/sda2, Windows Vista (loader), 16.1 GB
/dev/sda3, [no label], 126.6 GB
/dev/sda4, [no label, but I assume this is the boot sector or something], 21.2 MB

I consider myself to be rather tech savvy (senior computer science major), but I can't exactly just dive in and re-partition my drive not knowing what anything is.  If I had to guess though, I'd assume that sda3 is the main storage partition, and that would be the one that I could resize, and then I could install Ubuntu on the 30 or so GB that I free up there.  Could I get some other input on this before I risk messing with my system?  I don't want to brick this little laptop, but Ubuntu is so much more energy efficient than Windows (not to mention running on a more organized infrastructure and interface) that I'd really like to get it installed.

---

### Post by Jupp3 on 2010-09-20
> **gamelord12 said:**
> I got the Eee PC 1215n specifically because it was cheap, good on battery life, and came with Windows 7 Home Premium.  My old laptop, which recently died, had just Ubuntu on it, and I had few complaints.  However, there were those few times that I really wanted the ability to switch to Windows.

I'm running the Live ISO from USB, and I'm at the partition manager section of the install.  In the past, I remember there being an option where Ubuntu would specifically keep your old OS and settings intact, and you would just resize Ubuntu to the size that you needed it.  However, my only options right now are to either use the entire disc or partition it manually, which I'm not as comfortable with since I don't know if I'll be able to get this computer back to the way it was before without having a disc drive, an install disc for Windows 7, and a serial key.  The partition table reads as such:

/dev/sda1, Windows 7 (loader), 107.4 GB
/dev/sda2, Windows Vista (loader), 16.1 GB
/dev/sda3, [no label], 126.6 GB
/dev/sda4, [no label, but I assume this is the boot sector or something], 21.2 MB

I consider myself to be rather tech savvy (senior computer science major), but I can't exactly just dive in and re-partition my drive not knowing what anything is.  If I had to guess though, I'd assume that sda3 is the main storage partition, and that would be the one that I could resize, and then I could install Ubuntu on the 30 or so GB that I free up there.  Could I get some other input on this before I risk messing with my system?  I don't want to brick this little laptop, but Ubuntu is so much more energy efficient than Windows (not to mention running on a more organized infrastructure and interface) that I'd really like to get it installed.
I have same laptop, and done similar operation. I think the second big partition (D: in windows) was completely empty (but don't trust me, boot to windows and see for yourself, or mount in ubuntu), but let's go back to how I did it, and how I would recommend to do it:
1)Backup your Windows 7 installation. You can do it to USB massstorage aswell, no need for external DVD burner. There are detailed instructions for that in the manual. If I remember correctly, you need to push some key when booting to get to the "backup mode".
2)From ubuntu installer, select "partition manually", delete the second big partition (which you previously confirmed empty), and add whatever partitions you need (probably at least root and swap, I usually add separate /home aswell, but that's in no way needed)
3)Install :-)

---

### Post by Mark Phelps on 2010-09-21
> ..In the past, I remember there being an option where Ubuntu would specifically keep your old OS and settings intact, and you would just resize Ubuntu to the size that you needed it...
With Win7, however, the game has changed.  Make sure you do NOT use the Ubuntu installer to resize your Win7 OS partition.  Doing so runs the risk of corrupting the partition and rendering Win7 unbootable.

> ...without having a disc drive, an install disc for Windows 7, and a serial key.  
You're saying you don't have a CD/DVD drive?  That's bad news because, ordinarily, the advice I would give is to use the Win7 Backup feature to create and burn a Win7 Repair CD -- to be used later to repair the Win7 Boot Loader should it become damaged during the dual-boot setup.  Don't know if you can use that same feature to create a Win7 Repair USB stick.

> If I had to guess though, I'd assume that sda3 is the main storage partition, and that would be the one that I could resize, and then I could install Ubuntu on the 30 or so GB that I free up there.  Could I get some other input on this before I risk messing with my system?  
OK ... look in your NTFS partitions for a (hidden?) boot directory and a bootmgr file.  Those are components of the WIn7 boot loader.  The partition that contains them is your Win7 boot partition.  You CAN remove this, but you have to move the Win7 boot loader files into the Win7 OS partition, otherwise, Win7 will not boot.

Then, look in your NTFS partitions for a Program Files directory.  That partition containing that is your Win7 OS partition.
> I don't want to brick this little laptop, but Ubuntu is so much more energy efficient than Windows ... 
Not MY experience.  I'm running Ubuntu and Win7 on a tablet PC, and Win7 is every bit as fast and energy efficient (in terms of CPU usage) as Ubuntu.

---

### Post by ch3rryc0ke on 2010-12-09
I have this same laptop, and ran into the same issue. This is what I did:

1. Boot into Windows first and run all the config stuff etc
2. Reboot, press F9 and go into Asus recovery mode
3. Create a recovery USB partition. I used an external drive because you need about 16Gb. This will save you in case you screw things up when installing Ubuntu.
4. Boot into windows, and delete the D:\ partition. You need to leave this as unpartitioned space.
5. Use the live USB to install Ubuntu
6. During installation select "partition manually" and create the partitions you need, install

This way you can dual boot properly, keep separate partitions, and you have a backup to restore your laptop to the factory state if necessary (turned out to be necessary for me-- I managed to delete the bootloader amongst other things).

---

### Post by booyootoo on 2011-01-12
Maybe it's too late, but here's my take on it.
ch3rryc0ke was right, just to clarify
>  
 
/dev/sda1, Windows 7 (loader), 107.4 GB
/dev/sda2, Windows Vista (loader), 16.1 GB
/dev/sda3, [no label], 126.6 GB
/dev/sda4, [no label, but I assume this is the boot sector or something], 21.2 MB
 
The "D" drive in Windows is /dev/sda3
I Guess the /dev/sda2 is the recovery partition, so don't touch that.
Also I guess that /dev/sda4 is the "quick boot" partition; It's the built in OS from ASUS where you can fast boot to when using the button left of the "wifi" button.
And obviously /dev/sda1, is the Windows 7 Disk, so also don't touch this one
 
You dont need to delete the D drive in Windows, you can also do this from your Ubuntu Installation (If I remember correctly).
 
You Need to remove the /dev/sda3/ drive and then create at least 2 drives/partitions (1 for Ubuntu and the other for Swap).
 
I myself created 3 partitions. 1GB, 20GB and the Other was what was left (around 99GB) 
I then used the 20 GB partition as my Ubuntu disk, the 1 GB partition as Swap and the 99 GB Drive as an "extra" partition, and formated it FAT32, so I could use it in from Windows and Ubuntu

---

### Post by Quackers on 2011-01-12
booyootoo, this thread is weeks old. I'm sure any problems the OP had are long gone :-)
But, just to clarify, the OP has 4 primary partitions on one hard drive. This is the maximum allowed in the MBR partitioning scheme. If he creates another partition before he deletes one, Windows 7 will change his partitions into dynamic disks. This is not good news! It may even necessitate re-installing everything!
The OP needs to delete a partition, then create an extended partition, inside which he can have as many logical partitions as he wants.

---

### Post by Quackers on 2011-01-12
Double post - again!

---

