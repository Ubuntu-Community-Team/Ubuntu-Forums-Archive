---
title: "Ubuntu &amp; Kubuntu + Grub question"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by someusernoob on 2006-09-01
Ok, the situation:

```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

/dev/hda1               1        2611    20972826   83  Linux (Ubunut)
/dev/hda2            2612        2742     1052257+  82  Linux swap / Solaris
/dev/hda3            2743        9729    56123077+   5  Extended
/dev/hda5            2743        9729    56123046   83  Linux (/home of (Ubuntu)

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1044     8385898+  83  Linux (SLED)
/dev/hdb2            2612       14945    99072855    f  W95 Ext'd (LBA)
/dev/hdb3            1045        2611    12586927+  83  Linux (/home of SLED)
/dev/hdb5            2612       14945    99072823+  83  Linux (Data)

```

Grub is installed on hda, but also on hdb. If i boot i can choose from which disk i want to boot (with my bios by pressing F11, it gives me the bootoptions), and both disks show the same grub options, although the grubs are different from each other, i modifed them myself so they show the same things. Why? I didnt want to overwrite my first grub with another one, so it would keep my out of trouble.

On hda1 i got Ubuntu installed and on hdb1 i got SLED installed. I dont like SLED so i thought i give Kubuntu a shot and install it on that partition (i know i can do apt-get kubuntu-desktop - but i want to keep my Ubuntu clean since it is working very well and i want to start from scratch).

If i put in my Kubuntu CD now, and install it to hdb, it wont ask me where to put grub, so i expect it to overwrite the grub on hda, and leave the old one behind on hdb which wont work properly then. If i rip out hdb, hda wont boot then, since grub is missing the files from hdb. Right?

When i decide to install from the alternate version im afraid to mess things up because im not that experienced yet, and on hdb is also my Data partition, which is very important to me, so i really dont want to lose it.
With the alternate version i can install grub seperatly, right?

What is want is this:
- Leave the grub i have now untouched on hda, i can add the Kubuntu options manually, that is no problem.
- A new grub on hdb, so it will overwrite the old one and things will stay proper. I can aslo manually edit this one so i can choose to boot to Ubuntu instead of Kubuntu.

I hope it is clear and i hope someone can give some sort of advise of what to do. When i installed SLED i was able to choose where to put grub by GUI, so that wasnt so hard.

---

### Post by someusernoob on 2006-09-03
I found how to do it.

I installed Kubuntu to hdb (with the live cd). Once it was installed i booted into it, and typed 'sudo grub-install /dev/hdb'

After that i booted into Ubuntu and typed 'sudo grub-install /dev/hda'.

After that i edited my menu.lst files manually, and everything is working great now!! Exactly how i wanted it to be.

---

