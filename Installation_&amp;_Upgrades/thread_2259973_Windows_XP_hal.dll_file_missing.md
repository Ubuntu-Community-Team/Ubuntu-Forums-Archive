---
title: "Windows XP hal.dll file missing"
date: 2015-01-08
forum: Installation &amp; Upgrades
---

### Post by gogo3 on 2015-01-08
So, I installed Lubuntu 13.10(as 14.04 was somehow slow). It runs amazingly fast, but that's not the point here.
GRUB 2 also installed like it should. But while I was installing Lubuntu, I picked the option "Something else" instead of overwriting my Windows XP. I tried to minimise the space of my C: Partition to 50GB(it was around 55GB), but the installer got laggy and I had to quit it in the middle of an installation. It happened on 14.04 too, but it didn't show any problems. When I installed it and loaded GRUB 2, I tried to pick the Windows XP. But it showed "Windows XP couldn't start because the file hal.dll is missing"(Something like that.) When I tried to mount the C: Partition on Lubuntu, it gave me an error saying I need to turn something to 'ro' as this partition had a problem of some sort. Any answers will be really useful, as I still need Windows for some things!

EDIT:Error message down.
Error mounting /dev/sda2 at /media/gogo/1E58A3B358A3885B: Command-line `mount-t "ntfs" -o
"uhelper=udiskis2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177"
"/dev/sda2" "/media/gogo/1E58A3B358A3885B"' exited with non-zero exit status 14: Hibernated non-system partition, refused to mount. Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully(no hibernation or fast restarting), or mount the volume read-only with the 'ro' mount option.

To shorten these things out, I have 2 problems:
1.Windows XP doesn't work
2.Can't access C: partition which has some important files I do not wanna lose.

---

### Post by yancek on 2015-01-08
The problem is that you hibernated your xp before you installed Lubuntu which was a mistake.  You should have shut down xp completely.  That's what the error message you posted is telling you.  The site below explains how to fix the mbr for xp but you do need the xp install CD.  You might be able to get some free repair software online, I don't know as I don't use xp. 

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by oldfred on 2015-01-08
The not mounting is either hibernation or that it needs chkdsk.

And the hal.dll missing is almost never that, but issues with boot.ini.

You probably just need to boot XP installer in repair mode and run the full set of repairs. If you resized the NTFS partition it always needs a chkdsk.

---

### Post by gogo3 on 2015-01-08
Okay, thanks for everything guys. I'm actually thinking of reinstalling Windows all over, but I have 1 more question:
When I install a new Windows XP, will it's boot loader overwrite GRUB 2, and if not, will GRUB recognize the new Windows?

Also, I have NEVER EVER hibernated, and my Windows isn't in C: partition, it's in D: partition.

---

### Post by efflandt on 2015-01-08
You likely messed up the Windows partition by partially resizing it and then exiting. Anytime you use Linux tools to resize a Windows partition it is marked as dirty, so even if you did it completely (instead of aborting) you should have resized it from a live/install iso and rebooted Windows, so it could run its automatic checks, before installing Linux. For XP you also should have disabled virtual memory (similar to Linux swap) and defragged the partition before resizing it because virtual memory in Windows is usually not movable.

Or for reference in Win7 or newer (maybe Vista too?) you should use Windows' own Disk Management in Admin Tools to resize any Windows partitions to make sure everything is done to its satisfaction, before adding or expanding Linux partition(s). But I do not think WinXP can do that.

Reinstalling Windows will overwrite the mbr, but you can reinstall grub in the mbr [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) or maybe try bootrepair if you have trouble figuring that out (never tried it) [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

