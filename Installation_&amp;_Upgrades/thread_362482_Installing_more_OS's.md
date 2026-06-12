---
title: "Installing more OS's"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by geek_Man on 2007-02-15
Hi, I wanted to install Xubuntu along side Ubuntu to test it out. But when I got to the repartitioning part it said that I couldn't mount Xubuntu to "/" ('cause *Ubuntu* was already mounted to that). So I tried mounting to "/Xubuntu", but it didn't like that. I don't know what to mount it as so that there is no conflict. Am I just confused here, or what? Thanks in advance!

---

### Post by cidhus on 2007-02-15
It sounds like you are either
 1) trying to install over Ubuntu's / partition, or
 2) trying to call both partition's /

#1 is unsettling unless you intend to wipe out your Ubuntu OS. #2 is impossible. Each partition must have a unique mount point. During the install, name the ubuntu partitions
that you don't intend to replace as /ubuntu/<oldname>. For eg., name Ubuntu's /
partition /ubuntu. Ubuntu's bin partition as /ubuntu/bin. Then you can name the one's
for Xubuntu as you would have them. However, you can share the /home partition and
swap, though it's easier to use a different user name on different OS.

Just my personal thoughts, while on work break. /herbc

---

### Post by towsonu2003 on 2007-02-15
```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` will install xubuntu for you... you don't need two different installations for that. xubuntu = base installation of ubuntu + xfce tools (so if you do the above commands, you will have ubuntu base + gnome + xfce... 

as per partitioning (just in case), here is an example to how to do it:

suppose you have the following partitions (and you basically need empty partitions...):
/dev/hda1 [Ubuntu / ]
/dev/hda2 [Ubuntu Home]
/dev/hda3 [swap]
/dev/hda4 [empty]
/dev/hda5 [empty]

when you install a new distro, you will use the empty partitions and leave others (except swap) alone. So, it will be:

/dev/hda1 [**don't touch during installation** Ubuntu / ]
/dev/hda2 [**don't touch during installation** Ubuntu Home]
/dev/hda3 [**set as swap in both distros**]
/dev/hda4 [set as **New distro /** ]
/dev/hda5 [set as **New Distro Home**]

You could share the Home partition btw distros as well -I personally don't like that. 

If you have only the following, you don't have space to install another OS:
/dev/hda1 [Ubuntu / ]
/dev/hda2 [Ubuntu Home]
/dev/hda3 [swap]


there is the issue of MBR as well... it's simple if you start from the right place. have a look at this crazy post to get an idea on that: [http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

hope this helps

---

### Post by geek_Man on 2007-02-15
Well, obviously I can't name both of them as "/", but I was wondering what *can* mount Xubuntu as. I was doing this for testing, so I kinda want two installs. It's so I can see how Xubuntu runs, not just Ubuntu with Xfce.

---

### Post by towsonu2003 on 2007-02-15
I'm confused about the problem you're experiencing. could you post the output of sudo fdisk -l along with what OS is **currently** installed in which partition? thanks :)

---

### Post by IgnorantGuru on 2007-02-15
Yes, they are both named (mounted to) /  - they must be.  But not on the same OS.  (A mount point is used the OS - it is not stored in the partition table.)

For example, from the Ubuntu installation, Ubuntu is mounted to / and the Xub installation might be mounted to /mnt/xubuntu.

From the xubuntu installation, xubuntu is mounted to / and the Ubuntu installation might be mounted to /mnt/ubuntu.

:shock:

---

### Post by rsambuca on 2007-02-15
Geek Man,  sorry to say it but you are a bit confused.  If you want two separate OS installs, they have to be on separate partitions, and each will have it's own root directory.  Both will be simply installed to "/", but be on separate partitions.  The grub boot loader will then ask you whether you want to boot into ubuntu or Xubuntu.

And by the way, xubuntu IS just ubuntu with the xfce desktop.  If you simply follow towsonu2003's instructions to install the xubuntu desktop, you won't have to worry about any of the partitioning, and you will be able to select ubuntu (gnome) or xubuntu (Xfce) in the sessions menu upon login.  They are just different desktop environments.  You can also install the kubuntu desktop, e17 desktops and you do not have to have separate partitions.

---

### Post by geek_Man on 2007-02-15
Well, sudo fdisk -l isn't the problem, but here it is anyway. ```

Disk /dev/hda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         665     5027368+   b  W95 FAT32
/dev/hda2   *         666       25840   190323000    7  HPFS/NTFS

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       21889   175823361    7  HPFS/NTFS
/dev/sda2           21890       29722    62918572+  83  Linux
/dev/sda3           29723       29853     1052257+  82  Linux swap / Solaris
/dev/sda4           29854       32464    20972857+  83  Linux

```

I made sda4 for testing and when I try to reformat it as "/" it gives me an error.

rsambuca, I know Xubuntu is just Ubuntu with Xfce, but I want to install it anyway.

---

### Post by towsonu2003 on 2007-02-15
> **geek_Man said:**
> 
I made sda4 for testing and when I try to reformat it as "/" it gives me an error.

rsambuca, I know Xubuntu is just Ubuntu with Xfce, but I want to install it anyway.
ok you seem to be doing everything ok. try checking the md5sum of the iso you downloaded. if it's fine, I remember seeing a bug in launchpad (probably [this one]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/67130")) somehow similar to this. try the alternative installation cd (the one that is not a liveCD)... [here's a link]("http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/6.10/release/")

by the way, the alternative cd will give you a choice on where to install grub, so check the link I provided above about grub to make things easier from the beginning :)

---

### Post by geek_Man on 2007-02-15
Thanks guys, I was just playing around with it and it was turning out to be too much trouble, so I'll just leave it alone.

---

### Post by timcredible on 2007-02-15
i dual-boot pclos and ubuntu.  when running ubuntu, i mount the pclos partition to /pclos, when i run pclos, i mount the ubuntu partition to /ubuntu.  they both mount their own partitions to /.  here's my fstab when running ubuntu (snipped), hope it helps understand it:

```

/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2
/dev/hda2       /pclos          ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0

```

also, you can only have 4 primary partitions.

also, here's the fstab when running pclos:

```

/dev/hda1 /ubuntu ext3 defaults 1 2
/dev/hda2 / ext3 defaults 1 1
/dev/hda3 swap swap defaults 0 0
/dev/hda4 /home ext3 defaults 1 2

```

---

