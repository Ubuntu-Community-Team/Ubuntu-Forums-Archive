---
title: "cant create new partition / unusable space"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by Muminboll on 2010-01-19
Hello! Im running a dell studio xps 16 computer with windows 7. Im now trying to install a dual boot with ubuntu. 

My problem is that ubuntu refuses to create a new partition, claiming that i already have 4 main partitions. According to any partitionprogram run in windows I only got 3.

It looks likt this in Gparted (from live cd):

dev/sda1 | fat16 | system reserved | size: 40 MiB
dev/sda2 | ntfs | size: 797.5 KiB
dev/sda3 | ntsf | size: 100 MiB
dev/sda4 | ntsf | 87.56 GiB

The 40 mb partition is probably for some dell recovery stuff.
The 100 mb partition is some windows 7 backup, it is also flagged as "boot"..
The 87 gb partition is my main windows 7 disk.
I have no clue what the 797.5 KiB is for. It dosnt show up anywhere when looking at partitions in windows. I also tried deleting it from ubuntu (live cd) and then booting windows again, and when I booted ubuntu again it was there even tho i deleted it last time. 

What the hell is this? Can I just delete it and move on with installing ubuntu? Or should I instead delete the fat16 system reserved partition?

---

### Post by darkod on 2010-01-19
Gparted is right, you do have 4 partitions.
When you deleted /dev/sda2, did you make sure you executed the commands. If you did it with Gparted, the delete command is only scheduled, after that when you are sure you want to execute what you did in Gparted, you need to click the big green tick mark button in the Gparted toolbar. Otherwise if you just exit Gparted your scheduled command remains unexecuted.
Try again and make sure you delete that partition. After that you should have no problems installing Ubuntu.

On another note, this is why I hate win7 creating that 100MB useless partition. If you have single hdd and plan to dual boot, with all sorts of utility/restore partitions present today, the 100MB partition is a waste of one partition. You can avoid this by using ubuntu cd in live mode and using Gparted to create ntfs partition with the size you want for win7 system partition. After that you just tell the win7 installer to use the existing partition and in this case it doesn't create the 100MB partition. It only creates it if using the win7 installer partitioning tool.
You can always use Gparted instead even if you don't plan to install ubuntu at all.

PS. Personally. I don't think even /dev/sda1 has any significant use, but I can't know for sure. :)

---

### Post by Muminboll on 2010-01-19
So you think I should just start all over and begin with installing ubuntu, and then windows 7 after creating the nessesary partitions? I guess that will work, but its a lot of extra work since I then have to do a lot of backups to some external disk. Its probably the safest way tho i guess :)

Anyone else knows if its safe to delete any of the 3 backup/recovery/diagnotics partitions?

When i tried deleting the micro-partition I did so from the partitioner from the install menu of ubuntu, then I quit the installation.

---

### Post by Muminboll on 2010-01-19
Another thing, when in windows I can create another partition if I want, since it only says its 3 partitions. But not in ubuntu...

I think this is ubuntus fault.

---

### Post by darkod on 2010-01-20
> **Muminboll said:**
> So you think I should just start all over and begin with installing ubuntu, and then windows 7 after creating the nessesary partitions? I guess that will work, but its a lot of extra work since I then have to do a lot of backups to some external disk. Its probably the safest way tho i guess :)

Anyone else knows if its safe to delete any of the 3 backup/recovery/diagnotics partitions?

When i tried deleting the micro-partition I did so from the partitioner from the install menu of ubuntu, then I quit the installation.

No, I didn't say to start all over. And it's better windows to be installed before ubuntu. But for next time, create the windows system partition with ubuntu livecd instaed of win7 installer.
You are wrong, even though windows shows 3 partition in computer the 4th still exists and that's a limitation of the HDD, not ubuntu. Windows would not be able to create another partition too.

