---
title: "Partitions"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by pokethesmot on 2010-09-17
i just used dd code to move my 200gb hard drive onto my 1tb and it put a 200gb partition on the 1tb i downloaded gparted but i don't see how to make the 200gb stretch all the way 2 tb it wont let me make it any bigger so can some one pleas help me do this

---

### Post by sikander3786 on 2010-09-17
Which filesystem on your drive? Also see the following link.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by pokethesmot on 2010-09-17
> **sikander3786 said:**
> Which filesystem on your drive? Also see the following link.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)


what do you mean i have ubuntu and then some really small partition but i don't know what it is and ten all the free space

---

### Post by Rubi1200 on 2010-09-17
Could you use GParted on the LiveCD and take a screenshot for us please?

Also, from the terminal post the output of ```
sudo fdisk -l
```

Thanks.

---

### Post by pokethesmot on 2010-09-17
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3eec3eec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23330   187398193+  83  Linux
/dev/sda2           23331       24321     7960207+   5  Extended
/dev/sda3           24322      121602   781403136   83  Linux
/dev/sda5           23331       24321     7960176   82  Linux swap / Solaris

and hold on let me get the screen shot

---

### Post by pokethesmot on 2010-09-17
i took the screen shot and it said it saved it in root but i cant open the root folder it keeps saying permission denied

---

### Post by sikander3786 on 2010-09-17
Use

```

gksu nautilus

```

Navigate to the folder and copy the screenshot from there. **Be careful.**

---

### Post by Rubi1200 on 2010-09-17
According to fdisk you seem to have 2 Linux installations.

When you take a screenshot do you have the option to save it to the Desktop?

---

### Post by pokethesmot on 2010-09-17
no it just auto saves it and it didnt even save it right i guess cuz there is no screen shot

---

### Post by Rubi1200 on 2010-09-17
If you are on the LiveCD now could you please post the output of the bootscript linked to at the bottom of my post.

---

### Post by pokethesmot on 2010-09-17
im on ubuntu right now but hold on im downloading a new installation of ubuntu so if this dont work ima just reinstall it i gues or does anyone know how to coppy just my installation of ubuntu like all my settings and then save them to a disk and put it on like that

---

### Post by uRock on 2010-09-17
You may have to copy to and equal sized partition, then grow it to fill the hard drive.

---

### Post by pokethesmot on 2010-09-17
> **uRock said:**
> You may have to copy to and equal sized partition, then grow it to fill the hard drive.

what do you mean

---

### Post by uRock on 2010-09-17
I reread your original post. Is that partition mounted while trying to grow it?

---

### Post by pokethesmot on 2010-09-17
> **uRock said:**
> I reread your original post. Is that partition mounted while trying to grow it?

i dont think it is cuz i was running off the live cd of gparted...could it have still been mounted

---

### Post by srs5694 on 2010-09-17
> **pokethesmot said:**
> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3eec3eec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23330   187398193+  83  Linux
/dev/sda2           23331       24321     7960207+   5  Extended
/dev/sda3           24322      121602   781403136   83  Linux
/dev/sda5           23331       24321     7960176   82  Linux swap / Solaris

and hold on let me get the screen shot

The screen shot is unnecessary. Don't bother reinstalling. The problem is that you've got a swap partition, and its enclosing extended partition, sitting between the main Linux installation and the rest of the drive. There are several possible solutions. The simplest is probably this:


[list=1]
[*]Boot an emergency disc, such as an Ubuntu Live CD, [System Rescue CD,](http://www.sysresccd.org/) or [PartedMagic.](http://partedmagic.com)
[*]Launch GParted (aka GNOME Partition Manager).
[*]If you see a little key icon next to the swap partition, right-click the partition and select the option to deactivate swap space. (I don't recall the exact terminology it uses.)
[*]Use GParted to increase the size of the extended partition (/dev/sda2) so that it extends to the end of the disk.
[*]Use GParted to move the swap partition (/dev/sda5) to the end of the extended partition.
[*]Use GParted to shrink the extended partition (/dev/sda2), this time compressing it down from its start point.
[*]Use GParted to increase the size of the main Linux installation (/dev/sda1) so it covers the remaining free space.
[*]If you haven't done so between individual steps, click the green check mark or select Edit -> Apply All Operations from the menu bar. It will take a while (perhaps a few minutes) to do everything.
[*]Reboot.
[/list]


Alternatively, instead of moving swap space and resizing partitions, you could create a new partition and use it as your /home partition; see [here](http://www.ibm.com/developerworks/library/l-partplan.html) for a somewhat old but still relevant description of how to do this. If you do this, you might want to *shrink* your /dev/sda1 partition, since 200GB is too big for the root (/) partition on most desktop computers if they've got separate /home partitions. Using a separate /home partition has the advantage of protecting your user files from damage and enabling you to completely wipe your installation and re-install to a blank partition without losing your user data. Converting from a system without a separate /home partition to one with a separate /home partition takes some extra work, though, since you'll need to copy files around, edit /etc/fstab, and so on.

You may also want to check my two-part series on partition resizing on IBM developerWorks: [Part 1](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html) and [Part 2.](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

---

