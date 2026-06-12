---
title: "Ubuntu installer does not detect existing partitions and operating system (Win 7)"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by tamerucar on 2011-12-01
Hi,
I'm trying to install Ubuntu 11.10 but the installer does not detect my existing Windows 7 installation and NTFS partitions. The strange thing is when I boot Ubuntu in live mode, I can see and mount existing partitions from Home screen. What can cause this problem?


Output of sudo sfdisk -luS && sudo fdisk -l:

```
Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 125339129  125339067   7  HPFS/NTFS/exFAT
/dev/sda2     125352050 429340959  303988910   f  W95 Ext'd (LBA)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     125352113 312576704  187224592   7  HPFS/NTFS/exFAT

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdb2fdb2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   125339129    62669533+   7  HPFS/NTFS/exFAT
/dev/sda2       125352050   429340959   151994455    f  W95 Ext'd (LBA)
/dev/sda5       125352113   312576704    93612296    7  HPFS/NTFS/exFAT
```


I appreciate any help on this subject.

---

### Post by Mark Phelps on 2011-12-01
I'm guessing the installer is confused by the partition layout and rather than risk damaging the system, refuses to install.

You should boot into Win7, open up the Disk Management utility -- and see what it shows regarding the partitions.

---

### Post by tamerucar on 2011-12-01
Thanks for the reply.

I'm posting the output of Windows Disk Management utility as a screenshot. The free space (55,68GB) which is visible on the screenshot was meant for Ubuntu installation.

Any idea about my situation?

---

### Post by Mark Phelps on 2011-12-02
So apparently, Win7 Disk Management sees the disk differently, as well!

Suggest you download and burn the Partition Wizard Boot CD (Windows product), boot from it -- and see what it makes of the partitions.

Hopefully, it will either see the empty partitions and allow you to remove them, or it will allow you to repair the current partition setup.

---

### Post by oldfred on 2011-12-02
I prefer partitioning in advance and using the manual installer or Something Else. Then you have total control over sizes & locations of partitions. While the auto install tries to do a good job, it just is better to do it yourself.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

You seem to have 55GB free, I might suggest this all as logical partitions. You already have a d: drive for shared data.
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 20 GB Mountpoint /  logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by coffeecat on 2011-12-02
@tamerucar, I think I can see a bad entry in your partition table.

> **tamerucar said:**
> ```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total [COLOR="Red"]312581808[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdb2fdb2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   125339129    62669533+   7  HPFS/NTFS/exFAT
/dev/sda2       125352050   [COLOR="Red"]429340959[/COLOR]   151994455    f  W95 Ext'd (LBA)
/dev/sda5       125352113   312576704    93612296    7  HPFS/NTFS/exFAT
```

The end sector of the sda2 extended partition is showing as beyond the physical end of the hard drive - way beyond. I don't believe I've ever seen a figure like that. This would be why Gparted and the installer can't see your partitions, and I'm surprised that the Windows Disk Utility is not complaining.

The way to fix this is with fixparts:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Before you do, wait till someone else confirms what I'm seeing. Also - what did you use to create those partitions?

---

### Post by tamerucar on 2011-12-02
> **coffeecat said:**
> @tamerucar, I think I can see a bad entry in your partition table.



The end sector of the sda2 extended partition is showing as beyond the physical end of the hard drive - way beyond. I don't believe I've ever seen a figure like that. This would be why Gparted and the installer can't see your partitions, and I'm surprised that the Windows Disk Utility is not complaining.

The way to fix this is with fixparts:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Before you do, wait till someone else confirms what I'm seeing. Also - what did you use to create those partitions?
[B]
You are totally right.[/B]

Here is what I did about this problem:
- I downloaded the latest GParted live and booted with it.
- GParted also couldn't see the partitions. So I convinced that there is something wrong with my partition table.
- I booted again with Windows 7, opened Windows Disk Utility and tried to convert the free 55GB space into NTFS drive. It did convert but couldn't format the drive. And the size was about 2MB, not 55GB.
- I downloaded a free Windows disk partitioning tool to take a second chance. It showed me the same output as Windows Disk Utility. 
- So, I deleted the newly created problematic 2MB drive and shrunk my D drive by 30GB to gain free space for Ubuntu installation.
- After doing that, I booted with GParted again, and it showed me all of the partitions correctly!
- I didn't have enough time for Ubuntu installation so I didn't try to start the installer. But since GParted showed all of the partitions correcty, I think that Ubuntu installer will also do the same thing (which I'll try monday).

Thanks for all of the replies and interest.

---

### Post by coffeecat on 2011-12-02
@tamerucar, I'm glad that Gparted can now see your partitions but this does not necessarily mean that your partition table is yet in an ideal state. It would have been better to have used fixparts - there are both Linux and Windows versions available - which would have taken only seconds to repair this particular problem. Here is a link written by the author of fixparts - I post this only so that you can see how Gparted shows unallocated when there is just the sort of partition table irregularity that you had.

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

To see the current state of the partition table, please post the output of

```
sudo fdisk -l
```

That is, if you are running fdisk in Ubuntu 11.10. To get the output in sectors in an earlier version of Ubuntu, you need to run:

```
sudo fdisk -lu
```

We don't need the output of sfdisk - fdisk will do fine.

---

### Post by tamerucar on 2011-12-02
> **coffeecat said:**
> @tamerucar, I'm glad that Gparted can now see your partitions but this does not necessarily mean that your partition table is yet in an ideal state. It would have been better to have used fixparts - there are both Linux and Windows versions available - which would have taken only seconds to repair this particular problem. Here is a link written by the author of fixparts - I post this only so that you can see how Gparted shows unallocated when there is just the sort of partition table irregularity that you had.

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

To see the current state of the partition table, please post the output of

```
sudo fdisk -l
```

That is, if you are running fdisk in Ubuntu 11.10. To get the output in sectors in an earlier version of Ubuntu, you need to run:

```
sudo fdisk -lu
```

We don't need the output of sfdisk - fdisk will do fine.

Okay, I'll check it but I won't be near my computer during weekend. 
The first thing that I'll do on Monday will be posting the current state of the partition table.

---

### Post by tamerucar on 2011-12-05
> **coffeecat said:**
> 
To see the current state of the partition table, please post the output of

```
sudo fdisk -l
```


@coffeecat, the output of **sudo fdisk -l** is:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdb2fdb2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   125339129    62669533+   7  HPFS/NTFS/exFAT
/dev/sda2       125352050   248493419    61570685    f  W95 Ext'd (LBA)
/dev/sda5       125352113   248493419    61570653+   7  HPFS/NTFS/exFAT

```

---

### Post by coffeecat on 2011-12-05
> **tamerucar said:**
> @coffeecat, the output of **sudo fdisk -l** is:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdb2fdb2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   125339129    62669533+   7  HPFS/NTFS/exFAT
/dev/sda2       125352050   248493419    61570685    f  W95 Ext'd (LBA)
/dev/sda5       125352113   248493419    61570653+   7  HPFS/NTFS/exFAT

```

I can see no partition table irregularity now, but you have just under 33GB unallocated at the end of the drive. There are 312581808 sectors on the drive, but the end sector of sda2/sda5 is 248493419, which is equivalent to 32.8 GB.

---

### Post by tamerucar on 2011-12-05
> **coffeecat said:**
> I can see no partition table irregularity now, but you have just under 33GB unallocated at the end of the drive. There are 312581808 sectors on the drive, but the end sector of sda2/sda5 is 248493419, which is equivalent to 32.8 GB.

Thanks for the response coffeecat. I created that unallocated space for Ubuntu installer. Now, everything looks fine I think.

---

