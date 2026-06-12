---
title: "Lucid/Hardy triple boot query"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by paulb42 on 2010-05-28
I'm currently running Hardy and XP in a dual boot setup. I want to install Lucid but don't want to overwrite my working Hardy partition and am worried by the number of reported problems with Grub2.

XP is currently taking up all of my first hard drive.
Second hard drive is : Hardy, then swap, then separate /home.

After a bit of research, does this sound like a good plan ? ...
- Use gparted from the Live CD to shrink my Windows partition (then make sure XP still boots OK )
- Create a new partition after XP on drive 1
- Install Lucid in this new partition, using Advanced option, and tell it use my existing swap and home partitions on drive 2 (with no format, of course)
- Write Grub to this new partition
- Boot Hardy, and edit grub manually ( or use StartUp Manager, will it detect Lucid and add it as an option ? )
- Reboot and get options for Hardy, XP, and Lucid.

Does that sound correct, especially the Grub bits? When I'm happy that Lucid is OK I'll probably install Grub from it to the MBR.

Cheers
Paul

---

### Post by darkod on 2010-05-28
Personally, I don't have any idea why are you worried about grub2, you didn't specify anything in detail.

I was using grub2 (1.97) with Karmic, and now using 1.98 with Lucid, and haven't noticed any particular issues.

The most threads here lately about grub2 are for not being able to boot windows after upgrading from Karmic to Lucid. In the upgrade process, there is a window asking you where to install grub2, offering all disks and (unfortunately) partitions as choice. Users who don't know, or simply don't pay attention to what is a disk and what a partition, select all check boxes, thus installing grub2 also to their windows partition.

Of course, chainloading to the partition doesn't work after that.

Don't confuse that with grub2 "problems". :)

Of course there are other issues for some users, but I haven't actually seen any real, constant grub2 problem.

After that introduction, back to your plan. :)
If you want to keep Hardy grub1 in charge, it's best not to install grub2 when installing Lucid at all. In the last screen of the installer just click on the Advanced button and tell it not to install a bootloader.
Don't forget that grub can boot linux, so no need to put grub2 on the Lucid partition because you only need that if chainloading from windows bootloader.
However, if you use this, I think you will have to make your Lucid root ext3 because grub1 ext4 support was added only in 9.04. And you do need to create entry for Lucid in menu.lst because grub1 doesn't do that automatically.

Also, sharing /home like that between two versions might occasionally create hiccups with some packages settings which are kept in your home folder. The packages will be different version.

That's all I can think of right now.

---

### Post by kansasnoob on 2010-05-28
> **paulb42 said:**
> I'm currently running Hardy and XP in a dual boot setup. I want to install Lucid but don't want to overwrite my working Hardy partition and am worried by the number of reported problems with Grub2.

XP is currently taking up all of my first hard drive.
Second hard drive is : Hardy, then swap, then separate /home.

After a bit of research, does this sound like a good plan ? ...
- Use gparted from the Live CD to shrink my Windows partition (then make sure XP still boots OK )
- Create a new partition after XP on drive 1
- Install Lucid in this new partition, using Advanced option, and tell it use my existing swap and home partitions on drive 2 (with no format, of course)
- Write Grub to this new partition
- Boot Hardy, and edit grub manually ( or use StartUp Manager, will it detect Lucid and add it as an option ? )
- Reboot and get options for Hardy, XP, and Lucid.

Does that sound correct, especially the Grub bits? When I'm happy that Lucid is OK I'll probably install Grub from it to the MBR.

Cheers
Paul

The first thing I can think of is that Lucid and Hardy will not share a /home nicely unless you use different user names and it could still get messy. There have simply been too many changes in gconf and gnome (just to name two).

As far as:

> Write Grub to this new partition

I wouldn't. Grub 2 is persnickety about being installed to partitions. If you want to use your existing grub when you get to the final screen click on the Advanced button in the lower right hand corner:

[http://members.iinet.net.au/%7Eherman546/p22/035.png](http://members.iinet.net.au/%7Eherman546/p22/035.png)

Then just choose not to install grub anywhere: 

[http://members.iinet.net.au/%7Eherman546/p22/037.png](http://members.iinet.net.au/%7Eherman546/p22/037.png)

Notice there in the upper left hand there's a box you can uncheck "Install boot loader"?

That should leave Hardy's grub totally alone. but you will have to manually create a boot entry in Hardy's /boot/grub/menu.lst.

I would also remind you to defrag Windows XP before resizing :)

You could just try Lucid in a small 8 to 10 GB partition for a few weeks until you're sure it works well for you, then do a fresh install over Hardy being certain NOT to format /home.

Screenshots courtesy of:

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by paulb42 on 2010-05-28
Thanks for the advice Darko.
Maybe I should just bite the bullet and install Grub2 while I'm at it. There are plenty of solutions posted in these forums if it goes wrong. :)
Hopefully I'll be posting a successful install after the long weekend

---

### Post by kansasnoob on 2010-05-28
@ Darkod,

> However, if you use this, I think you will have to make your Lucid root ext3 because grub1 ext4 support was added only in 9.04. And you do need to create entry for Lucid in menu.lst because grub1 doesn't do that automatically.

Great point! I'd forgotten that. Hardy's grub won't boot ext4! I know that from trial and error.

---

### Post by paulb42 on 2010-05-28
Thanks also to Kansasnoob, sounds like a plan.. ( and yes, I've already defragged Windows :) )

---

