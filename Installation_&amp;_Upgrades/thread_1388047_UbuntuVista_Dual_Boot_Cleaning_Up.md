---
title: "Ubuntu/Vista Dual Boot Cleaning Up"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by itendo on 2010-01-22
Hello, I am requesting a broader list of steps to solve the following problem as I seem to keep missing a step here and there. So where and how do i begin?

Currently, after a handful of repairs and quick-fixes and emergency live-disk backups, I have two different Karmic installs alongside my Vista install (all other pc specs in profile). When i boot up, first GRUB loads and asks for how to boot, then if i select windows it will ask if i want to boot Vista or Linux (a dead link to a WUBI install i think; stupid wubi)). Fortunately, I have 2 1T hdds and a 320g, so storage has been a luxury that afforded me to leave this mess alone.

However, I need to clean up my machine tomorrow morning and am not sure A) what tools i should be using, or B) what set-up would be ideal. Standard resons of why the Linux/Vista setup, Vista for gaming and Linux for everything else.

I am looking to set up a permanent off-site backup system (a la Crash Plan) but dont want a ton of bloat to upload. Consequently, I want to set up a shared media partition (for use locally by both Karmic Ubuntu & Vista, and other networked machines (one Karmic, the other XP)), and an OS partition for each OS. The 320 gig hdd i want to use as little as possible as it is the oldest of the drives.

I want to have an additional partition for backing up images of each OS partition (see list).

I want the end result to boot into GRUB (a la gribbit) and pick boot options from there. I am okay with wiping the Linux installs and re-freshing, but i do not want to scare Vista and have it freak out (that happens enough on its own ).

Particular Concerns:
non-destructive resizing of the Vista partition 
boots to GRUB, not Vista 
when selecting Vista, doesnt re-ask boot option 
a media partition easily read/accessed/modified by Linux and windows (NTFS best?) 
as is its want, if the Vista install goes bad i would like to be able to drop an image in to replace it 

I am also capable of running the two 1Ts in a RAID and mirroring according to intel's specs for the DX58SO mobo i am running, but i have been unable to get it to work.

Partitions initially sound like:
1T hdd #1 - 
[LIST]
[*]50g Linux 
[*]150g(-ish) Vista 
[*]10g Linux swap 
[*]10g Vista swap 
[*]300g media 
[*](~440g leftover)
[/LIST]


1T hdd#2 - 
[LIST]
[*]350g OS backups (2 redundant, 1 step-back stable image for windows) 
[*]300g media (mirror backup) 
[*](~350g leftover)
[/LIST] 

320g hdd - 
[LIST]
[*]200g OS backups (1 redundant for linux, 1 step-back stable image for windows) 
[*](~120g leftover)
[/LIST] 

I will post menu.lst file what fdisk -l looks like shortly.

---

### Post by itendo on 2010-01-22
i'm probably doing something wrong here as /sda,b,c are not listed... nonetheless

from menu.lst:

```
# sample /boot/grub/menu.lst entry for memtest86
#
# This example assumes the contents of /boot is on the root partition.
# If your /boot is on its own partition, remove /boot from the 'kernel' line.

title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin

title  memtest86+ (serial console 115200)
root   (hd0,0)
kernel /boot/memtest86+.bin console=ttyS0,115200n8
```

for  fdisk -l:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed20049d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b2727b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      107077   860095971   83  Linux
/dev/sdb2          107078      121601   116664030    5  Extended
/dev/sdb5          120127      121601    11847906   82  Linux swap / Solaris
/dev/sdb6          107078      119590   100510609+  83  Linux
/dev/sdb7          119591      120126     4305388+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x150504d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux


```

---

