---
title: "Partitioning"
date: 2020-11-12
forum: Installation &amp; Upgrades
---

### Post by sniper8752 on 2020-11-12
I recently installed Ubuntu Server 20.04.1 LTS.  I had it automatically partition my drive for me.  I noticed that my root directory shows the following:
```
[FONT=monospace][COLOR=#000000]Filesystem                         Size  Used Avail Use% Mounted on[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]/dev/mapper/ubuntu--vg-ubuntu--lv  196G  6.1G  180G   4% /[/COLOR]
[/FONT]
```

It is a 1 TB WD HD.  
Doing a fdisk on it:
```
[FONT=monospace][COLOR=#000000]**Device**[/COLOR][COLOR=#000000]**  Start**[/COLOR][COLOR=#000000]**       End**[/COLOR][COLOR=#000000]**   Sectors**[/COLOR][COLOR=#000000]** Size**[/COLOR][COLOR=#000000]**Type**[/COLOR]
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624    3147775    2097152    1G Linux filesystem
/dev/sda3  3147776 1953521663 1950373888  930G Linux filesystem
[/FONT]
```
Which present a few questions.  What is sda2?  I assume that my root partition is on sda3.  Why is it showing a size of only 196G available?  Does that have to do with LVM?  Will it automatically grow in size as need be?  Lastly, do I really only have available to me ~930GB out of the 1TB?

---

### Post by Impavidus on 2020-11-12
Your harddrive has about 1,000,000,000,000 bytes, a.k.a. 1TB or 930GiB, as 1GiB=1024×1024×1024 bytes. My guess is that your sda2 is a /boot partition. I think that's required when you use LVM, as the software needed for reading LVs must be loaded from a filesystem that doesn't use it.

---

### Post by TheFu on 2020-11-12
Yes, you are using LVM.

sda2 is the boot area. It  necesary because booting inside an LV isn't easy.

To see the LVM storage objects, use
sudo pvs
sudo vgs
sudo lvs

By default, LVs do not automatically grow.  There are dfferent sorts of LVs. sparse LVs can auto grow, but ths is an advanced, enterprise, feature.

The best practice for using LVM is to only allocate LV sizes for about 3 months at a time and to leave 10-20% unused  so snapshots are possible.
LVM doesn't use that much extra storage, perhaps 2k per LV at most.

Don't confuse 1000 and 1024 byte differences. Storage vendors use 1000 =  1 K, but the rest of the computing world uses 1024 = 1 KB.

---

### Post by ActionParsnip on 2020-11-12
What is the output of
```

sudo parted -l; mount | grep sd

```
Thanks

---

### Post by Dennis N on 2020-11-12
You can boot an OS in a logical volume without the separate boot partition if you are not using disk encryption.

The disk partitioning below has no boot partition. The OSes within the LVM partitions boot from grub without any problem. 
```
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  106MB  105MB  fat32              boot, esp
 2      106MB   262GB  262GB                     lvm
 3      262GB   388GB  126GB                     lvm
```

---

### Post by TheFu on 2020-11-12
> **Dennis N said:**
> You can boot an OS in a logical volume without the separate boot partition if you are not using disk encryption. 

Ah - I see in 20.04 they finally setup boot that way.
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   17G   12G  4.8G  70% /
/dev/mapper/vgubuntu--mate-home ext4   12G  7.6G  3.7G  68% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi

thefu@regulus:/boot$ df .
Filesystem                       Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root   17G   12G  4.8G  70% /

```
So /boot/ is part of the "root" LV.  The system above is using Legacy boot, not EFI, so they fact that there is a /boot/efi partition really doesn't make any sense to me.  /boot/grub/ is also part of the "root" LV.

Prior Ubuntu systems with LVM definitely setup a separate /boot/ partition. Here's a 16.04 box:
```
/boot/grub$ df .
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc2       237M  136M   89M  61% /boot

