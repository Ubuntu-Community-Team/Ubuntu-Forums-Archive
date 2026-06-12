---
title: "Telling Ubuntu setup to use free space"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by BattleGnome on 2005-11-08
I have set aside 30 gigs of free space unpartitioned on my hdd for ubuntu, how do I tell ubunto to use this free space during setup?

---

### Post by adwait on 2005-11-08
Its been a long time since I ran the Ubuntu installation........but there's an option for automatic partitioning.

---

### Post by az on 2005-11-08
It should default to asking you if you want to use it.  If not, it will display the partition table and all you would have to do is select the free space and go on to guided partitioning, from where it will do the rest...

---

### Post by Arktis on 2005-11-08
Actually, isn't the default to erase and automaticly repartition the entire disk for ubuntu only?  But yes, when you choose to manually edit the partition table, you can just select an option to automaticly partition the free space.

---

### Post by az on 2005-11-08
[QUOTE=Arktis]Actually, isn't the default to erase and automaticly repartition the entire disk for ubuntu only?  But yes, when you choose to manually edit the partition table, you can just select an option to automaticly partition the free space.[/QUOTE]
No.  In Warty and Hoary, if there is free space, it will default to asking to use it.  If there is not, it will offer to blow away the first disk.

In Breezy, I have not tried it with a prepartitioned disk, but I would image it is the same.  If there is no free space and it can partitio n the drive, it will offer to do so for you.

---

### Post by rpimn on 2005-11-08
[QUOTE=azz]No.  In Warty and Hoary, if there is free space, it will default to asking to use it.  If there is not, it will offer to blow away the first disk.

In Breezy, I have not tried it with a prepartitioned disk, but I would image it is the same.  If there is no free space and it can partitio n the drive, it will offer to do so for you.[/QUOTE]

Hi Azz,

I just want to make sure that I understand your description correctly.
I am quite nervous for the partition section.
I have 160 GB HD as master (the first hard drive) and another 160 GB HD as slave (the second hard drive).
I already saved all my data in the second hard drive, and intend to replace my Redhat 9 (in the first hard drive) with Breezy Badger.

According to your experience, if there is no free space, Ubuntu will erase all the existing partition in the first hard drive only. Is it correct ?
I am quite nervous about my data in the second hard drive.
Any help and suggestions would be greatly appreciated.
Thanks.

---

### Post by az on 2005-11-08
[QUOTE=rpimn]According to your experience, if there is no free space, Ubuntu will erase all the existing partition in the first hard drive only. Is it correct ?[/QUOTE]

No.  It (Breezy) will offer to free up some space from a partition.  That means that it will take a partition and shrink it, liberating some free space (up to you to decide how much) for it to install Ubuntu.  Anyway, before it does anything, it asks you.

You can also pick the "Manualy edit partition table" and make it do exactly what you want.

It will ask you a final question before it actually does it, so you can boot the installer and take a look at what it offers.  You can quit and come back to ask questions here...

---

### Post by shade11 on 2005-11-08
If you already Partitioned the space. (Resize the partition) Then you should select the partition and press enter. Then click on "Partition the Free Space" (That is what i think it is called.)

---

