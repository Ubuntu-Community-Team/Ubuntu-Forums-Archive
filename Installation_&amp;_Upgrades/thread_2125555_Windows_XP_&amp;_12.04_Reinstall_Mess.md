---
title: "Windows XP &amp; 12.04 Reinstall Mess"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by eddiedee on 2013-03-14
Hello - First let me preface this by saying had I the opportunity to do things differently I would have. I upgraded the Mobo & CPU and wanted to move from 32bit 12.04 to 64bit 12.04 and re-install windows XP.

Here is the scenario:
Ubuntu 12.04 32bit and Windows XP dual booting happily on the same physical drive, (2 NTFS parts, XP & Storage, 2 EXT4 parts Linux & Swap)
Upgrade Mobo & CPU (z77-ds3h & i5 3570K)
Install from USB, Boot into 12.04 64bit without issue
Run Windows set-up from disk, new installation in existing Windows partition
Boots directly into Windows XP, all data/partitions still present on disk viewable in XP
I knew XP would overwrite MBR w/ windows bootloader so I booted w/ USB into linux-secure-remix to run boot-repair & re-install Grub
run boot-repair, restart, machine boots into windows
Boot from USB w 12.04 64bit ISO, run install, no partitions on found on dev\sda, neither the 12.04 or Windows installations are found by the installer
Install gives the option to erase everything (very bad, I must save the data in the NTFS storage partition) or do something else. Doing something else yields no visible partitions on \sda

sudo fdisk -l lists the NTFS & ext4 partitions, they are still present.

sudo parted /dev/sda print yields "Error: Can't have overlapping partitions" I would copy fdisk but am not at my pc right now;
  sda1 - NTFS 
  sda2 - NTFS
  sda3 - extended (to ~xxxxx99)
  sda4 - Ext4 (swap)
  sda5 - Linux (to ~xxxx999)
Note I did not change any partitions during this install cycle (or intend to, boot-repair perhaps?), the configuration was working perfectly for some time though I cant be 100% sure that sda5 was within the extended sda3 partition.

I have no idea how to proceed. The disk was originally partitioned with gparted.

OS wise I think I have everything where I want it but can only boot into XP and don't seem to have a partition table ubuntu can see.

Thanks in advance.

---

### Post by dino99 on 2013-03-14
from the liveusb, open a terminal, and install/reinstall grub:

sudo grub-install /dev/sda
sudo update-grub

then reboot on the hdd (select that disk too into bios)

---

### Post by oldfred on 2013-03-14
If you have overlapping partitions, some partitioning tool did not write table correctly. And then many tools do not work as partitions must be correctly read for them to work.

       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

Post details
sudo fdisk -lu

---

### Post by eddiedee on 2013-03-15
I haven't touched the disk partitions in over a year. If anything changed partition wise it could have been the Windows XP installer or boot-repair, neither seems likely.

ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda > parts.txt
**Warning: extended partition does not start at a cylinder boundary.**
DOS and Linux will interpret the contents differently.

ubuntu@ubuntu:~$ sudo fdisk -lu 
omitting empty partition (5)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x117d117c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   163837951    81918944+   7  HPFS/NTFS/exFAT
/dev/sda2       163837952  1748725759   792443904    7  HPFS/NTFS/exFAT
/dev/sda3      1748727806  1953523711   102397953    5  Extended
/dev/sda4      1947514880  1953523711     3004416   82  Linux swap / Solaris
/dev/sda5      1748727808  1947514879    99393536   83  Linux

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4f5a4f59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    72276434    36138186    7  HPFS/NTFS/exFAT

---

