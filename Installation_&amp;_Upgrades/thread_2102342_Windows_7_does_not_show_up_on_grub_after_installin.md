---
title: "Windows 7 does not show up on grub after installing Ubuntu 12.10"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by Gortzilla on 2013-01-07
Today I installed Ubuntu 12.10. It's been awhile since I last played with Ubuntu, back around 9.04.  After installing, I saw that Windows 7 didn't show up in the Grub menu. I've been trying for most of the day to get it Windows 7 to boot, but nothing I've tried has worked. I tried just forgetting about the Ubuntu installation and use the Win 7 disk to do a startup repair. That didn't work, so I tried Boot-Repair, which was scanning for almost an hour before I gave up on it. I tried adding the entry manually to Grub 2, but I'm not sure what exactly I should put. This is what I put in the 40_custom, then did sudo update-grub:
```
menuentry "Windows " {
insmod ntfs
insmod chain
insmod drivemap
set root=(hd1,5)
drivemap -s (hd1)(hd0)
chainloader +1
}
```


I feel like a major issue is my sata card. I have a sata card I use since the sata ports on my motherboard are dead. I think it is the cause of a few problems. Gparted always hangs when scanning, as do other tools like Boot-Repair. 

EDIT: I let Gparted and Boot Repair go overnight, and they both finished scanning when I woke up. It took more than 40 minutes for them to do their thing though, since I started it and checked on it just before I went to sleep. Is there any reason they'd take so long? I guess I needed to be more patient.

