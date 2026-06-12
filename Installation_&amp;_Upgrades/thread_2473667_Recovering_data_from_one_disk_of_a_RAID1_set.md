---
title: "Recovering data from one disk of a RAID1 set"
date: 2022-04-09
forum: Installation &amp; Upgrades
---

### Post by paulkinz on 2022-04-09
My apologies if this is the wrong place...

All of what I've found concerning lvm is about creating new sets and adding, extending, etc., but I have a different question.

I have a Seagate SRN02D set up to be a 2-disk Raid1, and something took out not only one HDD, but also the box. So I'd like to be able to mount the one disk of the Raid1 set just by itself. I've been stumbling around the documentation but don't know enough about lvm to be able to get it mounted as just a plain HDD and haven't been able to find my particular need explained.

I did find a couple of interesting examine type commands and here's the output so it looks like this HDD is probably OK:

paulkinz:~$ sudo mdadm --examine /dev/sdb8
/dev/sdb8:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : 38ff4694:597660e1:ae71d4c0:a36009ba
           Name : vg:8
  Creation Time : Mon Oct  8 10:56:06 2018
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 3897192176 (1858.33 GiB 1995.36 GB)
     Array Size : 1948596088 (1858.33 GiB 1995.36 GB)
   Super Offset : 3897192432 sectors
   Unused Space : before=0 sectors, after=256 sectors
          State : clean
    Device UUID : f96fab0a:12f568a7:8c74d6c0:1dd3040b

    Update Time : Sun Apr  3 13:32:15 2022
       Checksum : c60284c7 - correct
         Events : 2214


   Device Role : Active device 1
   Array State : .A ('A' == active, '.' == missing, 'R' == replacing)

paulkinz:/dev$ sudo lvmdiskscan
[bunch of unrelated devices deleted here]
  /dev/md127 [       1.81 TiB] LVM physical volume

Secondly, what I plan to do is install a couple of new HDD's on the system and create a RAID1 set, what's the best way to move all the data from the recoverd HDD to the new RAID1 set? rsync?

And what's the best way to back up the new Raid1 set to a flash drive? Again rsync? Seems to take forever.

TIA!

---

### Post by paulkinz on 2022-04-10
Also I get warnings:
paulkinz:/dev$ sudo pvs
  WARNING: PV /dev/md127 in VG vg is using an old PV header, modify the VG to update.
  PV         VG Fmt  Attr PSize PFree
  /dev/md127 vg lvm2 a--  1.81t    0 
paulkinz:/dev$ sudo vgs
  WARNING: PV /dev/md127 in VG vg is using an old PV header, modify the VG to update.
  VG #PV #LV #SN Attr   VSize VFree
  vg   1   1   0 wz--n- 1.81t    0 

I've got files on there I'd like to get back so I'm hesitant to do the create lvm instructions
for fear of writing over something.

---

### Post by paulkinz on 2022-04-11
A Linux friend came up with the solution:

sudo modprobe dm-mod
sudo vgchange -ay
  1 logical volume(s) in volume group "vg" now active
sudo lvscan
  ACTIVE            '/dev/vg/lv' [1.81 TiB] inherit
sudo mount /dev/vg/lv /mnt/lastnas
ls /mnt/lastnas
afp_db        aquota.user  iscsi       rainbow   shares  torrent_dir
aquota.group  autoupdate   lost+found  reserved  tmp     var

and my files are deeper under the 'shares' directory.

---

### Post by ActionParsnip on 2022-04-14
Is there no backup of the data? If not, why not?

---

### Post by paulkinz on 2022-04-14
The data on the disk is already mostly backedup, but I do back that disk up, there are probably a few files on the disk that haven't been backed up yet. So yes, I could go to the backup if I had to, but I'd rather get the data off the disk.

---

### Post by TheFu on 2022-04-14
If you are using LVM for RAID, that's very different than using mdadm for RAID.  LVM can do all the RAID stuff without mdadm.

I'll let someone else help with mdadm recovery.  LVM has very little to do with this.
Also, I have never used dm-mod related to either LVM or mdadm, so if that is part of it, I have to ask - did you happen to use FakeRAID against advice?  FakeRAID has all the problems of HW-RAID, but none of the flexibility of SW-RAID. It should be avoided 99.9999% of the time.  FakeRAID is what motherboards offer and really cheap RAID HBAs - say anything less than $250.

