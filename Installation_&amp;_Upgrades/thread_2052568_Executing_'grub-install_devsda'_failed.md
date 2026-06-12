---
title: "Executing 'grub-install /dev/sda' failed"
date: 2012-09-03
forum: Installation &amp; Upgrades
---

### Post by an0nym1ty on 2012-09-03
Hello 

I keep getting the "fatal error" in the title each time i try to install kubuntu 12.04 onto my raid 0  (which has a fresh win7 install on it at the begining of the disk).

I have searched and everything that comes up says:

1. it's not  fatal (you can install grub manually via live cd/usb whenever you want)
2. it's probably because you're not installing to MBR

I found a really solid reply to the question: 

I'll repeat. Don't install a raid boot loader to a non-raid location (ie sda,sdb, etc). The symbolic links for the raid drive and partition for your system can be listed in /dev/mapper. The first item in the list (after control) is the raid drive. Items following are the partitions. Following the instructions for reinstalling grub 2 I listed in my previous post, you reinstall grub for a raid as follows:

Mount the raid partition your new Ubuntu is installed to -
sudo mount /dev/mapper/<TargetRaidPartition> /mnt

Install and configure grub to boot on the raid -
sudo grub-install --root-directory=/mnt/ /dev/mapper/<YourRaidDrive>
Above - make sure that is /mnt/

Unless your system is an exception and the above doesn't work a reboot of your system should place you in the grub menu. Good luck.
 
___________________


however it unfortunately is not doing the trick for me... when i sudo mount I get a "Permision Denied" return from the terminal. It sort-of seems like that is a solution IF you get the OS fully installed, but my install crashes when the error pops up.

Another note: I have changed the install path for grub many times, and no matter where I put it I always get the /dev/sda even though that is not where I told it to install... (i tried /dev/mapper, /dev/mapper/<the windows install partition>, and the primary ext3 partition i made for my root -- all of which produced the same error, and none of which are "non-raid locations")

Here's my sudo fdisk -l, which seems very sparse...

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x746e6572

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb9624d97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953122815   976561376+  42  SFS
fdisk: unable to seek on /dev/sdc: Invalid argument

the no valid partition table is a little disconcerting...   This was taken right after a failed install and making a new root and swap in gparted.

thanks in advance = \

edit: the hd i'm trying to install on is /dev/sda (which has another 150gb as an NTFS partition)

---

### Post by oldfred on 2012-09-03
I do not know RAID.

But this says you converted your Windows to dynamic partitions which is like LVM is in Linux. But dynamic partitions do not work with Linux.

/dev/sdb1              63  1953122815   976561376+  42[COLOR=Red]  SFS[/COLOR]

Not sure how to undo that if inside your RAID install. On non-RAID systems these have worked:

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

I found this in my notes:
can I mount my WinXP software RAID 0 array in Ubuntu/Kubuntu? dynamic use mdadm
[http://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk](http://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk)

---

### Post by an0nym1ty on 2012-09-03
i believe sba/sba1 are both the same (second) raid-0 that I use as a slave drive.


this may be relevant...

when I installed windows, I didn't want to have the "system reserved" partiton, so when it was created I re-sized that to how big I wanted, and deleted the other one (leaving just a 150gb "system reserved" portion, which I used as the OS install).   I'm in windows right now looking into the dynamic thing


EDIT: yeah that output from fdisk was definitely referring to the second raid. The drive I am trying to install on is not dynamic. I thought the system reserve thing may have messed with it, but it doesnt look like it did.

EDIT2: I mean.. if i could only get the install to NOT terminate after it fails to install grub, then I could install grub manually myself...i just don't know how to do that. When I installed this setup on my laptop a while ago, I had a grub issue then too...but it didn't say the error was fatal. It just told me that i'd have to get a bootloader myself

---

### Post by helmut0 on 2012-09-03
I'm having the same problem for 3 weeks now.I did a dual boot when 12.04 was in alfa on a acer netbook,but mnow with the finished version on a different acer netbook with W7 it installed and then updated fine then grub rescue.I deleted the partitions and started over and it worked again for a while then grub rescue.Now when I insall it says can create partition 5....Painful

---

### Post by oldfred on 2012-09-03
Are you using the alternative installer? That includes RAID drivers that the standard desktop installer does not have.

Run Bootinfo report and post link it creates:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by an0nym1ty on 2012-09-03
boot info output:

[http://paste.ubuntu.com/1184183/](http://paste.ubuntu.com/1184183/)

edit: as far as installer goes, (since i don't see it just glancing at the boot info link), i'm usnig the standard 64-bit download from kubuntu.org. I'm doing the recommended boot-repair fix and re installing to see if that works (i'm not optimistic).

edit2: same business after boot-repair "fix", currently downloading alternative installer

---

### Post by oldfred on 2012-09-03
I am not sure what the interaction with SFS/dynamic Windows partitions and your hardware RAID may be but Linux generally does not install to Windows SFS drives as it cannot see them.

---

### Post by an0nym1ty on 2012-09-03
update:

the alternative installation gave the same exact error, but it gave me enough control to skip any specific part of the installation I chose, and I was able to continue the installation without installing grub.

When I continued, it told me this: 


boot loader has not been installed, either because you chose not to or because your specific architecture doenst support a boot loader yet
 
 
 you will need to boot manually with the /vmlinuz kernel on partition
 /dev/mapper/jmicron_RobBrown2 and root=/dev/mapper/jmicron_RobBrown2 passed as a kernel argument

I am in the process of re-writing my flash drive with a live cd (alternative doesnt seem to have a live component) to start the grub install process. Any advice on this would be much appreciated.

---

### Post by oldfred on 2012-09-03
Alternative is not liveCD. extra drivers for RAID, LVM and others did not leave room for gui and liveCD.

From liveCD you can install the RAID driver.

I know this works with the software RAID, but not sure with your Promise system.

sudo apt-get install mdadm

I think Boot-Repair automatically downloads the mdadm driver.

**Multi OS on RAID 0 array - says use dmraid**
sudo dmraid -l
[http://ubuntuforums.org/showthread.php?t=1886279](http://ubuntuforums.org/showthread.php?t=1886279)

RAID add kpartx to LiveCD or use alternative text installer
[http://ubuntuforums.org/showthread.php?t=1811353](http://ubuntuforums.org/showthread.php?t=1811353)
[http://ubuntuforums.org/showthread.php?t=1631336](http://ubuntuforums.org/showthread.php?t=1631336)

---

### Post by darkod on 2012-09-03
As already mentioned, don't even try to install it onto dynamic disks.

First convert the disk back to basic, and then it will work.

Even though the live cd can see a fakeraid array, you need to install with the alternate cd since it has raid and lvm support. If you use the live cd like you did, the grub2 install often fails. You can add it later, with the steps you posted in post #1, but in this case I think the dynamic disk is what's playing with you.

---

### Post by an0nym1ty on 2012-09-03
just an update for anyone now or in the future:

after skipping the grub install and booting with the live cd, following the instructions I quoted in my first post fixed the issue.  booted my raid, lo and behold was the grub bootloader.

Thanks a million for your help oldfred

---

