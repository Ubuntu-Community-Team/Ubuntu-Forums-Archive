---
title: "New install, all goes well untill first system boot."
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by derr12 on 2011-04-28
Hi, I am installing server 10.04 on a amd64 system.   two 500gb drives mirrored. I didnt have any problems installing.  

md0 = 128mb /boot ext4
md1 = 16gb /swap
md2 = 2gb /tmp  ext4
md3 = 30gb /  ext4
md4 = the rest /var ext4

when i boot the system halts saying that the file system is corrupt @ /var.  I tried running fsck and it said that the partition table may be corrupt and couldnt repair. Ive wiped the drives clean with boot n nuke and tried to re-install with the same thing.  

I was using the sata ports in raid mode (single disks) so ive reverted to native IDE and I am attempting to wipe and start over.  

Im probably going to do a single drive install first and then make the raid arrays after the first boot.  

Anyone ever see this before? I was using a nearly identical system for an install a few weeks ago and did not have these problems.  The only difference was i was using native IDE mode on the sata ports.

---

### Post by derr12 on 2011-04-28
oh yeah, they were 2tb disks in the other system, so these are mbr disks the others were gpt.

---

### Post by derr12 on 2011-04-29
Ok so i tried setting up on a single disk, it booted. 

What i found was that the first mbr partition overlaps the first primary partiton when i sfdisk -l /dev/sda

I also tried re-installing with only 2 raid partitions,  128mb /boot  and another partition where i am using the logical volume manager for /var /tmp swap and / 

First boot hangs at ureadahead-other terminated with status 4.

what is going on here?

---

### Post by derr12 on 2011-04-29
Ok on the assumption that the installer was too stupid to reserve data for the mbr partition, i created the two partitions at the end of the drive instead of the front with plenty of space in between, 

md0 128mb /boot
md1 /499.9gb logical volume w/
/ 30gb
swap 16gb
/tmp 2gb
/var the rest.

It crashed to an Initfs shell and wouldnt boot.  

going to try a singe disk config without logical volumes this time.  

this is starting to get irritating. Ive never wanted to punch a server so bad ever...

---

### Post by derr12 on 2011-04-29
Ok single disk config booted but i cant copy the partition table over.  

Run a sfdisk -d /dev/sda | sfdisk /dev/sdb and it says it cant write to the device, so i do a -f and it makes 4 empty partitions. 

during install i created 1 primary partition /boot @ 128mb
and 4 extendeds 
/
/var
swap
/tmp

when i sfdisk -l  

I get those partitions plus a few empty ones, does sfdisk show extended partitions properly?

---

### Post by srs5694 on 2011-04-29
Unfortunately, I can't parse what you're saying because you're using terminology very poorly. I recommend you start over again and describe what you're *really* doing. Some issues:

> **derr12]I tried running fsck and it said that the partition table may be corrupt and couldnt repair.[/quote]

The fsck utility works on filesystems, not partition tables. I've never known fsck to complain about partition tables, and as it's not given data on partition tables, it seems very unlikely to me that it would do so. If you're sure this is the message, please quote it verbatim, including the exact fsck command you issued. (Or do you mean fdisk rather than fsck?)

Further background: Disks are split into partitions, which are just contiguous sets of sectors -- for instance, sectors 2048 through 204800. Within most partitions, filesystem data are written, and the OS uses the filesystem data to control where it writes individual files and related data. Since fsck works on filesystems, it knows about that limited set of sectors (such as 2048 through 204800), but not the partition table itself, which is in sector 0 for MBR disks, plus additional sectors for logical partitions.

> md0 = 128mb /boot ext4
...
I was using the sata ports in raid mode (single disks) so ive reverted to native IDE and I am attempting to wipe and start over.

The /dev/md0 device filename normally indicates Linux software RAID, in which the hard disks are managed as normal non-RAID devices by the motherboard said:**
> the first mbr partition overlaps the first primary partiton when i sfdisk -l /dev/sda

The Master Boot Record (MBR) is another name for the first sector of the disk (sector 0). It also refers to a partitioning system in which up to four *primary* partitions may be defined. Using this system, one of those four primary partitions may be an *extended* partition that can hold an arbitrary number of *logical* partitions.

Thus, the statement that "the first mbr partition overlaps the first primary partiton" is unclear at best and unintelligible at worst; a primary partition is, in some sense, a type of MBR partition, but what partitions are overlapping is extremely unclear. Post the output of "sudo fdisk -lu /dev/sda" (or whatever the device is) to clarify what's going on. (Note that fdisk shows partition start and end points, whereas sfdisk works in partition start points and lengths, which is much harder to work with when looking for overlapping partitions; hence my instruction to post the "fdisk -lu" output.)

> First boot hangs at ureadahead-other terminated with status 4.

Post the *exact* error message, preferably including a few lines of context.

> on the assumption that the installer was too stupid to reserve data for the mbr partition

It's very unclear what you mean by "the mbr partition." Unless you're using GPT or some other partitioning system, *all* of your partitions (or at the very least all of your primary partitions) have equal claim to being MBR partitions. (If you're using GPT, then the MBR contains a "protective partition" that covers the whole disk, but it's ignored; only the GPT partitions are valid on GPT disks.)

> during install i created 1 primary partition /boot @ 128mb
and 4 extendeds 
/
/var
swap
/tmp

when i sfdisk -l  

I get those partitions plus a few empty ones, does sfdisk show extended partitions properly?

Ordinarily, only one extended partition can be created per disk. That partition can hold an arbitrary number of *logical* partitions, so it's probable you mean "logical" when you write "extended". Without seeing your partition table I can't comment on what's there, and without knowing *precisely* how you created those partitions and what installation options you chose, I can't speculate on why you might have partitions you aren't expecting to see.

---

### Post by derr12 on 2011-04-29
well fsck was a dead end anyways. Ive since tried a few different setups and had a few different results.



Here is what im trying to do right now to keep things nice and simple, 

Installing 10.04 server on an gigabyte AMD 890 motherboard. 
In the bios i have my sata ports set to native ide

i just pre-formatted both disks with the live CD with;
-1mb at beginning of disk (unallocated)
-128mb (unformatted)
-rest of disk (unformatted)

I started the installation and am going to use linux software raid.  

md0 is the 128mb partition formated as ext4 /boot
md1 is the rest of the drive formatted as (reserved for LVM)

I created a Logical group on md0 and made the following logical volumes;
16gb /swap
2gb ext4 /tmp
30gb  ext4 /
the rest ext4 /var

This time the system booted.  The only difference is that i pre-formated using gparted on the live CD.  

Im not really sure what the problem with the way the installer was making partitons. 

I tried using the installer like this 
128mb primary 
the rest of the drive logical. 

md0 had the 128mb /boot
md1 had a logical group w/
16gb /swap
2gb ext4 /tmp
30gb  ext4 /
the rest ext4 /var

that didnt boot.  

I tried 1 raid device per partition 

md0 /boot
md1 /swap
md2 /temp
md3 /
md4 /var 

that didnt boot.  

Anyways.  Im done thinking about this, it killed 2 days at work so......

---

