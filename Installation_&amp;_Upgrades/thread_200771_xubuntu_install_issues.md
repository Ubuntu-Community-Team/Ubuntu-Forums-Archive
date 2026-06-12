---
title: "xubuntu install issues"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by rowck001 on 2006-06-20
I installed xubuntu 6.06 from the liveCD onto my tosiba laptop already running ubuntu breezy. All went well but as I forgot to have my ethernet pcmcia card connected to my router - it didnt detect my network and i could not get net access.

I attempted to run the xubuntu disk install again with the ethernet connected - and running the live CD gave me an adsl net connection.  :-)

Then when I selected the hard disk install icon - the install went to the point where it re-partitioned the disk and started the 'installing system' dialog. But all that happens is the CDROM thrashes wildly and no hard disk access can be seen and the install progress stays at 0%. Re-burning the CD image and trying a new CD has no effect.

I selected the erase disk partitioning option and it said that part #1 was ext3 and part #5 was the swap in all cases.

What could possibly be the cause??

---

### Post by Winblowz on 2006-06-20
What is your hardware? It might be that your hardware can't handle the live-cd. Maybe you should try the alternate install cd. 

How fast did you burn the cd image? The slower the better, so burning at 4x might be a good thing to do.

---

### Post by rowck001 on 2006-06-20
I burnt the liveCD slowly (4X) and checked for CD integrity with xubuntu and both my burnt CD's were ok. 

Surely I should not have hardware issues if the Live Install worked the first Time and Ubuntu has been working flawlessly previously (just a little slowly with gnome).?

Is my theory that the filesystem is somehow become locked  and the installer cant copy to it (eg. a permissions issue) and I should fdisk the drive to remove all partitions before trying again correct??

---