Boot with ubuntu cd again, Try Ubuntu option, open Gparted and delete the small micro partition as you call it, /dev/sda2. Then make sure you click the big green tick mark button in Gparted to execute the command. After that it will rescan the hdd and it should show you just the 3 partitions.

Then you can just reboot with ubuntu cd again, select Install Ubuntu and continue from there.

---

### Post by Muminboll on 2010-01-20
Ok, I tried that. Now both ubuntu and windows says its 3 partitions.

Now this happens: I created a new partition for installing ubuntu. Just to make sure windows was still working I rebooted the computer with the ubuntu partition empty. Now windows wont boot! It produces a bluescreen and the computer just reboots in an instant.

So I booted with the live cd again, and removed the partition made for ubuntu. Now windows can boot again! Is this weird?

Also, I can make an extended partition with both an ext2 partition for ubuntu and an ntfs partition for files, right?

Oh, and thnx for the answers darkod :)

---

### Post by presence1960 on 2010-01-20
> **Muminboll said:**
> Hello! Im running a dell studio xps 16 computer with windows 7. Im now trying to install a dual boot with ubuntu. 

My problem is that ubuntu refuses to create a new partition, claiming that i already have 4 main partitions. According to any partitionprogram run in windows I only got 3.

It looks likt this in Gparted (from live cd):

dev/sda1 | fat16 | system reserved | size: 40 MiB
dev/sda2 | ntfs | size: 797.5 KiB
dev/sda3 | ntsf | size: 100 MiB
dev/sda4 | ntsf | 87.56 GiB

The 40 mb partition is probably for some dell recovery stuff.
The 100 mb partition is some windows 7 backup, it is also flagged as "boot"..
The 87 gb partition is my main windows 7 disk.
I have no clue what the 797.5 KiB is for. It dosnt show up anywhere when looking at partitions in windows. I also tried deleting it from ubuntu (live cd) and then booting windows again, and when I booted ubuntu again it was there even tho i deleted it last time. 

What the hell is this? Can I just delete it and move on with installing ubuntu? Or should I instead delete the fat16 system reserved partition?

We need to see exactly what each partition is, as one of those either the 40MB or 100 MB is a windows 7 boot partition- most likely system reserved. But to be sure it would be nice to see your setup info. Do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

This info will clarify with no doubt what each partition is.

---

### Post by darkod on 2010-01-20
> **Muminboll said:**
> Ok, I tried that. Now both ubuntu and windows says its 3 partitions.

Now this happens: I created a new partition for installing ubuntu. Just to make sure windows was still working I rebooted the computer with the ubuntu partition empty. Now windows wont boot! It produces a bluescreen and the computer just reboots in an instant.

So I booted with the live cd again, and removed the partition made for ubuntu. Now windows can boot again! Is this weird?

Also, I can make an extended partition with both an ext2 partition for ubuntu and an ntfs partition for files, right?

Oh, and thnx for the answers darkod :)

I wouldn't create partitions in advance unless you have experience with that. And one thing we didn't mention so far is where are you planning to install ubuntu. I thought you had unallocated space but having 4 partitions was preventing you from creating ubuntu partition in that unallocated space. Otherwise, if all your hdd is allocated to partitions, you need unallocated space for ubuntu.

It might be a good idea to post a screenshot of Gparted too. You can take screenshots in Applications-Accessories. Just don't forget to set a delay of 3sec for example, so that the Take Screenshot window is gone and only Gparted is shown in the shot.

You can attach it here for better review how is your hdd partitioned right now.

---

### Post by Muminboll on 2010-01-20
============================ Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 81920. But according to the info from fdisk, 
                       sda1 starts at sector 63. According to the info in the 
                       boot sector, sda1 has 204799 sectors, but according to 
                       the info from fdisk, it has 80262 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7c83ef96

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda3    *         81,920       286,719       204,800  42 SFS
/dev/sda4             286,720   204,881,919   204,595,200  42 SFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="663618A036187373" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="68643D08643CDA90" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory


