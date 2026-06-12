---
title: "Unbootable system after screwing up with the dd command"
date: 2013-03-15
forum: Installation &amp; Upgrades
---

### Post by ShukatsuRonin on 2013-03-15
Hello,

Last night I was tired and I made a stupid mistake. While trying to create a live-usb with the dd command I entered "of=/dev/sda". I quickly realized what I had done and I stopped the process. I was too late, of course. 

With Linux Secure Remix I tried the "recommended repair" option of the Boot Repair program to no avail. The report can be seen here: [http://paste.ubuntu.com/5616340/](http://paste.ubuntu.com/5616340/)
At that point, my computer when powered on would still boot to the welcome screen of the OpenSUSE live medium.

I decided to ignore the warnings and proceeded with the advanced options to restore the MBR. Now when I turn on my computer the welcome screen is gone but it complains that there's no bootable device to boot from. The new report can be found here: [http://paste.ubuntu.com/5616510/](http://paste.ubuntu.com/5616510/)

I checked with GParted, instead of having Win7 (+recovery) and Xubuntu (/boot, /, /home and swap) on the disk it shows a boot partition (4MiB) on sda1, an unknown file system labeled OpenSUSE 12.3 KDE Live (948.8 MiB) on sda2 and an unallocated partition (297,16 GiB). 

Is there anyway to recover my partitions?

---

### Post by oldfred on 2013-03-15
I did not know that dd of ISO writes an efi partition and then the ISO to the flash drive.

You may be able to get some partitions back with testdisk, but dd erases/overwrites everything bit by bit, so everything in the first approx 750MB is probably gone. It is why I do not suggest dd even though it is now one way to install to a flash drive. 

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")

      
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Since you overwrote start of drive, you may not have any of the file tables in first partition. For any data beyond the dd write you may be able to use photorec.
      
 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by ShukatsuRonin on 2013-03-15
I tend to be careful when I use dd, but not this time, obviously. 
As far as I know OpenSUSE hybrid isos do not work with Unebootin or Startup Disk Creator and require ImageWriter. 

I'll take a look at the links you posted over the weekend and I'll let you know of the results.

Cheers.

---

### Post by ShukatsuRonin on 2013-03-21
A quick update, I've managed to recover most of my system. Grub is back but it doesn't show a Win7 entry. Oh yeah, and and have to reset the swap. Not fully resolved yet but I'm rather optimistic now. 

It's all thanks to TestDisk and Boot-repair and the French-speaking Ubuntu Community who helped me step after step. You guys rock! 
I guess I could link to the thread in French if someone is interested.

---

