---
title: "Missing operating system"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by apple pie maker on 2012-12-27
The Problem: After reinstalling 10.04.4 side-by-side with 12.04, startup options show 12.04 and Windows XP, but not 10.04.4.

Background:

Equipment: 
HP desktop Pavilion Model a1210n
Two Hard Drives - The original 160 Gb HD contains Windows XP. Ubuntu has been housed on the second HD of 300Gb. 

History:
I have been using this setup for years with XP on one hard drive and Ubuntu on the other hard drive and had no problems. During startup, bios gave me a list of available operating systems and I'd choose which one I wanted. As updates for 10.04 were released, that list kept getting longer and stretched to two pages, but no problem.

Three weeks ago I upgraded to 12.04. The list of available operating systems shrank to 8 -- 12.04, three versions of 10.04, plus recovery versions of each. That's when the first odd thing happened: The six versions of 10.04 retained their build numbers (2.6 etc) but they were relabeled as versions of Pangolin. For example, Pangolin appears at the top of the list as "Ubuntu 12.04.1 LTS, kernel 3.2.0-34-generic" and Lucid Lynx appears below Pangolin as "Ubuntu 12.04.1 LTS, kernel 2.6.32-44-generic". The second odd thing was that when I tried to load one of the remaining 10.04 versions, I always got 12.04 instead.

I do not like 12.04 so after considerable research and planning, I decided that the simplest solution would be to reinstall 10.04. I backed up everything to dvds, downloaded 10.04.4, burned a live cd, and confirmed its integrity via md5sum. Last night I disconnected the Windows hard drive and reconnected the Linux drive as primary to receive 10.04. The installation program let me resize the partitions, so I reduced the 12.04 partition to 55Gb and left the other 245Gb for 10.04. 

I was able to log into the reinstalled 10.04 once, right after the installation, so I thought that the installation was successful, but...

Now at startup, bios gives me the same operating system choices as it did before the reinstallation of 10.04, and the available 10.04s still produce 12.04. 

Where did the new 10.04.4 go and how do I get it back??

---