```

This command:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
is really useful for seeing storage disks, LVM, and mounts. It doesn't include all the /dev/loop.... stuff that is useless.

---

### Post by sniper8752 on 2020-11-12
> **TheFu said:**
> 
To see the LVM storage objects, use
sudo pvs
sudo vgs
sudo lvs

```
[FONT=monospace][COLOR=#000000]pvs[/COLOR]
  PV         VG        Fmt  Attr PSize    PFree    
  /dev/sda3  ubuntu-vg lvm2 a--  <930.01g <730.01g
[/FONT]
```
If below it is showing 200G in size for /, do I just need to expand the LVM?

> **TheFu said:**
> 
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
is really useful for seeing storage disks, LVM, and mounts. It doesn't include all the /dev/loop.... stuff that is useless.

```
[FONT=monospace][COLOR=#000000]lsblk -e 7 -o name,size,type,fstype,mountpoint[/COLOR]
NAME                        SIZE TYPE FSTYPE      MOUNTPOINT
sda                       931.5G disk              
&#9500;&#9472;sda1                      512M part vfat        /boot/efi
&#9500;&#9472;sda2                        1G part ext4        /boot
&#9492;&#9472;sda3                      930G part LVM2_member  
  &#9492;&#9472;ubuntu--vg-ubuntu--lv   200G lvm  ext4        /
sr0                        1024M rom    
[/FONT]
```
So to answer the boot question, there are 2 separate partitions for this?

---

### Post by TheFu on 2020-11-12
> **sniper8752 said:**
> ```
[FONT=monospace][COLOR=#000000]lsblk -e 7 -o name,size,type,fstype,mountpoint[/COLOR]
NAME                        SIZE TYPE FSTYPE      MOUNTPOINT
sda                       931.5G disk              
&#9500;&#9472;sda1                      512M part vfat        /boot/efi
&#9500;&#9472;sda2                        1G part ext4        /boot
&#9492;&#9472;sda3                      930G part LVM2_member  
  &#9492;&#9472;ubuntu--vg-ubuntu--lv   200G lvm  ext4        /
sr0                        1024M rom    
[/FONT]
```
So to answer the boot question, there are 2 separate partitions for this?

No.  there is just sda3 partition which is used as a PV IN LVM. Without seeing the other to LVM commands, how and what type of LVM containers cannot be stated with 100% accuracy.  It is likely you have 700+G available to be used by LVs however you like. That can be expanding, creating new, defined as a sparse LV or used for snapshots.

a) thank god they only allocated 200G for / - really 25-35G should be sufficient for the OS.
b) If it were me, I'd do a few things.

[LIST=1]
[*]Create a 4.1G swap LV. Enable it and remove the swap file.  IMHO, swap files are for noobs. Enable the new swap LV.
[*]Create a 50G LV for "home" and mount it on /home/
[*]Create a XXG LV for data stored outside the /home/.  To work around current snap problems, I'd mount this LV on /media/d/
[*]Reduce the current size of the "root" LV to 35G or so. Just depends on how full you've already got / after you move /home and the swap file out.
[/LIST]

But that is me.

If you just want help adding 50G to the current LV, the command is lvextend. Be certain to use  -r in the list of options so the file system gets expanded.  Please, please, please, don't allocate 100% of the storage.  Yes, you can, but you shouldn't. Increasing LVs is trivial - 5 seconds - while the system keeps running.  Reducing the size of an LV is a huge hassle.  Almost everything LVM related can be performed on a running system.  

What you decide is what matters.

Please post the ** sudo vgs** and **sudo lvs** command+output.

---

### Post by sniper8752 on 2020-11-12
> **TheFu said:**
> No.  there is just sda3 partition which is used as a PV IN LVM. Without seeing the other to LVM commands, how and what type of LVM containers cannot be stated with 100% accuracy.  It is likely you have 700+G available to be used by LVs however you like. That can be expanding, creating new, defined as a sparse LV or used for snapshots.

a) thank god they only allocated 200G for / - really 25-35G should be sufficient for the OS.
b) If it were me, I'd do a few things.

[LIST=1]
[*]Create a 4.1G swap LV. Enable it and remove the swap file.  IMHO, swap files are for noobs. Enable the new swap LV.
[*]Create a 50G LV for "home" and mount it on /home/
[*]Create a XXG LV for data stored outside the /home/.  To work around current snap problems, I'd mount this LV on /media/d/
[*]Reduce the current size of the "root" LV to 35G or so. Just depends on how full you've already got / after you move /home and the swap file out.
[/LIST]

But that is me.

If you just want help adding 50G to the current LV, the command is lvextend. Be certain to use  -r in the list of options so the file system gets expanded.  Please, please, please, don't allocate 100% of the storage.  Yes, you can, but you shouldn't. Increasing LVs is trivial - 5 seconds - while the system keeps running.  Reducing the size of an LV is a huge hassle.  Almost everything LVM related can be performed on a running system.  

What you decide is what matters.

Please post the ** sudo vgs** and **sudo lvs** command+output.

```
[FONT=monospace][COLOR=#000000]vgs[/COLOR]
  VG        #PV #LV #SN Attr   VSize    VFree    
  ubuntu-vg   1   1   0 wz--n- <930.01g <730.01g
[/FONT]
```

```
[FONT=monospace][COLOR=#000000]lvs[/COLOR]
  LV        VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 200.00g   
[/FONT]
```

I am confused by your previous post.  The lvs command output shows that sda{1,2} are both part of /boot.  Am I misunderstanding something?
```
[FONT=monospace][COLOR=#000000]&#9500;&#9472;sda1                      512M part vfat       ** /boot/efi**[/COLOR]
&#9500;&#9472;sda2                        1G part ext4        **/boot**
[/FONT]
```

---

### Post by TheFu on 2020-11-12
Only sda3 is using LVM. The other partitions are not using LVM.  Those other partitions are tiny, not worth any concern.

You can mount storage to any directory you like, so mounting /boot and /boot/efi is perfectly acceptable. Note how they have different file system types too?  EFI has to be FAT32 due to the standards.

The way to better understand LVM is to work through an LVM tutorial.  LVM hasn't changed in the way you will use it in 15+ yrs.  Any tutorial for any distro made in the last 15 years is fine. The commands are the same across all Linux distros that support LVM.  Do some reading. Learn how LVM is made of of PVs, VGs, and LVs.  LVs can generally be used in any way that a partition would be used.  When you create a file system, you create that on an LV (just like we would create a file system on a partition). It is just that LVs are 100x more flexible than partitions.

```
NAME                        SIZE TYPE FSTYPE      MOUNTPOINT
sda                       931.5G disk              
&#9500;&#9472;sda1                      512M part vfat        /boot/efi
&#9500;&#9472;sda2                        1G part ext4        /boot
&#9492;&#9472;sda3                      930G part LVM2_member  
  &#9492;&#9472;ubuntu--vg-ubuntu--lv   200G lvm  ext4        /
```
sda1 is a FAT32 partition.
sda2 is an ext4 partition.
sda3 is a partition using the rest of the disk. Inside it is a PV - LVM physical volume. 

Look up the relationship between PVs and VGs to understand how 1 or 50 physical partitions can be used to have 1-50 VGs - LVM Volume Groups. There are reasons to have 1 and there are reasons to have 2 or 5 or 50. Just depends.

Then look up the relationship between VGs and LVs.

LVM adds some complexity for the trade off of nearly infinite flexibility.

**Update**:  The main way people use LVM is to have multiple PVs added to a single VG, then have multiple LVs allocated from that VG.  For a single disk setup, it is basically, 
1 partition (PV) == 1 VG == 3+ LVs.  You'll likely never touch the PV or VG setup.  The only consideration for now is how many LVs you want and the 5 second command to extend those LVs once they are created.  

**About LVM and Backups (safe to ignore)**
When you setup backups, you'll want to use LVM snapshots to get clean backups. That is basically:
[LIST=1]
[*]Create a snapshot LV of another active LV
[*]Mount as read-only that snapshot LV someplace temporary
[*]Backup that temporary mounted storage however you like. The files there will not change, period.
[*]umount that temporary storage
[*]Destroy the snapshot LV so the system can use that space later.
[/LIST]

If you learn by watching videos, 
[LIST]
[*][https://www.youtube.com/watch?v=7JyKZg5zOq4](https://www.youtube.com/watch?v=7JyKZg5zOq4) : Beginning LVM
[*][https://www.youtube.com/watch?v=ng2mtVwoRtc](https://www.youtube.com/watch?v=ng2mtVwoRtc) : LVM and rdiff-backup 
[/LIST]
They are long winded and you'll want to skip 80+% of those videos, but for the 10 minutes that matter, the explanation is fine.

---

### Post by Dennis N on 2020-11-13
Good reads - links for LVM beginners:

An Ubuntu Guide to lvm:
[https://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](https://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

LVM Demystified by Shawn Powers
[http://www.linuxjournal.com/content/lvm-demystified](http://www.linuxjournal.com/content/lvm-demystified)

The Ubuntu guide (from around 2012-13) makes brief reference to a GUI tool that no longer exists, so you must stick to the terminal commands. Otherwise, it is accurate.

---

