---
title: "Help please - resize partition instructions"
date: 2022-05-06
forum: Installation &amp; Upgrades
---

### Post by urbanbox on 2022-05-06
Hi there,

I'm trying to figure out the correct process to allocate an additional 20GB to the Ubuntu boot partition that is running within VirtualBox.
Currently getting error that var has run out of space, so resized disk in virtual box, booted into liveCD Gparted, However, reading various guides, the names of partitions don't match, and i am stumped.

See attached image of disk/partition within Gparted

[IMG]https://imgur.com/a/Le6DwQm[/IMG]
[https://imgur.com/a/Le6DwQm]("https://imgur.com/a/Le6DwQm")

- /dev/sda1   grub2 core.img   1.00mb
- /dev/dsa2 ext4 1.00GiB
- /dev/sda3 lvm2 pv ubuntu-vg 19.00GiB
- unallocated 20.80Gib

Thank you in advance.

Dingofandango

---

### Post by yancek on 2022-05-06
>   /dev/sda3 lvm2 pv ubuntu-vg 19.00GiB

The above line which you posted shows that you have an LVM install and the method for extending/modifying partitions is not the standard.  If you go to the View tab in GParted and select filesystem support you will see that it supports lvm.  I've never used LVM so can't help but you could try an online search for modifying an LVM partition.

---

### Post by TheFu on 2022-05-06
No images please.  I can't select/paste answers.  

Please post the command + output from these things:
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
$ sudo pvs
$ sudo vgs
$ sudo lvs
```
Then an answer, which may be very simple, can be provided.  I use LVM and if the partitions are setup in a good way, extending a partition could be easy.

BTW, if you use a swap file, the quickest answer might be to stop doing that, delete the file and use an LVM-LV instead for swap.
```
$ ls -lh /swap* 
```
will let us know about the swap file.

---

### Post by ActionParsnip on 2022-05-06
LVM is great. Joining in the foray

---

### Post by urbanbox on 2022-05-06
> **TheFu said:**
>  

Please post the command + output from these things:
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
$ sudo pvs
$ sudo vgs
$ sudo lvs
```
Then an answer, which may be very simple, can be provided.  I use LVM and if the partitions are setup in a good way, extending a partition could be easy.

BTW, if you use a swap file, the quickest answer might be to stop doing that, delete the file and use an LVM-LV instead for swap.
```
$ ls -lh /swap* 
```
will let us know about the swap file.

Hi TheFu,

Thanks for your assistance,

the output of ```
df -hT -x squashfs -x tmpfs -x devtmpfs
``` is as follows:

Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv ext4   19G   19G     0 100% /
/dev/sda2                         ext4  976M  320M  590M  36% /boot


then in order as you have listed them

NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
sda                       40.8G disk
&#9500;&#9472;sda1                       1M part
&#9500;&#9472;sda2                       1G part ext4        /boot
&#9492;&#9472;sda3                      19G part LVM2_member
  &#9492;&#9472;ubuntu--vg-ubuntu--lv   19G lvm  ext4        /
sr0                       1024M rom

-----------------------------------

  PV         VG        Fmt  Attr PSize   PFree
  /dev/sda3  ubuntu-vg lvm2 a--  <19.00g    0

-----------------------------------

  VG        #PV #LV #SN Attr   VSize   VFree
  ubuntu-vg   1   1   0 wz--n- <19.00g    0

-----------------------------------

  LV        VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- <19.00g  

------------------------------------

-rw------- 1 root root 3.8G Feb 13 08:24 /swap.img

------------------------------------

Thank you.

---

### Post by TheFu on 2022-05-06
Please edit the post above and wrap the CLI/shell/terminal output in _forum code tags_. This makes everything line up - otherwise misinterpretation is likely. That could be bad.  
[Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains _code tags_.

From here, it looks like you have a 40.8G disk with about 22G used.  The problem is how sda3 is laid out.  If it was to the end of the disk and the PV and VG were also using the remainder of the that space, then extended the LV would be trivial.

It isn't all bad news.  Thanks to LVM, you can create another partition in the free space, extend the VG into that, then extend the LV - all while the system keeps running - but this is dependent on the partitioning tool allowing another partition to be created while the other partitions on the disk aren't touched. I think that's allowed.

Without LVM, none of this would be possible and I'd just say to create a new partition, format it ext4, and move everything from /home into the new partition.  Honestly, that is just as valid a solution as the LVM stuff.

But you should know that 20.04 and later will quickly use 40G of storage.  I know this from first hand knowledge.  I had to nearly double the space my desktop had after a few months running 20.04. Here's the output from the commands I asked for above:
```
$ dft
Filesystem                 Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--root ext4   19G   14G  4.3G  77% /
/dev/vda1                  vfat  511M  7.1M  504M   2% /boot/efi
/dev/mapper/vgubuntu--home ext4   12G  7.2G  4.1G  64% /home

$ sudo pvs
  PV         VG       Fmt  Attr PSize   PFree
  /dev/vda5  vgubuntu lvm2 a--  <29.50g    0    
  /dev/vdb1  vgubuntu lvm2 a--  <10.00g 4.39g

$ sudo vgs
  VG        #PV #LV #SN Attr   VSize  VFree
  vgubuntu   2   3   0 wz--n- 39.49g 4.39g

$ sudo lvs
  LV     VG        Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home   vgubuntu -wi-ao---- 12.00g                                           
  root   vgubuntu -wi-ao---- 19.00g                                           
  swap_1 vgubuntu -wi-ao----  4.10g                                           

$ lsblkt
NAME                  SIZE TYPE FSTYPE      MOUNTPOINT
vda                    30G disk     
&#9500;&#9472;vda1                512M part vfat        /boot/efi
&#9500;&#9472;vda2                  1K part     
&#9492;&#9472;vda5               29.5G part LVM2_member     
  &#9500;&#9472;vgubuntu--root     19G lvm  ext4        /
  &#9500;&#9472;vgubuntu--swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu--home     12G lvm  ext4        /home
vdb                    10G disk     
&#9492;&#9472;vdb1                 10G part LVM2_member     
  &#9492;&#9472;vgubuntu--root     19G lvm  ext4        /

```
Basically, I added a new disk (vdb) where you need to add a new partition.  See how both disks have vgubuntu--root and the mountpoint is /?  That was just so I didn't need to move /usr/ to the new partition.  It is a judgement call - either using LVM or just creating a new ext4 partition and moving all of /home/ over to it, then mounting that through the fstab is fine.

There isn't any GUI.
If you choose not to use LVM in the new area, you'll have to boot from a "Try Ubuntu" flash drive to make the changes and move the files - which is actually something you'll want to have around anyway for emergencies.

There's a how to move /home to a new disk how-to guide.  [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)  In reality, it is harder to explain than to actually do it.  In the end, the new partition needs to be mounted via the fstab so the directories are all the same as before, with the same owner, group, permissions, acls and xattrs.  For a single user (1 userid) system, this is really easy. If you have more than 1 userid under /home/ ... then use rsync -avz with sudo to retain all the permissions.

---

### Post by urbanbox on 2022-05-10
Hi Thefu,

Thank you for your reply and help thus far.

So, would best practice be creating a new partition/disk for home/ and migrating existing home/ to that partition? therefor in the future if partition needs to be resized it is a streamlined process?

Presently the server is hosting a single docker container which is run out of home/userxxx/dockerfiles . Everything was fine, no issues, until 7 days ago when it ran out of space.

I don't know why Ubuntu is becoming so bloated, and the only reason I am using it is because it works with a specific docker package where other linux distros do not work.

Thank you.
Kind regards,

---

### Post by TheFu on 2022-05-10
Please edit the post above with the output from the commands requested.  Those are the where the lack of columns can cause confusion. If you look at my post, you'll see that I show the exact command AND the output from it in a single code block. That means that others can do it and compare their output with mine, seeing differences (there will always be differences).


"Best Practice" is an ideal.  When using partitions for file system management, the flexibility for the future becomes less when compared to what is possible using volume managers like LVM.

Once a partition is sized, resizing is only possible with many caveats, mainly that there is empty space immediately following the current partition and it cannot be a "logical partition" inside another Primary (aka Extended) partition.  LVM removes these limitations, but introduces some complexities.  LVM provides 50 other things that straight file-system on partitions cannot do.

I don't use docker. I'm not a fan of their tech, but I do use Linux Containers.

So, is having a separate partition for /home a best practice?  Yes, sorta.  I think the real best practice is to use LVM and setup separate partitions for the OS, logs, linux containers, virtual machines, swap AND home directories.  Above, I tried to show the simplest example of LVM with separate LVM-LVs for home, root, and swap. Further, that example shows how I extended the / (LVM-volume group) across 2 storage devices (which could have been different partitions on a single device) so that the root directory could be expanded.

BTW, 
```
/home/
```
and 
```
home/
```
aren't the same. Please be careful mixing absolute paths and relative paths, since bad data can lead to terrible outcomes.

If you don't feel like LVM is easy enough to be used, then you don't have much choice. Partitions are all that you have and you'll need to do things the hard way. I posted a link to the Ubuntu guide for moving /home to a different partition. Follow that.

Or, you can do a fresh install of the OS and check the "Use LVM" box during installation. Adding LVM after the fact isn't really very useful for the "best practice" purpose.

---

### Post by ActionParsnip on 2022-05-11
What is the output of
```

df -h; echo; mount

```
Thanks

---

### Post by TheFu on 2022-05-11
> **ActionParsnip said:**
> What is the output of
```

df -h; echo; mount

```
Thanks

The df is already posted above along with the other needed information. It is just not formatted to be readable - missing code tags. Adding code tags will help greatly.

I could be wrong, but sda3 is 19G and the LVM VG is 19G too. The problem is that sda3 needs to be resized, so the VG can be resized, then the LVs inside can be either resized or some new ones created.  The total disk appears to be 40G, so at least 10-15G more should be available.  It is a little confusing how this could happen. Defaults for setting up LVM at install wouldn't do this.  Someone manually setting things up who knows LVM wouldn't do this.  I don't know.

Of course, there are other options - nearly infinite. Another partition could be made in the free space, then set to be LVM, then the VG could be extended into that new partition, then either new LVs or the current LV could be created/extended. This would be a bit messy looking, but since it is 1 disk, the risks in doing it are small.  Using LVM to cross multiple disks in a non-RAID way can be dangerous if 1 of the disks has a failure.  All data can be lost on both disks.  But with just 1 physical drive, a failure that impacts 1 will likely impact the other regardless, so why not?  Whatever makes the most sense.

And with the free space after sda3, a new partition could be created, then used for /home/.  Just because it can be done, doesn't make it a good idea.  The system already has LVM. Why not avail ourselves of that flexibility and use it to create a home LV that can be mounted for /home/ or other needs?   The main question really is where is all the storage being used on the system?  For example, there's a 3.8G swapfile.  So, moving that from /swap.file to a new LV would be any easy choice for me. I'm not a fan of swap files.

Is there any plan to add more storage to the system?  I know I bought a used 250G desktop drive a few years ago for $9.  If that's an option, having LVM can make the migration to new storage really easy thanks to the **pvmove** command.  I've used this myself. Didn't even need to modify the fstab after the move.

---

### Post by ActionParsnip on 2022-05-11
Seems you have 4.4Gb free in the volume group. You can add a couple of gigabytes to the LVM disk
[https://www.linuxtechi.com/extend-lvm-partitions/](https://www.linuxtechi.com/extend-lvm-partitions/)

You will need to use resize2fs to extend the partition on the LVM disk.

Be sure to run a full backup before you start in case of catastrophe

---

### Post by TheFu on 2022-05-11
> **ActionParsnip said:**
> Seems you have 4.4Gb free in the volume group. You can add a couple of gigabytes to the LVM disk
[https://www.linuxtechi.com/extend-lvm-partitions/](https://www.linuxtechi.com/extend-lvm-partitions/)

You will need to use resize2fs to extend the partition on the LVM disk.

Be sure to run a full backup before you start in case of catastrophe

I think you saw my post with my LVM data, not the OPs. Sorry for the confusion.

Also, resize2fs isn't needed if the **lvextend -r** is used.  Once the VG has some free space, extending is extremely low risk. I don't both with any fresh backups, since this is a 5second effort to extend.  But the OP can't do that because the VG is using all the space in the current partition already.

---