If you are going to move data, I'd say to pick either mdadm with SW-RAID or LVM with SW-RAID and not mix the two. There's no need.  With LVM, you gain access to all the LVM commands that support moving PVs to new storage ... or adding 3rd and 4th mirrors to the RAID1 set then breaking the first 2 mirrors off, leaving just a single RAID1 on 2 LVs that are mirrored.  Very handy.

But some people are much more comfortable using mdadm.  They know to fail and remove a bad disk, clone a new one with the exact partition table (or at least the exact same partition size, tell mdadm the  new partition by adding it into the array and watch the sync progress. There are ways to make the sync slower or faster, depending on your needs.

---

### Post by paulkinz on 2022-04-14
I had two issues. Well, I have more issues than that, but let's not get personal. :-)
One was connecting to the single disk left from the Raid1 set from the Seagate NAS box that broke.
The other was how to create a new raid with new hard drives in my Ubuntu box.

For the first issue, I got it working as described above.

For the second issue...
I did get the new Raid1 set working from a how-to guide, it suggested using mdadm. Commands were pretty simple once I stumbled across what they are. :-) This is what I used:
[https://www.computernetworkingnotes.com/linux-tutorials/how-to-configure-raid-in-linux-step-by-step-guide.html](https://www.computernetworkingnotes.com/linux-tutorials/how-to-configure-raid-in-linux-step-by-step-guide.html)

To answer your questions...
1) FakeRAID - never heard of it. As I said, I had a Seagate Raid box that broke (lost its mind and thought I had factory reset it but I hadn't) and one of the two disks broke too.

I don't know enough about either mdadm or lvm to understand your question. It sounds like what you're saying is that they both can do the same thing, but I should use one or the other, not both, is that correct? The howto said mdadm so that's what I used. I had tried to use lvm before that because that's what another source suggested but didn't get to having it work.

Is there any benefit of one over the other?
If I created the Raid1 set using mdadm, can lvm then operate on them and manage them too?

---

### Post by TheFu on 2022-04-14
mdadm is for RAID and only RAID.

LVM is for enterprise volume management, which happens to include SW-RAID.  For a while 20 yrs ago, using both mdadm and LVM was recommended.  The LVM team took the SW-RAID code from mdadm and integrated it while keeping the great added features that LVM has always provided.

LVM does LVM things only. It doesn't talk to mdadm or manage mdadm RAID sets.

You know, if you don't really know much about either, perhaps using ZFS would be better?  ZFS for data is really where the world is headed and supports a next-gen, rock solid, RAID and validated data methodology.  If you don't really know mdadm nor LVM, I'd say to not bother and learn ZFS for any new storage.

And I have so many 'issues' it isn't funny. Really, it is kinda sad. ;(

---

### Post by paulkinz on 2022-04-15
Thank you TheFu, I'd never heard of ZFS.

However, I can't say I *learned* mdadm or lvm, I stumbled thru the howto manuals and got both issues to work, the first with lvm and the second with mdadm so I hesitate to touch either because they're working. :-)

Is it possible to use ZFS to manage either issue now that they're both working? Or would I have to remove or back out mdadm and lvm to use ZFS?

---

### Post by TheFu on 2022-04-15
[https://en.wikipedia.org/wiki/Zfs](https://en.wikipedia.org/wiki/Zfs)

---

### Post by paulkinz on 2022-04-15
Sounds like ZFS can do all kinds of neat stuff, but I don't have the bandwidth to really learn it. That'll have to come someday.

But I'm wondering whether ZFS can take over a Raid created by mdadm, or whether I'd have to un-Raid it and recreate it with zfs?

I'm hesitant to do anything given that it's working.

---

### Post by TheFu on 2022-04-15
RAID is not RAID, is not RAID, is not RAID.  Every software solution, every hardware solution is incompatible with the others.  Even if 2 different HW-RAID cards are used, the underlying data on the disks is incompatible.

>  But I'm wondering whether ZFS can take over a Raid created by mdadm, or whether I'd have to un-Raid it and recreate it with zfs?
No.

ZFS can do RAID, but only in the ZFS way.
mdadm can do RAID, but only in the mdadm way.
LVM can do RAID, but only in the LVM way.

---

### Post by paulkinz on 2022-04-15
Thanks, that directly answers my question, everything else I found dances around it.

---

