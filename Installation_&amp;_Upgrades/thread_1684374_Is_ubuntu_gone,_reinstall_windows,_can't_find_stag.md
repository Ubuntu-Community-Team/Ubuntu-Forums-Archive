---
title: "Is ubuntu gone, reinstall windows, can't find stage1"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by Hybird on 2011-02-09
so i just want to know if my ubuntu is gone? I had ubuntu 9.04 and vista dual booting on separate partitions, and I did a clean install of windows from my recovery disks. At one point in the install it said all data on the hard drive will be removed. I wasn't sure if this meant it could delete my linux partition but i think it did.

Now I know there is the whole issue about re-installing windows causing the MBR to be over written, and hence grub to be removed, but I don't think that is the case here. 

So some info. I have a ubuntu 9.04 64 bit and 32 bit CD that I first installed ubuntu from. I am using that and selecting the "try ubuntu without installing" as i type and so I can use the terminal. Now the issue is this, i can get into the grub> command prompt from the terminal, but when i type

find /boot/grub/stage1

I get the message : Error 15 file not found

i tried guessing its on hd0,0 and running the command

root(hd0,0)

but i get the message : Error 27 unrecognized command

So my other diagnosis was to use the fdisk and see my partitions, so when i run 

sudo fdisk -l

i get back

device boot   start end blocks id system 
/dev/sda1 * 1 28864 231846880+ 7 HPFS/NTFS
/dev/sda2  28864 30401 12347392 7 HPFS/NTFS

So it almost seems as if there is no linux (ext3) partition??? But the weird thing is that when i used the ubuntu cd to install (started but didn't go through with it yet) you could see a 2.5 gig ubuntu partition in the partition editor. So is it gone or what? i know when I first installed it I used very little harddrive space and I don't think i created a swap.

Can someone verify that it is gone? Could it be I have to mount some sort of file system before I can see the partition in fdisk because I am running from the CD now and not actaully using my hard drive?

Any response would be greatly appreciated... i just want ubuntu back.

---

### Post by wilee-nilee on 2011-02-09
Look in gparted on the live cd, the fdisk shows only 2 NTFS.

9.04 is end of life now anyway.

---

### Post by Hybird on 2011-02-09
I know 9.04 is old but I had files on that partition that I wanted to place on an external partitioned harddrive so I could update to the newest ubuntu and put them back on.

I'm pretty sure gparted showed a ext3 partition, i'll have to check again tomorrow as it is 2:00am and i'm tired of reading through ways to get grub installed.

---

### Post by P4man on 2011-02-09
Its gone. The MBR might still have an entry for the linux partition, and that showed up in the installer, but it looks like windows overwrite the actual partition. Time for a fresh install I fear.

---

