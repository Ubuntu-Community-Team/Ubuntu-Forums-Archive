---
title: "Howto install on a 2nd hard drive?"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by held7over on 2010-09-24
I have two 250 gig drives in a system. Originally, I partitioned both of them exactly alike, by hard wiring each hard drive in its turn, as the primary drive and installing Ubuntu. 

Then, I slaved one hard drive to the other, and set up rsync to periodically update the second hard drive with my /home as my backup, because I had heard it wouldn't work if I told rsync to back up / of the first drive to / of the second drive.

So, after a time, the first drive now has Ubuntu 10.04 and the second drive slaved to it has 9.04.

I decided today that I wanted to update the OS of the second drive to 10.04. 

In the manual partitioning, by temporarily enabling options, I managed to change the drop down menu from "a" drive to the "b" drive (maybe I didn't need to do that), and then clicked on manual partitioning, which gave me BOTH drives represented in the partitioning. Both drives were already partitioned the way I wanted them to be, and so I only operated on the "b" drive, telling it to format the "b" drive "/" and to format the "b" drive "/home" since I was changing them to EXT 4, from EXT 3. 

What actually happened, is the installer wiped my "/home" on the "a" drive, and installed Ubuntu 10.04 in the "/" partition of the "b" drive. It got half of what I wanted done correctly and half wrong. Luckily, all my personal data is still alive on the "/home" "b" drive.

My FIRST question is, how could I have gotten the installer to use my existing partitions and format and install only the partitions I enabled on the "b" drive?

And my SECOND question is, If I had told it to do both the "a" and the "b" drive, would it have installed Ubuntu 10.04 in the "/" partitions of both drives at the same time?

Thanks! :)

---

### Post by n1unqn on 2010-09-24
By default I think Ubuntu puts your data files on a second disk if it finds one because this means your data is separate from the OS so if you ever need to wipe an reinstall you don't have to backup.

To do what you wanted you could have removed the first hard drive physically to get it to the update only on the 2nd one.

A bit of a pain.

A better option for a mirror (sound like what you are trying to do) is to use a motherboard that has hardware RAID 1 support then anything you do the the first hard drive is automatically replicated on the second one.

---

### Post by held7over on 2010-09-24
Thanks n1unqn.  Evidently I have tried to get the installer to do something it wasn't meant to do.  I guess I will go back to hard wired installs. Ha!

---