Here is the result.txt!

---

### Post by Muminboll on 2010-01-20
[IMG]file:///home/ubuntu/Desktop/Screenshot.png[/IMG][ATTACH]144242[/ATTACH]

and here is a screen of Gparted.


Also, I am experience with computers normally, I've had dual boots on my 2 last computers but I never had those problems before! Also, I'm not experience when it comes to linux.

My plan is this: One partition for Windows, one for Ubuntu and one for files. Nothing more fance than that! Have always worked in the past.

So now I got 2 options basically: 

Keep the windows partition, meaning I have to keep both the boot partition and the files partition. If im also gonna keep the OEM partition, then I need to do an extended partition, one with ext2/3 and one with ntfs, install ubuntu on one and have the other one for files. I could also maybe remove the OEM partition and do 1 primary for ubuntu and 1 primary for files. My problem here is that If i create an partition right now, windows wont boot! And this is where Im stuck at the moment.

The other option is to just format the entire disk, create 1 primary for windows, 1 for ubuntu and 1 for fiiles. Do this with the live cd, then install windows on a premade partition, making it so that it wont create the 100 MB boot partition. Then install ubuntu after that.


Dose that sounds about right?

---

### Post by oldfred on 2010-01-20
The extended partition should be the rest of your drive, if you are going to partition in advance. You then add logical partitions for NTFS data, ubuntu, swap and if you want /home. Swap should be about 2GB or your RAM size if you want to hibernate. Root (/) can be 10-20GB if you have a separate /home. The rest is all for data (including /home as data).

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Muminboll on 2010-01-20
Ok thnx, Ill do that!

Still tho, do you guys think ill have to reinstall windows for this to work? Since it refuses to boot when i create a new partition.

---

### Post by darkod on 2010-01-20
> **Muminboll said:**
> Ok thnx, Ill do that!

Still tho, do you guys think ill have to reinstall windows for this to work? Since it refuses to boot when i create a new partition.

Looking at your results file, it might be better idea to reinstall win7 too. At the top of the results you can see you have the boot files /botmgr and /boot/BCD in /dev/sda1, and not in /dev/sda3 where I would expect them to be. Now, the files in /dev/sda1 might be from some recovery partition but that is not recovery partition, only small utility partition.

On the other hand, the script returns unknown filesystem for /dev/sda3 and /dev/sda4, and fdisk says SFS. I've never used SFS, what is that? Did you use it on purpose instead of ntfs?

If you don't mind redoing everything, and if the Dell utility partition is old since it looks like you don't need it for your win7, I would use ubuntu cd and Gparted to delete all partitions (backup your win7 data first). Then create in Gparted just one ntfs partition with the size you want for the win7 system partition.

Then boot with win7 dvd and install it on that partition. It will not create the 100MB partition so at that moment you will have only one single partition used out of the maximum four.

Then you can decide and create another ntfs partition to be shared between win7 and ubuntu, and it can be primary too.

After that install ubuntu into extended partition, either by the default procedure (Use Largest Available Free space) or by creating ubuntu partitions manually during the install process.

And you will still have option to create one more partition later (fourth) if you need to.

---

### Post by Muminboll on 2010-01-20
Sound like a perfect plan! Im gonna do just that, my win7 install is pretty new anyways, not a lot of settings to lose.

Thnx for the help everyone!

---

### Post by Muminboll on 2010-01-20
Figured I'd tell how things went for me, since you guys probably wanna know and for anyone else having the same problem in the future.

Booted with the live cd, deleted all partitions and created a new partition for windows. 

Rebooted and installed windows.

Booted with the live cd again and created a big ntfs partition for data, and an ext4 partition for ubuntu and a swap partition.

Everything seems to work perfectly so far!

---

### Post by akhilesh_linux on 2011-06-17
Love you guys.... ( take it metaphorically :) ) I am also facing the same problem. Probably after reading all this, I should be fine now with my setup.

---

