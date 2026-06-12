---
title: "ubuntu 16.04.6 - 300GB upgrade for sda - doesnt work"
date: 2021-06-17
forum: Installation &amp; Upgrades
---

### Post by goodfred on 2021-06-17
Hello everyone!

Usually. When I upgrade the hard disk space on a virtual machine on our ESXi I go to the virtual machine settings, upgrade the GB (for example here from 300GB to 600GB) and then I extend the LVM with "lvextend -l +100%FREE /dev/vs00034-vg/root" and "resize2fs /dev/vs00034-vg/root"
After that the partition is as big as it should be.

But this time following is happening: 
```
root@vs00034:~# lvextend -l +100%FREE /dev/vs00034-vg/root
  New size (74630 extents) matches existing size (74630 extents)
```

And logically the 2nd command outputs following:
```
root@vs00034:~# resize2fs /dev/vs00034-vg/rootresize2fs 1.42.13 (17-May-2015)
Das Dateisystem ist bereits 76421120 (4k) Blöcke lang. Nichts zu tun!
```

When I think back in my memory there was a column with "free space" on the output of "df -h" - but now I only see this:
```
root@vs00034:~# df -hFilesystem                    Size  Used Avail Use% Mounted on
udev                          3,9G     0  3,9G   0% /dev
tmpfs                         799M   17M  782M   3% /run
/dev/mapper/vs00034--vg-root  287G  191G   82G  71% /
tmpfs                         3,9G     0  3,9G   0% /dev/shm
tmpfs                         5,0M     0  5,0M   0% /run/lock
tmpfs                         3,9G     0  3,9G   0% /sys/fs/cgroup
/dev/sda1                     472M  105M  343M  24% /boot
tmpfs                         799M     0  799M   0% /run/user/1000
```

On the following output I have to say that I remember that when I used the command "sfdisk -l" before there wasnt 602GIB on /dev/sda (1st row in the following code)
```
root@vs00034:~# sfdisk -lDisk /dev/sda: 602 GiB, 646392578048 bytes, 1262485504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xbdef77f4


Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 629143551 628142082 299,5G  5 Extended
/dev/sda5       1001472 629143551 628142080 299,5G 8e Linux LVM




Disk /dev/mapper/vs00034--vg-root: 291,5 GiB, 313020907520 bytes, 611368960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/mapper/vs00034--vg-swap_1: 8 GiB, 8585740288 bytes, 16769024 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```
Maybe there are 602GIB because I have tried the command "growpart /dev/sda 5" which was executed sucesfully (he was showing the size before the command and the size after. I think it was double. But I dont have the output anymore)
After the "growpart /dev/sda 5" I wanted to try "resize2fs /dev/sda5" (the two commands belong together in the tutorial)
```
root@vs00034:~# resize2fs /dev/sda5resize2fs 1.42.13 (17-May-2015)
resize2fs: Device or resource busy beim Versuch, /dev/sda5 zu öffnen
Es kann kein gültiger Dateisystem-Superblock gefunden werden.
```
(this message occured before, too)

Here some additional informations
```
root@vs00034:~# pvdisplay  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               vs00034-vg
  PV Size               299,52 GiB / not usable 0
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              76677
  Free PE               0
  Allocated PE          76677
  PV UUID               xxxxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxxxx
```

```
root@vs00034:~# lvdisplay  --- Logical volume ---
  LV Path                /dev/vs00034-vg/root
  LV Name                root
  VG Name                vs00034-vg
  LV UUID                xxxxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxxxx
  LV Write Access        read/write
  LV Creation host, time vs00034, 2017-06-29 14:44:05 +0200
  LV Status              available
  # open                 1
  LV Size                291,52 GiB
  Current LE             74630
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0


  --- Logical volume ---
  LV Path                /dev/vs00034-vg/swap_1
  LV Name                swap_1
  VG Name                vs00034-vg
  LV UUID                xxxxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxxxx
  LV Write Access        read/write
  LV Creation host, time vs00034, 2017-06-29 14:44:05 +0200
  LV Status              available
  # open                 2
  LV Size                8,00 GiB
  Current LE             2047
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

```

```
root@vs00034:~# lvs  LV     VG         Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   vs00034-vg -wi-ao---- 291,52g
  swap_1 vs00034-vg -wi-ao----   8,00g
```

In the following section I am 100% sure that the output of sda was 300GB before! (maybe I can fix it myself but I will ask now) (could be because of the "growpart" command!)
```
root@vs00034:~# lsblkNAME                   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
fd0                      2:0    1     4K  0 disk
sda                      8:0    0   602G  0 disk
&#9500;&#9472;sda1                   8:1    0   487M  0 part /boot
&#9500;&#9472;sda2                   8:2    0     1K  0 part
&#9492;&#9472;sda5                   8:5    0 299,5G  0 part
  &#9500;&#9472;vs00034--vg-root   252:0    0 291,5G  0 lvm  /
  &#9492;&#9472;vs00034--vg-swap_1 252:1    0     8G  0 lvm  [SWAP]
sr0                     11:0    1  1024M  0 rom
```

