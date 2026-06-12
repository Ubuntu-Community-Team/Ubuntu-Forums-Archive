---
title: "Swap Partition/Swap File Not Being Created"
date: 2024-05-09
forum: Installation &amp; Upgrades
---

### Post by Rubi1200 on 2024-05-09
Was doing some testing recently with 3 different flavours:

Ubuntu 22.04
Ubuntu MATE 24.04
Xubuntu 22.04

I noticed that Ubuntu and Xubuntu did not create either swap partitions or swap files. MATE on the other hand did create a swap file.

For all 3, I choose Manual Partitioning.

The old laptop (legacy BIOS) has 8GB of installed RAM.

Curious to know why swap files were not created for 2 of them but yes for one.

Any thoughts on the matter?

---

### Post by gezzer2 on 2024-05-10
when i installed 24.04 it created a swap.img of 8.6GB on one system but no swap file/img on a second system.  i have no idea why.

on the 1st system i deleted the swap.img file and set up manually a 2GB swap file.
the 1st system is seeing the file and working OK with it.

on the 2nd system i reinstalled 22.04 as 24.04 wasn't running properly 22.04 created a swap file of 2GB
not much help, sorry ..

---

### Post by TheFu on 2024-05-10
I have 3 LXC 22.04 systems.  No physical system installs.  Linux containers use the swap from the host system ... which is 20.04

The host LXC system:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi        20Gi       2.6Gi       102Mi       8.1Gi        10Gi
Swap:         **4.1Gi       2.1Gi**       2.0Gi
```

```
$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/dm-5                               partition       4300796 2232356 -2

$ sudo lvs
  LV                VG             Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
swap              vg00           -wi-ao----    4.10g
...
```

LXC-1:
```
$ free -hm
               total        used        free      shared  buff/cache   available
Mem:            30Gi       108Mi        30Gi        33Mi        85Mi        30Gi
Swap:          **4.1Gi**          **0B**       4.1Gi
```

LXC-2:
```
$ free -mh
               total        used        free      shared  buff/cache   available
Mem:            30Gi       688Mi        29Gi        59Mi       215Mi        29Gi
Swap:          **4.1Gi          0B**       4.1Gi
```

LXC-3:
```
$ free -hm
               total        used        free      shared  buff/cache   available
Mem:            30Gi       229Mi        30Gi       7.0Mi       162Mi        30Gi
Swap:          **4.1Gi          0B**       4.1Gi
```

Interesting.
Here's a 20.04 VM (KVM/QEMU):
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:          964Mi       187Mi       116Mi       1.0Mi       660Mi       598Mi
Swap:         1.0Gi       5.0Mi       1.0Gi

$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/dm-1                               partition       1048572 5888    -2

$ lsblk 
NAME                TYPE FSTYPE       SIZE FSAVAIL FSUSE% LABEL MOUNTPOINT
vda                 disk             30.2G                      
&#9500;&#9472;vda1              part ext2         487M  229.2M    46%       /boot
&#9500;&#9472;vda2              part                1M                      
&#9492;&#9472;vda5              part LVM2_member 29.7G                      
  &#9500;&#9472;blog--vg-root   lvm  ext4        23.5G    8.1G    59%       /
  &#9492;&#9472;blog--vg-swap_1 lvm  swap           1G                      [SWAP]
```

VMs are just like physical systems.

That VM swap was manually sized.  I should probably make it 500MB. The Linux kernel behaves different when there's no swap and when there's a minimal swap, it enables some good features.

Ah ... I have a VPS with a 22.04 server install.  I didn't manually size anything.  Everything for the base OS install was created in the provider's panel.  I didn't customize the swap at all.
```
$ dft
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      ext4   24G   11G   13G  46% /

$ free -hm
               total        used        free      shared  buff/cache   available
Mem:           957Mi       255Mi       133Mi       1.0Mi       568Mi       538Mi
Swap:          2.3Gi          0B       2.3Gi

$ ll /swapfile 
-rw------- 1 root root 2516582400 Jun 26  2023 /swapfile
```

The swap is much larger than I need. I'm unhappy that a swapfile is used, but I guess that's the default. The VPS is just a VPN and reverse proxy server, so it doesn't need much CPU or storage.  I'm at a loss for how 11G is used. For a minimal Ubuntu server, I'd expect less than 7GB would be used.  There aren't any snaps on the box.  Just haproxy and wireguard with a basic Ubuntu 22.04 server.  Clearly the bloat is strong in 22.04.

Lubuntu 24.04 - wipe disk + minimal install:
```
$ free -hm
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       756Mi       2.5Gi        11Mi       886Mi       3.1Gi
Swap:          511Mi          0B       511Mi

$ ll /swapfile 
-rw------- 1 root root 536870912 May  1 10:37 /swapfile

$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME   TYPE FSTYPE SIZE FSAVAIL FSUSE% LABEL        M
sr0    rom           2K                             
vda    disk         25G                             
&#9492;&#9472;vda1 part ext4    25G   16.3G    28% lubuntu_2404 /
```
I don't remember being asked about the swapfile size.

---

### Post by Rubi1200 on 2024-05-10
Tested the following in VMs:

Lubuntu 24.04
Xubuntu 24.04

Chose the option to erase and use entire disk (no other special options chosen).

Lubuntu offered to create a swap file (as default) during the install.
Xubuntu did not make the same offer.

End result:
Lubuntu installed with a swap file
Xubuntu also created a swap file

Therefore, I am wondering if choosing Manual Installation in the installer results in no swap file being created? Is that by design perhaps? 

But then I do not have a good explanation for why Ubuntu MATE did create the swap file even though it was a manual install to the partition in question.

---

### Post by Rubi1200 on 2024-05-13
More tests:

Kubuntu 24.04 and Ubuntu 24.04: both created swap files. Kubuntu, like Lubuntu, offers the option during installation.

Since I am neither a developer nor a programmer I would not know where to start an investigation as to why some versions installed a swap file while others did not.

Therefore, even though the question is not really answered I am marking this thread as Solved.

Thanks to those who responded.

---

### Post by TheFu on 2024-05-13
I reinstalled Lubuntu 24.04 yesterday, paying attention more closely to the disk and swap options.
There was a toogle-box that offered 2 choices.
[LIST]
[*]Swapfile
[*]No swap
[/LIST]
this was a "normal install" without any custom partitioning.

As to how sizes are chosen, I haven't looked at the code, so I don't really know. 
In about 5 lines of code, for simple disk layouts, the size of swap could be smart enough.  As long as hibernation is allowed, the amount of RAM in a system is the amount of swap once the 4GB minimum is passed.  At a minimum, 4GB of swap makes sense unless someone has less than 20G of disk space. Then the trade-off between storage available and storage used for swap can be important.

---

