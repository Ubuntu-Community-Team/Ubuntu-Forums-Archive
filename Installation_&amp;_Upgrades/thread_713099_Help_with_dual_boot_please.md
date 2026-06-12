---
title: "Help with dual boot please"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by tonman23 on 2008-03-02
OK, I'm no Linux expert. I just installed ubuntu on an extra IDE hard drive on my machine. I currently run xp on 4 sata hard drives setup with raid 0. 

summary: I have 5 HD's in my machine 4 sata drives with raid 0 running xp and one IDE running ubuntu. 

I am trying to find an easy way to dual boot without going into the bios and choosing the drive each time. I have gone through grub and am at a loss because Ubuntu doesn't see the windows installation. (im assuming it's because of the raid) Ubuntu sees them as separate drives. 

Any help would be much appreciated!

Tony

---

### Post by chewearn on 2008-03-03
I have no idea about raid, so can't help you there. (ideally, ubuntu would recognise the raid and detect windows accordingly).

A workaround will be to set your 1st boot device to CD-ROM; 2nd boot device to the raid.

When you want to boot into ubuntu, pop-in the ubuntu liveCD and select boot from local harddisk.  Presumably, it will find the ubuntu from your harddisk, and boot from there.  When you want to boot to Windows, remove the disc from CD-ROM; then, the BIOS should jump to the 2nd boot device, which is your raid.


It will be even better if you know how to put grub into a USB key.

---

### Post by tonman23 on 2008-03-06
not a bad idea i will try it out. 

Thanks for the reply!

---

### Post by gpilkay on 2008-03-06
You may also want to try setting up Ubuntu as Master with the main XP boot drive as Slave, then just load up Ubuntu, letting GRUB see the slave drive as an option.  Then afterwards. re-connect the other drives.

It's the RAID that throws me, I've never seen a  dual boot use one like that before, so I'm not honestly sure how that affects things.  My own desktop uses two IDE drives too, with the Ubuntu/M Windows/S configuration, but that's a lot simpler then yours, obviously...

---