```
root@vs00034:~# lvscan  ACTIVE            '/dev/vs00034-vg/root' [291,52 GiB] inherit
  ACTIVE            '/dev/vs00034-vg/swap_1' [8,00 GiB] inherit
```

Again in the following part! 602GB detected! (maybe the "growpart" command ...)
```
root@vs00034:~# lsblk -o NAME,UUID,FSTYPE,SIZE,LABEL,MOUNTPOINTNAME                   UUID                                   FSTYPE        SIZE LABEL MOUNTPOINT
fd0                                                                           4K
sda                                                                         602G
&#9500;&#9472;sda1 xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx ext2          487M       /boot
&#9500;&#9472;sda2                                                                        1K
&#9492;&#9472;sda5 xxxxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxxxx LVM2_member 299,5G
  &#9500;&#9472;vs00034--vg-root xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx ext4        291,5G       /
  &#9492;&#9472;vs00034--vg-swap_1 xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx swap            8G       [SWAP]
sr0                                                                        1024M
```

```
root@vs00034:~# vgs  VG         #PV #LV #SN Attr   VSize   VFree
  vs00034-vg   1   2   0 wz--n- 299,52g    0
```

```
root@vs00034:~# pvs  PV         VG         Fmt  Attr PSize   PFree
  /dev/sda5  vs00034-vg lvm2 a--  299,52g    0
```

Following rows I have on the output of "cfdisk"
```

Device - /dev/sda1              Size 487M        Type Linux
Device - /dev/sda2              Size 299,5G      Type Extended
Device -     ->/dev/sda5      Size 299,5G       Type Linux LVM
Free space                          Size 302G
```

I hope you can help me! I tried reboots of the machine with addind 1GB space before booting again. Did not work.
I tried several commands.
I tried several tutorials.
But I cant expand the LVM of the machine.

Im very very thankful for reading and for answers/tips/etc!
I wish a good left week and weekend!

goodfred

---

### Post by TheFu on 2021-06-17
Please edit the first post and change "quote" tags into "code" tags, so output lines up correctly. Difficult to read as it is.

Also, please update the post to clarify which commands are run on ESXi and which are run inside a guest VM.  Don't make us guess. Please. I haven't used ESXi in about a decade - we dropped VMware stuff due to VMware management poor communications on pricing changes that was drastically going to increase costs for us and our clients.  Moved to KVM + libvirt and never regretted doing that. KVM is 100x more flexible and definitely faster.

BTW, **lvextend -r** will resize the filesystem at the same time it resizes the LV.  1 command, 2 steps.

---

### Post by oldfred on 2021-06-17
I do not know LVM, but you do not have 600GB with MBR partitioning.
The extended partition sda2 is a container for logical partitions. 
Your sda5 then is one logical partition using the entire extended partition.
And you have two volumes / & swap which use the entire 300GB.

```
/dev/sda2 1001470 629143551 628142082 299,5G 5 Extended
/dev/sda5 1001472 629143551 628142080 [COLOR=#ff0000]299[/COLOR],5G 8e Linux LVM
/dev/mapper/vs00034--vg-root [COLOR=#ff0000]287G[/COLOR] 191G 82G 71% /
```

---

### Post by ajgreeny on 2021-06-17
I have changed your quote tags to code tags, but then just noticed that you are using 16.04 which has lost support unless you have signed up for extended support, though I am  not even sure if that is available for 16.04.

There is little point spending a lot of time and effort on a version which has no support, even if it's a VM so I strongly recommend that you upgrade to 20.04 which is supported for 4 years more.

---

### Post by MAFoElffen on 2021-06-17
On LVM2, think of PV, VG & LV as Russian Dolls (containers). The logical order for growing is PV, VG, LV, then grow the filesytem of the LV... (And reverse that order for Shrinking...)

[SIZE=3]_**Hint:**_[/SIZE] You started out by growing your VG by 100%, before and without growing your PV first, so the VG already hit it's limit. It did grow to 100% (with no error) logically, but look at your pvdisplay stat's. It's at 299,52 GiB. Nothing inside a container can grow any larger than the inside of that container. 

The PV Extents can still grow by about 300GiB.

---

