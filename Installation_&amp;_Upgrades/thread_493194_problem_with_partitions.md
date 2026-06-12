---
title: "problem with partitions"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by bluaki on 2007-07-05
Hi, I'm trying to install Ubuntu on my computer which already has Windows XP. to make it multi-boot. The computer is mainly Dell Dimension B110. The first HDD is taken from a Dimension 2400 (the 2400 was replaced when broken, I kept its HDD) and the second drive is the one included with the B110.
My disk was set up like this:

Physical 80GB Drive (1):
Partition about 76GB w/ Windows XP (Windows drive C:\)
Partition about 3GB w/ Windows XP (Windows drive G:\)
Partition about 50MB, I don't know what this was for. Not recognized by Windows.
Free Space, about 100MB

Physical 80GB Drive (2):
Partition about 76GB w/ no OS, used as storage for large files (Windows drive D:\)
Partition about 3GB w/ Windows XP, I don't need it and could delete it (Windows drive E:\)
Partition about 40MB, has unknown purpose and not recognized by Windows.
Partition about 60-70MB, also has unknown reason and isn't accessible from Windows.
Free space, about 512MB

I planned on installing Ubuntu on the free space on my second drive, deleting the partitions that I don't recognize and my Windows E:\ installation. I made two partitions in the Ubuntu installation: a 256MB swap and a 3GB ex3 (both on the second drive). I proceeded with the ex3. It installed past that, there was some sort of error at the end, II don't remember what it said. I restarted the computer (removing the Ubuntu CD), and it showed some boot loaded (it wasn't GRUB or NTLDR) and the boot loader just froze, not showing any choices. I rebooted again, onto the LiveCD (which I'm at right now). I've launched the Ubuntu installer and and the partition section, I realized many things were changed that I didn't want. Also, I've looked in "Computer" (under the "Places" menu) and found some drives I don't remember and some drives that I do remember are gone.

My new partitions:
Drive 1:
Partition about 76GB, with "efi" under "type", instead of the NTFS that was there before. Has only 32MB used.
Partition about 3GB, marked as "swap"

Drive 2:
Partition with 41MB, the same one that was there before (which was supposed to be deleted). FAT16 filesystem and 33MB used.
Partition about 76GB, still the way it was before. (but I think it used to be smaller)
Partition about 3GB, probably the same drive as the Windows E:\ that I wanted to be deleted.

The "computer" folder from Ubuntu shows:
CD-RW/DVD-ROM Drive
4 Removable card drives (I know they're connected through USB): Compact Flash, Memory Stick, SD, and Smart Media.
1.0KB Volume (Ubuntu can't mount it, shows error message)
3.2GB Volume: Disk (mounting it shows the XP partition that I wanted to delete)
DellUtility (39.2MB)
DellUtility (2) (72GB, 7.6MB used, the name includes the [2])
Drive 2 (I named it that way from Windows XP, it's the drive with no OS. Still completely intact)
Filesystem (doesn't give me any volume size or anything, I guess it's Ubuntu's files)

From the looks of it, both of my good XP installations were deleted, and the one I didn't want is the only one left. Ubuntu doesn't seem to be on either drive. Dell seems to be the reason to that, they created "DellUtility" folders that take up most of my disk space. The partition sizes and the drives in "computer" don't match up. The only thing that will boot is the Ubuntu LiveCD. (I might be able to boot my XP CD too, I don't think that will solve anything). Also, I am not allowed to modify or delete my files from my storage drive, "Drive 2". I am given a "read-only" warning. 
This seems like an extremely strange and rare problem, I couldn't find anything of use from searching through old posts. I hope I posted this in the correct section.

---

### Post by Mopana on 2007-07-05
I had some problems after repartitioning an old XP drive for an Edgy Eft installation on my laptop. The installation appeared to work, but GRUB didn't recognize the XP partition. Later, trying to reinstall Edgy Eft, the partition wizard didn't notice the XP partition either. My solution was to fix the MBR in Windows with their install CD, and this appeared to fix the problem; GRUB could then recognize XP and boot into it.

Maybe your installation got involved with the Windows boot loader? You might need to deal with the XP partitions before you get a clean Ubuntu install.

---