Boot Repair Output: [http://paste.ubuntu.com/1506716/](http://paste.ubuntu.com/1506716/)

I've tried using my Win 7 install disk to do a repair, but nothing has helped. Startup Repair isn't able to fix anything. I tried /fixmbr and /fixboot. /fixmbr is successful but /fixboot gives "The volume does not contain a recognized file system."

What's a next good step? Thanks for any help.

---

### Post by Gortzilla on 2013-01-07
I waited over night and Boot Repair finished scanning. Here is the output: [http://paste.ubuntu.com/1506716/](http://paste.ubuntu.com/1506716/)

---

### Post by darkod on 2013-01-07
Looks like win7 boot files were on /dev/sda and you deleted that partition.

Windows can put boot files on a partition which has the boot flag even when it's on another disk, and it is not informing you about this. That way you might even not know that that partition has windows boot files and not to delete it in the future.

Also, your win7 system partition sdb5 seems to have EFI part of the bootloader, but your disks have msdos tables and win7 works with uefi only on gpt table. I guess that efi file might be mistake, maybe a result of the repair you tried to do.

On the top of this, the win7 system partition is logical, and the windows boot files need to be on a primary partition.

You can either convert it to primary and try the win7 repair process to write the boot files there, or add a small ntfs partition with the boot flag on /dev/sda.

I can see that sdb5 is taking the whole hdd but it is logical, and i see no point in that. I don't know whether you created it like that or the win7 installer, but when you have only one partition on the whole hdd make it primary in the future. You use logical (extended) partitions when you already have 3 primary on the disk, not when you want only one partition on the whole disk.

---

### Post by Gortzilla on 2013-01-07
I'm not sure why the Win 7 partition is logical. I was concerend about that, but figured that's how it's been since install. I did have Win 8 Consumer Preview on the hard drive that has Ubuntu now, so that could explain why Win 7 has EFI stuff.

To fix it, do you think it's easier to convert it to a primary or to add an ntfs partition on /dev/sda? I guess making it primary is the more correct way to do it, but I'm not sure what needs to be done. I'd like to avoid a reinstall of Win 7 if I can.

If I add a small ntfs partition to /dev/sda, would I need to run the Win 7 recocery environment, then Boot Repair?

---

### Post by oldfred on 2013-01-07
+1 on Darko's comments.

I always prefer to have Windows on sda so it does not do this type of install. It installs its boot files to the boot drive in BIOS and the active partition which in Linux we see as the boot flag.

You can convert sdb to primary and/or may have space in front of the extended to let you add the boot partition in from of your main install. Windows will only repair and install it boot files to your current sda5 if you convert to primary, have boot flag on that partition and have BIOS set to boot from that drive when doing repairs.

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by darkod on 2013-01-07
I have no idea what a dual boot of win8 and win7 would do, especially since windows is rather idiotic in some things. You are using legacy boot, not the newer UEFI boot as it seems. And win7 can only work on msdos table with legacy boot. Or only on gpt table with uefi boot.

If you decide to create small 100MB ntfs partition on /dev/sda, make sure you use Gparted and set the boot flag on. Also, remove the boot flag from sdb5, it's pointless there and can only confuse the win7 repair process.
Yes, you will need to run the win7 repair after that. There is no need to run boot-repair really, because even if the win7 repair process deletes grub2 from /dev/sda, it's easy to add it from live mode. Much faster than running boot repair.
Or if you delete the ubuntu partition to create the small ntfs at the start of the disk, you will have to reinstall ubuntu anyway which will reinstall grub2.

The only benefit of running boot-repair will be to see if the win7 boot files are in its place. Two boot files/folders named /bootmgr and /boot/BCD should be either on the small ntfs partition or on the win7 system partition.

If you decide to cenvert it to primary, Fixparts seems to have a way to easily convert logical to primary in this case:
[www.rodsbooks.com/fixparts/](www.rodsbooks.com/fixparts/)
Note that if you decide to go this way, things change and none of the above applies. You will have to set the boot flag to the win7 system partition, which when converted to primary should be /dev/sdb1, and remove the boot flag from /dev/sda1 (currently there is one there). Then start the win7 repair process.

---

### Post by Gortzilla on 2013-01-07
Thanks darkod and oldfred so far. I used fixparts to convert the logical drive to primary. I removed the boot flag from /dev/sda1 and put a boot flag on /dev/sdb1. I started with Win 7 repair process, but progress is slow. I tried the startup repair. 
First time through I get (when looking at the details of the repair): "The partition table does not have a Valid System Partition. Repair action: Partition repair. Result: Completed successfully." 
Next I Reboot and get: "disk boot failure, insert system disk and press enter."
I put in the system disk again, and go through startup repair again. It gives the same message as previously, and the same result.

If I use the command prompt: 
bootrec /fixboot returns "Element not found."
bootrec /fixmbr returns "The operation completed successfully."
bootrec /scanos returns "Total identified Windows installations: 1 [1] C:\Windows"
bootrec /rebuildbcd returns "Element not found."

I tried disconnecting my Ubuntu drive. I go through startup repair again, and when I reboot I get "A disk read error occurred. I do ctrl + alt + del to restart, and get the same thing. 

What's the next step?

---

### Post by oldfred on 2013-01-07
Were you doing the auto repairs the first time? You have to run those 3 times. But your manual repairs should have worked. Did you have BIOS set to boot from the Windows drive, or did Windows then overwrite grub on the Ubuntu drive?

Did you also run chkdsk on the NTFS partition? That often is one of the first things to run.

Try Boot-Repair again, if still slow it means you need to run chkdsk on NTFS partition(s) or fsck on Linux partitions as it seems like it cannot load & parse something and has to time out.

---

### Post by Gortzilla on 2013-01-08
I did auto repairs the fist few times. I did at least 3, because I've seen that number thrown out there a lot. 

I finally got it to work. I worked with only the 500GB drive attached. I think I read somewhere that there can't be too large of a gap before a primary partition. I really wish I remember where I saw that so I could learn more about it. I booted into the Ubuntu live CD, ran Gparted, and resized my Win 7 partition so it filled that 16 GB I had preceding it. I then used the windows recovery disk 3 times through. Everything isn't quite how I want it, my 250GB drive isn't connected, but now that I have the Windows thing all fixed, it should be fairly starightforward to set up, and a majority of the problems are fixed.

Thank you so much for helping me oldfred and darkod. It's community members like you that really make linux more accessible. Keep up the good deeds.

---

### Post by oldfred on 2013-01-08
I would suggest to keep Windows as sda or first port on SATA motherboard. With XP you could not change without editing boot.ini, newer Windows are somewhat tolerant of drive order changes, but still seem to work best if on first drive and first partition. 
Ubuntu now uses UUID and is very tolerant of drive order changes. But some systems and some older BIOS still do not let you boot other than sda. My 6 year old system boots fine from any SATA port and my flash drive with a full install is sometimes sdb and sometimes sde but still works either way as when booting BIOS/grub sees it as hd0. Boot drive is always hd0.

---

