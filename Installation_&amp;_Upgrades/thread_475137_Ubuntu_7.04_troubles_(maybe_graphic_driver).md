---
title: "Ubuntu 7.04 troubles (maybe graphic driver?)"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by No Leaf Clover on 2007-06-15
Hello all.  Big linux noob here.  Always been curious, finally decided to give it a shot.  Looked at the different distros and decided to settle with Gnome Ubuntu.  Ive been running into some issues though.

When I decided to get ubuntu, I went ahead and backed up one of my windows partitions and prepared it to be wiped (but thankfully the partitioner shrank it, havent checked if it worked out well for my data yet).  Downloaded the install iso for amd64 and mounted it no issue.  Put the cd in and reboot, and the primary screen pops up.  I go ahead and check the disk, comes back good.  Go to launch the graphic installer, loading screen comes up, loads, and then when it comes to the (I am guessing) gui, I get a mouse pointer, a background, and a garbled image across the middle.  Reboot and the same thing happens again.  Mosey back into windows and see if i can find anything online to help me out without much luck.  I find out how to check the md5 checksum, do that and it comes back golden.  Then I hear about the alternate installer.  Download that etc... partition, install ubuntu, install grub, reboot and boot into ubuntu.  Loading screen comes up, loads, and it sends me to an almost complete black screen save for a few lines of color at the top of the monitor.  Reboot and notice it can boot into the recovery mode.  Aaaaaand now I'm here.  Has this happened to anyone before.

Let me go ahead and post my specs.

MS-7220 Motherboard
Soc 939 Dual Core AMD Opteron 165 un-oc'd @ 1.8Ghz
2 Gigs OCZ Dual Channel Ram
Evga 7800gt 256mb, second PCI-e x16 left open
2x seagate SATA 160gb hd
(First Hd has a 25 gig partition for vista, second partition was storage, Second hard drive for Apps/Games.  Resized the second partition on hd1 to give me 30 gigs of space free, then had the partition manager auto-partition the 30 gigs for ubuntu)
CDRW drive, DVDRW/CDRW drive, floppy drive

Thanks in advance!

---

### Post by Pumalite on 2007-06-15
> **No Leaf Clover said:**
> Hello all.  Big linux noob here.  Always been curious, finally decided to give it a shot.  Looked at the different distros and decided to settle with Gnome Ubuntu.  Ive been running into some issues though.

When I decided to get ubuntu, I went ahead and backed up one of my windows partitions and prepared it to be wiped (but thankfully the partitioner shrank it, havent checked if it worked out well for my data yet).  Downloaded the install iso for amd64 and mounted it no issue.  Put the cd in and reboot, and the primary screen pops up.  I go ahead and check the disk, comes back good.  Go to launch the graphic installer, loading screen comes up, loads, and then when it comes to the (I am guessing) gui, I get a mouse pointer, a background, and a garbled image across the middle.  Reboot and the same thing happens again.  Mosey back into windows and see if i can find anything online to help me out without much luck.  I find out how to check the md5 checksum, do that and it comes back golden.  Then I hear about the alternate installer.  Download that etc... partition, install ubuntu, install grub, reboot and boot into ubuntu.  Loading screen comes up, loads, and it sends me to an almost complete black screen save for a few lines of color at the top of the monitor.  Reboot and notice it can boot into the recovery mode.  Aaaaaand now I'm here.  Has this happened to anyone before.

Let me go ahead and post my specs.

MS-7220 Motherboard
Soc 939 Dual Core AMD Opteron 165 un-oc'd @ 1.8Ghz
2 Gigs OCZ Dual Channel Ram
Evga 7800gt 256mb, second PCI-e x16 left open
2x seagate SATA 160gb hd
(First Hd has a 25 gig partition for vista, second partition was storage, Second hard drive for Apps/Games.  Resized the second partition on hd1 to give me 30 gigs of space free, then had the partition manager auto-partition the 30 gigs for ubuntu)
CDRW drive, DVDRW/CDRW drive, floppy drive

Thanks in advance!

I would get rid of Vista, but if you can't do that, install in a different disk. Vista is known for not wanting to share space with other OS. If you insist on installing in same disk, then you have to shrink and make new partition from Vista, but I can't help you there.

---

### Post by steveneddy on 2007-06-15
Try burning the CD at 4X.

A slower burn will give you a better quality CD.

---

### Post by No Leaf Clover on 2007-06-15
steveneddy: Did burn the disc at 4x.
Pumalite: Is this the known cause? I cant quite get rid of vista (1. I would rather not, 2. Misplaced the install disc), and I would rather not try to make room on my 2nd hard drive, thats fairly full, couldnt fit all the stuff on that on the space left on the first hard drive.  I do however have an external hdd that I might be able to use, but would rather have it on the internal.

---

### Post by Pumalite on 2007-06-15
> **No Leaf Clover said:**
> steveneddy: Did burn the disc at 4x.
Pumalite: Is this the known cause? I cant quite get rid of vista (1. I would rather not, 2. Misplaced the install disc), and I would rather not try to make room on my 2nd hard drive, thats fairly full, couldnt fit all the stuff on that on the space left on the first hard drive.  I do however have an external hdd that I might be able to use, but would rather have it on the internal.

Look, I said I couldn't help you because I haven't done it myself, I know there are users in this forum that have done it the way I told you. I tried Vista last year, but got rid of it. I you need it for your job, then you are stuck. I would help you if I knew how. I'm sorry. I hope some Windows Vista user will come to the rescue. Maybe a good idea would be to change the title of the thread to 'Double booting with Vista'?

---

### Post by Gremlinzzz on 2007-06-15
I dual boot with vista found out that i could create a partiton useing Vistas Disk manager.Just click start-right click computer=click mange-then click disk manager=right click on C; window choose shink volume-you choose how big you want the partition.I had all kinds of errors useing old rw cds.bought new cds no problems at all.oh yeah you can shink volume on any partiton.mine was all c drive.you can allso reverse it by choosing extend volume.

---

### Post by No Leaf Clover on 2007-06-16
Did a bit of searching around, and I was right, it was a graphic driver issue.  The 7800gt cards dont like the default driver in ubuntu, and wont work correctly.  [This thread]("http://ubuntuforums.org/showthread.php?t=379807") saved me.  Now I am on to getting better drivers so I can run this at a decent resolution.  Thanks for your help guys.

---