### Post by TheFu on 2021-06-17
Multiple pickles in this setup.
16.04 is the first issue.  That must be solved. 
As part of that solution, do a fresh install of 20.04 and this time, choose GPT partitioning and create 3 partitions (assuming there isn't any UEFI booting)
[LIST=1]
[*]/boot - 500MB - 750MB
[*]LVM for everything else
[/LIST]

Inside the LVM area, 
[LIST=1]
[*]create a PV for all of it
[*]create a VG for all of the PV
[*]create LVs for 
[LIST]
[*]  / - 40G  If your OS takes more than 40G (really should fit into 10G on a server) something is very, very, very wrong.
[*]  /home - if less than 10G, just merge into /
[*]  swap - 4.1G, but on servers I strive to allocate sufficient RAM so that only a token swap, if any, is needed - EVER.
[*]  /where ever your huge data goes.  This LV should be sufficient for 3 months of use. 
[/LIST][/LIST]
It is very important to NOT allocate all the VG into LVs.  Leave as much free VG space as you can for other server needs (LV snapshots) and future growth.

There are reasons for everything I specified.  The order of partition creation matters, though not so much with GPT.
Once this is done, you can migrate your old data over.  This is an excellent opportunity to validate your DR plan.  A DR plan that needs exactly identical hardware will never actually work, BTW.

If you need more detailed validations, post these commands from inside the VM:
```
sudo fdisk -l
sudo pvs
sudo vgs
sudo lvs
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
All the other stuff is just junk to confuse people.  Also, UUIDs aren't private any more than IP addresses are private. Actually, UUIDs are so much completely unimportant as to not be worth dealing with - especially when LVM is used.  For LVM storage mounts, use the /dev/{vgname}/{lvname} links in the fstab.  Much easier to use, understand and provides actual useful information where it is needed.  UUIDs should only be used if the other alternative is a device like /dev/sda1 (never use that).

---

### Post by goodfred on 2021-06-18
1. all commands were run in the vm
2. thank you for changing the quotes to code
3. pvresize ```
root@vs00034:~# pvresize /dev/sda5  Physical volume "/dev/sda5" changed
  1 physical volume(s) resized / 0 physical volume(s) not resized
``` doesnt help
4. at the moment I cant upgrade the ubuntu to 20.04. I need a solution for now for upgrading the space to 600gb
5. I dont want to repartition. I think it should be good as it is (I only want to upgrade the space to 600gb)
6. ```
root@vs00034:~# fdisk -lDisk /dev/sda: 602 GiB, 646392578048 bytes, 1262485504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xbdef77f4


Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 629143551 628142082 299,5G  5 Extended
/dev/sda5       1001472 629143551 628142080 299,5G 8e Linux LVM




Disk /dev/mapper/vs00034--vg-root: 291,5 GiB, 313020907520 bytes, 611368960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/mapper/vs00034--vg-swap_1: 8 GiB, 8585740288 bytes, 16769024 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```
```
root@vs00034:~# pvs  PV         VG         Fmt  Attr PSize   PFree
  /dev/sda5  vs00034-vg lvm2 a--  299,52g    0
```
```
root@vs00034:~# vgs  VG         #PV #LV #SN Attr   VSize   VFree
  vs00034-vg   1   2   0 wz--n- 299,52g    0
```
```
root@vs00034:~# lvs  LV     VG         Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   vs00034-vg -wi-ao---- 291,52g
  swap_1 vs00034-vg -wi-ao----   8,00g
```
```
root@vs00034:~# lsblk -e 7 -o name,size,type,fstype,mountpointNAME                     SIZE TYPE FSTYPE      MOUNTPOINT
fd0                        4K disk
sda                      602G disk
&#9500;&#9472;sda1                   487M part ext2        /boot
&#9500;&#9472;sda2                     1K part
&#9492;&#9472;sda5                 299,5G part LVM2_member
  &#9500;&#9472;vs00034--vg-root   291,5G lvm  ext4        /
  &#9492;&#9472;vs00034--vg-swap_1     8G lvm  swap        [SWAP]
sr0                     1024M rom
```

I hope someone can help me to increase the LVM/SDA5 to 600GB ...

---

### Post by TheFu on 2021-06-18
Post #3 from oldfred above explains the issue.  It isn't LVM.  It is the current legacy MBR partitions causing the limitation.
[LIST]
[*]The PV must entirely be contained within sda5.
[*]sda5 must entirely be contained withing sda2.
[*]sda must entirely hold sda1, sda2, sda5.
[/LIST]

sda is ~ 600G now.
sda2 is still 300G.
sda5 (logical partition) cannot become larger than sda2 (Extended Primary partition).
This is how MBR partitioning works regardless of the OS. It has been this way since the "Logical Partition" hack was introduced in the 1980s.

There are 2 solutions.  I'm not sure the first can be done.

_a) _boot from alternate media - I'd use a desktop Ubuntu Mate "Try Ubuntu"/Install flash drive. This is mandatory because in-use partitions cannot be modified.  Using gparted, try to extend sda2 out to use the new storage. Hopefully it is AFTER all the current sda partitions. It looks that way.  After doing this, there should be empty space "to the right" of sda5.  Now, try to extend sda5 inside gparted to use the rest of the available storage inside sda2.  That will make the partition ~ 600G.  

Next, run **vgchange -ay** while still inside the "Try Ubuntu" environment. This will make all the LVM object available, so that pvresize can be performed.  This should automatically match the new size of the sda5 partition.

Next, you can do this next part from either inside the Try Ubuntu flash environment or boot the OS normally.  Run **vgchange -x** to allow the existing vg to be resized. Then vgextend. I've never used these commands in this way. Finally, run **lvextend -r** to resize the LV and extend the file system.  Please do not use all 300G of added storage. Leave some for LVM snapshots and to get a warning well before more storage is needed to allow 3+ months for budgets to be approved.

_Or  b) _ This is how I'd do it if I knew the underlying storage was actually coming from the same physical HDD or if all storage is RAID-protected **and** knew 100% that my backups were solid and had restores tested.  If backups were not tested. I'd stop and do that first.

Ok - in the extra storage, create a new partition. I think it will be sda3.  Mark it as LVM for the partition type.  Use vgextend to add this new partition to the existing VG.  Bob's your uncle.  Use **lvextend -r** to resize the LV and extend the file system in 1 command.

With "b", we have 2 PVs, 1 VG, and use the power of LVM to access that merged storage in a logical way. The VG will be concatenated and if anything fails in either partition, all data will be lost in both.  In the early 2000s, I lost 80% of my data doing something like this.  This is a serious warning.  I did something like this last year, but with 2 virtual HDDs (they were physically on the same SSD in reality) connected to a VM.  I use KVM, not ESXi, but inside the VM, I think the steps are the same.
[https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156](https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156) has the details. It has been running that way since last June. I'm lazy. Really should create a single, larger vHDD. I ran into the logical partition issue too. I'd been aware of the problem since the 1980s.

---

### Post by MAFoElffen on 2021-06-18
As I, TheFu and oldfred said... My thoughts: It is Russian Doll Syndrome.

 I'm thinking about this and mapping this out in my head...

The math on all the partitions on /dev/sda is that the existing partitions are taking up 299.987001GB of the 602GB VM disk, leaving around 302GB unallocated. 

Physical Volume Members (PV) = /dev/sda5 (one current PV Extent, which OP wants to add PV Extents to use around 601GB(?) *** See below.
Volume Group (VG) = /dev/vs00034-vg can grow 100% to  around 601GB 
Logical Volume (LV) Member = /dev/vs00034-vg/root can grow to around 593GB (though not recommended to add 100%)

Is that a sound solution? NO, not with the logic of what was suggested, in the how...
Are any of us recommending that you do it that way? No. But the concept model needs understanding and clearing up
Do you need to migrate to a supported LTS Version. Yes, definitely

Again, just thinking out loud:

You  know that you don't have to change anything on the existing PV member(s), to add "more" PV to LVM to add more space. Right? What you usually do is to add another LV type partition (whether another partition on another disk, or another partition on that same disk), Create it as a PV extent, to add to your VG (grows the VG), grow your LV within the VG, extend the filesystem within the LV... That's the logic.

Sometimes I have to visualize what that means...
```

[FONT=book antiqua][SIZE=3][FONT=century gothic]fdisk /dev/sda                                                          # create/add new partition to unallocated space as type "BE" 
                                                                               #    example that is created, let's say sda7...

pvcreate /dev/sda7                                                  # create new PV from it

lvmdiskscan -l                                                         # Scan for PV devices to verify it was created

vgextend vs00034-vg /dev/sda7                              # Add the PV Extent to grow the VG

lvm lvextend -l +80%FREE /dev/vs00034-vg/root  # Extend the LV

resize2fs -p /dev/mapper/vs00034--vg-root            # Extend the filesystem

df -H                                                                      # Verify it[/FONT][/SIZE]
[/FONT]
```
So modifying TheFu's logic from his last post, re-mentioning oldfred's comments...
> 
[LIST]
[*]The PV must entirely be contained within sda5.
[*]sda5 must entirely be contained within sda2.
[*]sda must entirely hold sda1, sda2, sda5.
[/LIST]

Evolves to:
> 
[LIST]
[*]The PV members of the VG Group are sda5 and sda7 (add more PV members)
[*]sda5 (logical) and sda7 (logical) must entirely be contained within sda2 (extended).
[*]sda must entirely hold sda1, sda2, sda5, sda7. (there is 302GB of unallocated space on that drive)
[/LIST]

Is that how I read that? Again, just "thinking out loud..." 

...The Russian Doll model.

---

