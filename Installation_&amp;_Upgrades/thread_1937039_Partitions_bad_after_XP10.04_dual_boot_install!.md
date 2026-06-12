---
title: "Partitions bad after XP/10.04 dual boot install!"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by jbuczek on 2012-03-07
I have concluded that the Ubuntu 10.04 LiveCD Install and/or gparted have messed up the HDD on my wife's computer.  Those of you who are married will appreciate this is serious.

Hardware:  Dell Dimension 8200, RAM 1GB, HDD 80GB, nVidea Display card

After almost 10 years the original XP was slow so I wiped it and reinstalled XP Pro SP3 from a Dell OEM CD. Drive partitioned as:
	1 - 20 GB WinBoot
	2 - 20 GB extended
	        1.5 GB WinSwap
		18.5 GB WinData
        40GB unallocated
			
Everything worked fine.  Installed my wife's apps and she played with it for a week A-OK.

I then installed Ubuntu 10.04 LTS using gparted to expand the extended partition to use all remaining space and to reworked the logical partitions as now reported by "System/Administration/Disk Utility":

HDTYPE: ATA ST380023A mounted on Port 1 of PATA
sda1		19GB NTFS, WinBoot
sda2		61GB Extended
sda5		20GB NTFS, WinData
sda6		1.6GB NTFS, WinSwap
sda7		2.1GB Linux Swap
sda8		17GB ext4, UbuntuBoot
sda9		21GB ext2, UbuntuHome

	18,446,744 TB Free       <TB is NOT a typo>
			
Here's the glitch: gparted under LInux and PartitionMagic8 under XP both now report no valid partitions and 74.53GB unallocated on this 80GB drive.  Under Linux fdisk reports no partitions. 

BUT - the computer will boot.  It finishes the Dell BIOS, hangs for three minutes and reports:

	Primary HDD 1 not found, 	Primary HDD 2 not found
	F1 to continue		F2 for Setup
	
F1 gets me to GRUB after another minute or so wait and either OS will then boot from the menu.  XP works for a random period of 5-30 min then locks up.  Ubuntu will lock up about once a week.

To save myself the headache of reactivation and downloading hundreds of "hot fixes" for XP again I tried clonezilla to back up the WinBoot but after hours it generated dozens of pages of error logs and wrote nothing.

It seems the partition table has been damaged.

I could wipe the whole thing and spend a week rebuilding it but first  I'd like to be sure there is no quick and easy fix.  A day of searching and reading suggests TESKDISK and other tools can repair the MBR and partition table but........???

So is there anyone out there that has seen this and can point me at THE genuine, certified quick and simple fix?

TIA

---

### Post by darkod on 2012-03-07
I believe you shouldn't have expanded the extended partition. Since the unallocated space was next to it, simply creating logical partitions using the manual method during the install would extend the extended partition automatically to include the new logical partitions.

In this situation, you can try using fixparts which can locate some errors in the partition table and fix them. Run it from ubuntu live mode.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

It looks to me like you have partitions overlapping, maybe because of the resize. That would make it confused and not showing the partitions.

---

### Post by Mark Phelps on 2012-03-07
Personally, I wouldn't trust Partition Magic 8 anymore.\

As an alternative, if you have another PC, download the free Partition Wizard Boot CD ISO and burn it to PC.  Note that it's an MS Windows product.

Then boot this PC -- the one that has problems.

See if PW then is able to see the partitions.  If it does, since it's a current product, you may have more success fixing the partition problems.

---

### Post by ottosykora on 2012-03-07
> **Mark Phelps said:**
> Personally, I wouldn't trust Partition Magic 8 anymore.\

.

+1

partition magic is not compatible with the 'vista' type of partitions which are used by vista and w7.
It will definitely break the partitioning.
It is OK to use it on older systems up to XP or linux with up to ext3 etc, but not when the drive was touched by any current partitioning tool as gparted etc before.







partition magic was an excellent tool, probably the first of its kind, and as it goes often, real innovators do not survive the commercial battle.

Symantec bought the rest of the company, the devs left however, symantec did not bother to develop the tool any more, not enough revenue apparently.

---

### Post by jbuczek on 2012-03-07
As I said in my original message.... I was using XP, not Vista or later.

In this case I used Partition Magic only to examine the partitions although it was used to construct the partitions used by my original XP install.

I'll look into "fixparts" today.

Thanx

---

### Post by darkod on 2012-03-07
Also, have you tried what is the output of:
sudo parted /dev/sda print

---

### Post by jbuczek on 2012-03-09
Classify this as SOLVED!

Per the suggestion of DARKOD, I downloaded and tried "fixparts".  It reported "partition not aligned to cylinder". I copied everything off the HDD since fixparts apparently does NOT do non-distructive repairs, then corrected the problem and restored.  Fortunately the extended partition involved did not contain XP so I didn't have to do any MS activation/deactivation songs or dances.

Many thanks to all.

---