### Post by Supercomputerpower on 2012-12-27
maybe you all ready know but reconfigure your grub bootloader i think will solve your problem [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

---

### Post by fdrake on 2012-12-27
```

sudo parted -l
sudo blkid

```post the output

---

### Post by apple pie maker on 2012-12-27
Model: ATA SAMSUNG SP1604N/ (scsi)
Disk /dev/sde: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  152GB  152GB   primary  ntfs         boot
 2      152GB   160GB  7789MB  primary  fat32        lba


Model: ATA Maxtor 6L300R0 (scsi)
Disk /dev/sdf: 300GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  56.3GB  56.3GB  primary   ext3            boot
 2      56.3GB  300GB   244GB   extended
 6      56.3GB  297GB   241GB   logical   ext4
 7      297GB   299GB   1327MB  logical   linux-swap(v1)
 5      299GB   300GB   1341MB  logical   linux-swap(v1)

---

### Post by apple pie maker on 2012-12-27
sudo blkid:

/dev/sde1: LABEL="HP_PAVILION" UUID="78F417CBF4178B10" TYPE="ntfs" 
/dev/sde2: LABEL="HP_RECOVERY" UUID="7580-436A" TYPE="vfat" 
/dev/sdf1: UUID="a5a90e3b-9aaf-47c3-b200-f725a64df4d4" TYPE="ext3" 
/dev/sdf5: UUID="0dc2107d-29ee-4b29-87c6-e71fbffe2ef8" TYPE="swap" 
/dev/sdf6: UUID="91827f4b-a16d-4119-bd0b-e113dd536816" TYPE="ext4" 
/dev/sdf7: UUID="fead132a-48b4-42d3-9ddd-86f71c843fc1" TYPE="swap"

---

### Post by apple pie maker on 2012-12-27
I read about GRUB and decided to upgrade from legacy to GRUB2. When I rebooted, I got an "error 15" message; according to one of the help pages GRUB2 does not return numbered error messages - so I must still have legacy GRUB, right? Advice from another place had me run /boot/grub/menu.lst, but that returned a "no such file" message. Further research found a page that said menu.lst was in  only GRUB legacy and was replaced in GRUB2 - so  I must have GRUB2. right? "grub-install -v" returns GNU GRUB 1.98-1ubuntu13 now; before I tried to upgrade, it returned 0.97. My general experience is that only about half of the various recommended commands work on my machine. I tried Boot Repair, too. It blamed the problem on a nearly full partition - which may be true for Pangolin, which is not the OS that I'm trying to restore - and it could not remove the problem files (which is what it seemed to want to do). Boot Repair had me enter 3 lines of code to force purge GRUB, but I got a message of "no such file or directory" for "apt-get" and for "dpkg". I also tried to reinstall GRUB2, but the machine refused and said it was already in place. 
In three weeks of this, I have lost about 30 hours.
If I reinstall 10.04 from the disk again, will that erase the apparently defective GRUB and replace it with a clean one?

---

### Post by fdrake on 2012-12-28
> **apple pie maker said:**
> I read about GRUB and decided to upgrade from legacy to GRUB2. When I rebooted, I got an "error 15" message; according to one of the help pages GRUB2 does not return numbered error messages - so I must still have legacy GRUB, right? Advice from another place had me run /boot/grub/menu.lst, but that returned a "no such file" message. Further research found a page that said menu.lst was in  only GRUB legacy and was replaced in GRUB2 - so  I must have GRUB2. right? "grub-install -v" returns GNU GRUB 1.98-1ubuntu13 now; before I tried to upgrade, it returned 0.97. My general experience is that only about half of the various recommended commands work on my machine. I tried Boot Repair, too. It blamed the problem on a nearly full partition - which may be true for Pangolin, which is not the OS that I'm trying to restore - and it could not remove the problem files (which is what it seemed to want to do). Boot Repair had me enter 3 lines of code to force purge GRUB, but I got a message of "no such file or directory" for "apt-get" and for "dpkg". I also tried to reinstall GRUB2, but the machine refused and said it was already in place. 
In three weeks of this, I have lost about 30 hours.
If I reinstall 10.04 from the disk again, will that erase the apparently defective GRUB and replace it with a clean one?

since last time i checked your post it looks like you have run a lot of different commands thjat may have changed grub.

Lets see if this works:
1. plug only the hhd with linux installed not both
2. boot into a live ubuntu cd
3. Run this commands (if the terminal askes you for a password just press ENTER)
```
sudo parted -l
```Now pay attention to the output! If the disk name is /dev/sdf , then just follow the nest commands. If your hdd name has changed yo something else (/dev/sda,/dev/sdb etc) then use the next command by changind /dev/sdf into /dev/sda, or /dev/sdb etc..same goes for /dev/sdf1> /dev/sda1 ! just change the letter "f" to the appropiate letter givend by the command.
4.```

sudo dd if=/dev/null of=/dev/sdf bs=446 count=1 
sudo mount /dev/sdf1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo grub-install /dev/sdf
sudo grub-install --recheck /dev/sdf
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
sudo reboot 

```

5. boot into ubuntu 12.04 and in the terminal run
```
sudo update-grub
```
6.reboot and see if you find 10.04

reference:[http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/](http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/)

------------------------------------------------------
if everything fails , then just reinstall ubuntu 10.04 from scratch. Choose option: "erase everything and install ubuntu"

---

### Post by apple pie maker on 2012-12-28
Dear fdrake,

Shortly after posting comment #6 and before reading your comment #7, I figured that I no longer had much to lose, so I decided to use BootRepair to *revert* to GRUB Legacy. When BootRepair finished, the missing operating system was right on top of the list and - get this - the title at the top of the page was "GNU GRUB 1.98". Yep, reverting was the way to repair the upgraded version. Whooduthunkit?

Anyway, I want to thank you for your efforts. I will study the material in your comment #7; I think that it will come in handy some day (even though I have sworn off doing any more upgrades).

Thanks again.

Apple Pie Maker

---

### Post by apple pie maker on 2012-12-28
Dear Supercomputerpower,

Thanks for your reply. It got me moving in the right direction and led me to learn stuff that I did not know.

Apple Pie Maker

---

