---
title: "Changing from Xubuntu to the regular ubuntu and resizing partions"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by lsolesen on 2008-11-18
I grew tired of my xubuntu. It worked great but recently it has done some quirks and decided to give the regular ubuntu a whirl instead.

However, I am unsure what the best way to do that is. I used to use Windows, and it is necessary for me to keep the current windows setup when working with photographs.

So basically, I need to know two things.

1) How do I create partions in a clever way?
2) How do I do the actual upgrade without loosing for instance drivers and stuff for the wireless network card etc and the graphics driver and the ability to use two screens. (which took me a long time to setup in xubuntu)

I am on a IBS/Lenovo T60. Right now my disks are setup as the following. One partion for the windows system (/dev/sda2) and another disk for data (/dev/sda3). /dev/sda2 is somewhat bigger than needed, and the /dev/sda5 (which I am guessing is the linux disk) is getting too small. I think /dev/sda1 is a recovery partion, so I can reinstall windows if I would like that. I am not sure what /dev/sda4 is.

I have thought of moving the /home/ directory to a new partion, but dont know if that is a good solution.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         848     6809600   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         848        9730    71339008    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            9730       17471    62178711    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           17471       19457    15959160    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           17471       19368    15240928+  83  Linux
/dev/sda6           19368       19457      718168+  82  Linux swap / Solaris

I need some advice as how to do this? Hope someone is up for the task of explaining stuff to a guy who wants a lot, but understands so little.

---

### Post by snowpine on 2008-11-18
Ubuntu is just a different windows manager (gnome instead of xfce) over the same "guts" as Xubuntu. This command will install it on top of your existing Xubuntu install:

```
sudo aptitude install ubuntu-desktop
```

All of your documents and settings will be unchanged. (Though you might want to backup important data first; never a bad idea!)

Log out, then from the login screen, choose Sessions then Gnome and you'll be in Ubuntu!

---

### Post by lsolesen on 2008-11-18
Ah, neat. What about the partion stuff? Can you help with that?

---

### Post by OrangeCrate on 2008-11-18
> **lsolesen said:**
> Ah, neat. What about the partion stuff? Can you help with that?

No additional partitioning is needed. As said, you'll choose either Gnome or Xfce for your current session, under options, on your log-in screen.

---

### Post by snowpine on 2008-11-18
To re-partition, you should boot from an Ubuntu Live CD (or any other Live CD with gparted) and run the gparted partition editor (under the system menu). I advise against adding/deleting partitions unless you're 100% confident you know what you're doing. :)

It looks like your /dev/sda4 is what's called an extended partition. Basically it's a sort of "super-partition" that holds /dev/sda5 and /dev/sda6, since a hard drive can only have 4 primary partitions maximum. So, you'll have to resize sda4 if you want to grow the partitions inside of it. 

Gparted is pretty easy to use. The partitions show up as colored rectangles. Just click on a partition, choose resize, and drag the edges to the new size. (Remember that you have to resize sda4 before you can grow sda5.) Then, when you're happy with the new arrangement, click Apply and go have lunch. Partitioning is fairly safe if done correctly, but a mistake can be catastrophic, so best to back everything up first.

ps Re-partitioning is not necessary to switch from Xubuntu to Ubuntu using the method in my previous post, however, if the partition is getting full, you might run out of space. :)

---

### Post by lsolesen on 2008-11-18
What does this mean "Partition 1 does not end on cylinder boundary." Anything I should address when resizing? Would it be an idea to put /home/ in a partion for itself, or will it just be a waste?

---

