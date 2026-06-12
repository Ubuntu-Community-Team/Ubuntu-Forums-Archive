---
title: "Locked Partitions"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by puner on 2007-12-26
I booted my computer today and found out that 

"No operating system installed"

I went into the bios, and it seems that my OS HD is not being detected but my media on IS.

I want to remove Ubuntu off the OS HD and see if Windows Xp is detected and boots.

I cannot remove it with GParted because it seems that swap and extended is locked.

[[IMG]http://img201.imageshack.us/img201/7929/screenshotdevsdagpartedjd2.th.png[/IMG]](http://img201.imageshack.us/my.php?image=screenshotdevsdagpartedjd2.png)

---

### Post by taurus on 2007-12-26
You cannot remove a partition while you are using it.  To remove Ubuntu, you need to boot from the LiveCD and use gparted from the LiveCD to remove both /dev/sda3 & /dev/sda5.  Then, you would have a dead GRUB so you need to recover your MBR so you can boot from windows.  Hope you have windows disc handy or you can use this.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Craigus on 2007-12-26
Are you running gparted from a livecd ?

You should be able to right click on the locked partitions and select [COLOR="RoyalBlue"]unmount[/COLOR] .

---

### Post by puner on 2007-12-26
I can only delete /dev/sda3 by right clicking and "delete"

But the only options I see for /dev/sda5 are swapoff, manage flags, and information.

---

### Post by Craigus on 2007-12-26
swapoff will unmount the swap partition - sorry, should have been more specific.

---

### Post by taurus on 2007-12-26
/dev/sda5 is your swap so if you want to unmount it, you have to run the swapoff.

---

### Post by puner on 2007-12-26
alright so I removed ext3, extended, and swap. Basically that space is unallocated. 

Now, the problem is my bios doesnt see the IDE drive that has Windows xp installed on it (this happened after "fixmbr").

[img]http://imagenerd.com/uploads/dsc08362hyIx.jpg[/img]

Although as you saw, GParted saw it.

---

### Post by taurus on 2007-12-26
Don't you have only one harddrive, /dev/sda?  On that harddrive, you have XP, Vista, and used to be Ubuntu.

---

### Post by Craigus on 2007-12-26
Wouldn't you have to go into IDE configuration in BIOS to see the IDE drive ? I assume that the SATA drive is your media storage.

---

### Post by puner on 2007-12-26
1xSATA 320GB = Storage
1xIDE 120GB = Just WinXp (No vista or ubuntu)

---

### Post by Craigus on 2007-12-26
Thought so, so - what happens if you select IDE configuration in BIOS ?

---

