---
title: "Problems after compressing XP drive"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by SalishSea on 2009-11-13
As soon as I pressed the button I knew I just bought myself grief, but oh the clarity of hindsite.

I was a bit pressed for space on the XP side of my XP/Ubuntu 9.04 dual install, so I stupidly compressed the XP drive using XP's compression tool.  Dumb idea.  Now I see the Ubuntu partition on boot in GRUB, but no joy once I try to boot to the Ubuntu drive.

I figured the Ubuntu partition was hosed, but... when I tried to do a new install with 9.10, it asked me if I wanted to uninstall 9.04.  So, is there any hope of recovering a bootable Ubuntu image off this drive? Might I just uncompress some file or files?

Thanks!

---

### Post by SalishSea on 2009-11-13
I should have noted that the dual install was a WUBI install.

---

### Post by darkod on 2009-11-13
I am new to Ubuntu too, so if I am wrong someone with more experience please correct me.
I am seeing plenty of people here confusing wubi with Ubuntu installation. As far as I know, wubi is just to test ubuntu, it "installs" it sort of like a virtual machine, it does not change partitions on your hdd, it will add an entry for ubuntu on your standard windows bootloader and in your windows drive it will just create a folder for ubuntu in which it virtually works.

So, unless you have some very important data, forget about saving the wubi installation. It is not an installation.

Next, you mention grub. Are you sure you have grub at all? Wubi would have added ubuntu entry in your XP bootloader.

One of the reasons it doesn't work is that the wubi-ubuntu was actually in a folder in your xp drive. Remember when installin wubi it is asking on which drive to put itself? Look around and you should have folder called ubuntu (I think). Also, in your Add/Remove programs in XP control panel you should have Ubuntu installed just like regular windows app. So when you shrinked XP most probably it shrinked the space reserved for wubi too and corrupted something.

If you want a proper 9.10 or 9.04 installation I recommend:
1. Go in Add/Remove programs and remove Ubuntu (wubi). That will also free the space reserved by it. Don't just delete the folder, remove it like any windows app.
2. Sit down and do the math, make a partition plan. How large you need your XP system partition, do you want another NTFS data partition, and how much space you want for Ubuntu.
3. If you need to make changes to the XP partitions, boot with ubuntu CD and selectoption Try Ubuntu. That will boot so called live cd oe live environment. It doesn't even mount the hard drive so you can use Gparted (System -> Administration) to change partitions. BE CAREFUL: Any partition changes shrink/expand involve some level of risk for the data on the disk. Have everything backed up.
4. When you are happy with partitions and have enough free space for ubuntu, boot with ubuntu CD, select option Install Ubuntu, when it asks select Manual Partitioning and create /, swap and if you want /home in your empty space. And that's it.

Enjoy your Ubuntu. :)

---

### Post by SalishSea on 2009-11-13
Yes, GRUB sees the ubuntu boot record and offers as a choice at boot (of course).
So, whether or not it is a legitimate partition is one question. If it is an XP folder as you suggest, then does anyone know if there is a means to uncompress that folder?

Thanks,

---

