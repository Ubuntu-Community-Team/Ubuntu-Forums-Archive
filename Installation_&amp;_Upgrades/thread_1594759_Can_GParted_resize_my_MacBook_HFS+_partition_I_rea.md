---
title: "Can GParted resize my MacBook HFS+ partition? I *really* don't want to screw it up!"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by youbuntu on 2010-10-12
Hi guys. So I have a MacBook which I am dual-booting with Mint 9 x86 - I wish to triple boot using 10.10 i386 as my third OS - can Gparted **reliably** resize my Snow Leopard partition WITHOUT screwing it up?

I know EVERYTHING is a risk, but I just want to know the level of risk involved. Gparted never failed me before... but I would like to know ASAP!

Thank you chappies & chapesses :D

---

### Post by srs5694 on 2010-10-12
I'd recommend using Apple's Disk Utility rather than GParted for this job. However you do it, *back up first!*

---

### Post by gunnar123 on 2011-01-06
GParted came to my rescue now.  I have a WD external drive with a NFS partition filled with Windows files. And I wanted to use half of the free drive space to back up my MacBook Pro.
The Mac tools did not seem to want to help with preserving the NFS stuff but only offered options to wipe the drive clean and write new partitions. But I know GParted is cool. 
So I fired up a small Eee 4G computer where I have managed to install Ubuntu 10 on its minuscule 4GB SSD drive and ran GParted from there with that USB drive attached to the Eee.
In preparation for having GParted support HFS+ file system you need to install the "hfsprogs" package on ubuntu; easy command line job:
sudo apt-get install hfsprogs
Then fire up GParted:
sudo gparted

I was able to resize the NFS partition to get 300 GB free space. Then I created a new partition there in HFS+ format. That was it. When plugging the USB drive back into a MacBook Pro USB jack I was greeted with a question if I wanted to use this drive with Time Machine.  Yes, and all works.

So GParted is a cool swiss army knife useful for solving stuff others have not catered for, for a reason or another.

---

### Post by space_agent on 2011-06-12
Thanks gunnar123 ! I am just now facing a very similar situation. Thanks for your post. I think what makes ubuntu superior to mac or you name it, is its community, so thanks again pal.

---

### Post by shearn89 on 2011-08-12
> **gunnar123 said:**
> ... In preparation for having GParted support HFS+ file system you need to install the "hfsprogs" package on ubuntu...

You're a hero. Just what I was looking for!

EDIT: You may need to reformat the drive anyway, as HFS+ doesn't play nice with MBR...

---