### Post by eddiedee on 2013-03-15
[http://paste.ubuntu.com/5616529/](http://paste.ubuntu.com/5616529/)

---

### Post by oldfred on 2013-03-15
It looks like you swap changed from sda6 which would be inside the extended partition to sda4 which has to be outside extended partition, but still is inside it. 
You can use the sfdisk output and change the sda4 to sda6 and reimport it.
But I think you can just use fdisk and have it rewrite partition table.

Do not press w unless it looks ok. It may reorder other partitions, but in your case I do not think anything else will change. Btu always good to have LiveCD/DVD/Flash handy.

 You can reorder the partition with fdisk:
sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk
q  # quit

Error on cylinder boundry has not appled since drives went over 8GB. BIOS should be set to Large or LBA not IDE?

---

### Post by nibal on 2013-03-15
@eddiedee:
> Device Boot      Start         End      Blocks   Id  System
> /dev/sda1   *          63   163837951    81918944+   7  HPFS/NTFS/exFAT
> /dev/sda2       163837952  1748725759   792443904    7  HPFS/NTFS/exFAT
> /dev/sda3      1748727806  1953523711   102397953    5  Extended
> /dev/sda4      1947514880  1953523711     3004416   82  Linux swap / Solaris
> /dev/sda5      1748727808  1947514879    99393536   83  Linux

I think I see your problem. /dev/sda3 is your extended table. It is not an actual partition per se, but lists the space occupied by all (subsequent) extended partitions.
However, its type seems wrong: Extended (5). Mine is W95 Ext'd (LBA) (f). That's why Ubuntu doesn't recognize your partitions, and fdisk reports overlapping ones.
It's easy to correct the type from within fdisk:

```

sudo fdisk /dev/sda
m                                                              // List menu of available ops
t                                                              // Change partition's system id

```

However, before you do it, it is a dangerous operation, you better wait for oldFred, to see what he says about it. 
It won't touch your NTFS partitions, only your Linux ones, which you don't care anyway. Also you waste space between your partitions.
Once you fix your problem, you may want to go back and tighten them up a bit.

BR,
Nikos

---

### Post by eddiedee on 2013-03-15
I tried to re-order 4 to 6 but was unable:

Command (m for help): x

Expert command (m for help): f
Nothing to do. Ordering is correct already.

Thinking further about this, I do recall the swap being after Linux prior to this failed XP/12.04 re-installation. I wonder which installer messed with my partitions, must have been windows.

---

### Post by nibal on 2013-03-15
> **eddiedee said:**
> I tried to re-order 4 to 6 but was unable:

Command (m for help): x

Expert command (m for help): f
Nothing to do. Ordering is correct already.

Why would you do such  thing? You just need to change the ID (t) of dev/sda3 from 5 to f. No expert mode needed. I recommend waiting for oldFred.

Nikos

---

### Post by eddiedee on 2013-03-15
I was doing what oldFred advised, see the post above yours.

---

### Post by nibal on 2013-03-15
> **eddiedee said:**
> I was doing what oldFred advised, see the post above yours.

Yeah. Sorry, I didn't see that and thought you were playing around with your partitions:(. Anyway, that is not your problem. Sure it
would be nice to sort your partition table, but not essential. fdisk reports "overlapping partitions", right? Well, this is not caused by
out of order partitions, but it could be caused by incorrect partition types.

@oldFred:
What do you say he changes the partition type of /dev/sda3 from 5 to f? At worst it will do nothing, at best it will fix the problem.

BR,
Nikos

---

### Post by oldfred on 2013-03-15
I thought reorder would do it.

 But I thought t was the command to change type ( or its format code in partition table).

Download and run fixparts. Besure you have the backup table  from sfdisk.
       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by nibal on 2013-03-15
@oldfred:

> But I thought t was the command to change type ( or its format code in partition table).

That's exactly what it is! The only overlapping partition, as reported by fdisk, is /dev/sda3, which in reality is the extended partition table.
I am not familiar with the Extended type, I only know the W95 Ext'd (LBA) type, and from the error it seems that neither fdisk understands it!
If fdisk doesn't understand it, then noway ubuntu can get it.

What do you say? It will only take a second, and NTFS partitions should not be affected, since they are below it. After that, he can fix
any order he wants.

@eddiedee:
A workaround, for reordering:
Since you don't have any data in your Linux, delete from fdisk in your live CD, both swap and linux partitions. Then create them again and they will
take the correct order.

HTH,
Nikos

---

### Post by kuifje09 on 2013-03-15
[QUOTE=nibal;12558677]@eddiedee:

> /dev/sda3      1748727806  1953523711   102397953    5  Extended


However, its type seems wrong: Extended (5). Mine is W95 Ext'd (LBA) (f). That's why Ubuntu doesn't recognize your partitions, and fdisk reports overlapping ones.


Depends who created it.  This one is the "linux" style, the other windows style. For linux it does not matter.

---

### Post by eddiedee on 2013-03-15
Well, thanks to you both.

Running FixParts, p then s did the trick. Booted into Grub upon restart.

Thanks!

---

### Post by nibal on 2013-03-18
> **eddiedee said:**
> Well, thanks to you both.

Running FixParts, p then s did the trick. Booted into Grub upon restart.

Thanks!

Could you please print the output of the final working fdisk?

TIA,
Nikos

---

