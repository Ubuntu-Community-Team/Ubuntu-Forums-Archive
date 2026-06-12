---
title: "Unable to partition in Vista..."
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by svivian on 2007-10-20
I've installed Linux (Red Hat and SuSE) a few times on my old PC so I'm familiar with the process of creating blank/unallocated space on the end of the hard drive for it.

Now I'm using Vista, and want to shrink my main drive. But Vista won't let me do it, it gives me the message "Size of available partition can be restricted if snapshots or pagefiles are enabled on the volume".

I have one HD, 300 GB. Vista shows the current partitions as:
```

| [no name] 63 MB              | RECOVERY (D:) 10 GB NTFS    | OS (C:) 288 GB NTFS                                                      |
| Healthy (EISA Configuration) | Healthy (Primary Partition) | Healthy (System, Boot, Page File, Active, Crash Dump, Primary Partition) |
```

Anyone know how to fix this so that I can create some blank space on the end of my drive?

---

### Post by svivian on 2007-10-20
bump ;)

anyone?

---

### Post by Imamoomoocow on 2007-10-20
im a noob when it comes to linux but i have been using windows since 95.  I had his same problem when upgrading to ubuntu 7.1 . This is what worked for me.
Defragment your drive.
Try using a System rescue CD from [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) 
burn the disk and boot to it. When everything is loaded (forget what command you use to get gui) use g parted to shrink you 288 gig partition.  
Then simply install your distro.

---

### Post by svivian on 2007-10-22
I defragmented my hard drive, first using Vista's tool, and when that didn't work, Diskeeper. But there are still files near the end of the drive. Vista's partitioning tool only says I can shrink the drive by ~3 GB. But I tried that and it keep getting an error.

I downloaded and burned that system rescue CD, but the graphical environment ('startx' is the command, btw) just won't load. I've tried everything - using the 'vmlinuz2' kernel instead of the normal 'rescuecd' one, and various other things it told me to type ('doxdetect' and 'forcevesa') to no avail.

Are there any partition tools for Vista that actually move data to accomodate partitions?

---

### Post by Shazaam on 2007-10-22
I haven't used Vista but this might work...
Open "System Restore" and delete all but the LAST restore point. (or turn it off)
Turn off the "Indexing Service"
Find out where to adjust and set the Vista swap file and turn it off.
Find "Disk Cleanup" and run it.
Reboot into "Safe Mode" (F8?) and defrag from there to see if Vista will move the files. If it does move the files try to resize the drive with Vista again in normal mode.
Once again I haven't ran Vista so I don't know if those tools are the same.

---

### Post by Tom B on 2007-10-22
I also had problems shrinking my vista partition. The vista partition tool wouldn't let me, and even when I defragmented it still took up way more space than it should have. A few people advised me to use the vista tool, but I got sick of it and used the [GParted live cd]("http://gparted.sourceforge.net/livecd.php") to shrink it. It worked fine for me, but backup anything you don't want to lose before you try it.

---

### Post by svivian on 2007-10-23
Woohoo! I finally got it sorted! After a bit of fuss choosing different display options, the Gparted live CD worked like a charm. Took all night and half of this morning, but it worked...

Had to use our old CRT just to get the display to work.

Ubuntu is now installed. Thanks for all the help guys!

---

