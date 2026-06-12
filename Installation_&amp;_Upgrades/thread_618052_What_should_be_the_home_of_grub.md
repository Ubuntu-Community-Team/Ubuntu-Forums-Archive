---
title: "What should be the home of grub?"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by Ruuud on 2007-11-20
I am installing Ubuntu following the instructions on [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto). All works fine up to the point where I need to install/configure grub ([https://help.ubuntu.com/community/FakeRaidHowto#head-6c76652aaaf5e147adaaca8b0547d2dd06f2c5ce](https://help.ubuntu.com/community/FakeRaidHowto#head-6c76652aaaf5e147adaaca8b0547d2dd06f2c5ce)).

Since this is my third try I should try to get some help I thought and my first question is why I have to make a home this way: "mkdir /boot/grub"? /boot is not on my hard drves for as far as I know because up to know that has been /target/boot. 
This is my first question...

Second question I have is with configuring grub which also doesn't work out really nice; I cannot figure out which partition number to choose to boot from. I tried (hd0,0) and (hd0,5) but (perhaps I did the thing in my first question wrong) but neither seems to really make a difference. When I update-grub I just get errors that grub can't be found...

Below I printed some information about my raid drive. I would be really happy if someone can verify the numbers I used to configure grub
```
root@ubuntu:/# dmraid -ay
RAID set "isw_efggddfdh_RAID_Volume1" already active
RAID set "isw_efggddfdh_RAID_Volume11" already active
RAID set "isw_efggddfdh_RAID_Volume15" already active
RAID set "isw_efggddfdh_RAID_Volume16" already active
root@ubuntu:/# dmraid -r
/dev/sda: isw, "isw_efggddfdh", GROUP, ok, 240121726 sectors, data@ 0
/dev/sdb: isw, "isw_efggddfdh", GROUP, ok, 240121726 sectors, data@ 0
root@ubuntu:/# dmraid -s
*** Group superset isw_efggddfdh
--> Active Subset
name   : isw_efggddfdh_RAID_Volume1
size   : 480242176
stride : 256
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0
root@ubuntu:/# fdisk /dev/mapper/isw_efggddfdh_RAID_Volume1

The number of cylinders for this disk is set to 29893.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/mapper/isw_efggddfdh_RAID_Volume1: 245.8 GB, 245883994112 bytes
255 heads, 63 sectors/track, 29893 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                                  Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_efggddfdh_RAID_Volume1p1   *           1        1275    10241406   83  Linux
/dev/mapper/isw_efggddfdh_RAID_Volume1p2            1276       29893   229874085    f  W95 Ext'd (LBA)
/dev/mapper/isw_efggddfdh_RAID_Volume1p5            1276        1403     1028128+  82  Linux swap / Solaris
/dev/mapper/isw_efggddfdh_RAID_Volume1p6            1404       29893   228845893+  83  Linux

```
I used Volume11 where the fakehowto said via_hfciifae5 (/boot)
I used Volume15 where the fakehowto said via_hfciifae6 (swap)
I used Volume16 where the fakehowto said via_hfciifae7 (/)

I set up grub like this:
device (hd0) /dev/mapper/isw_efggddfdh_RAID_Volume1
root (hd0,5) # which I believe to be the second partition on the extended drive (volume 16)

But I also tried (hd0,0), should I also try (hd0,2)? Which is what the FakeRaidHowto suggests, but I read the documentation of grub too and it make me think I should use partition number 5

Thanks for any information!

---

### Post by Ruuud on 2007-11-20
Can't believe my question is that difficult? I have the installation here, which I left on the stage before setting up grub to go to work, and I want to do it right this time because I was unable to fix it before when I got it wrong. So I hope someone can give me a quick reply or else I'll start experimenting again but that takes me several hours per guess to go through the entire howto :( (And that's why I am asking)

So can anybody answer my questions? Thanks!

---

### Post by Ruuud on 2007-11-20
Ok, forget about question one! I figured out that when did sudo chroot /target I started working from that point. So /boot is really /target/boot.

Now it is the grub question which is the last hurdle before I can start using my first linux install ever :-k

---

