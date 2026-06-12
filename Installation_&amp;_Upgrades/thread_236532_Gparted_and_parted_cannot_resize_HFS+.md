---
title: "Gparted and parted cannot resize HFS+"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by rbp082006 on 2006-08-14
Hi, I am an ubuntu linux newbie. I have been searching the forum and googling for a few days but I couldn't find a way to resize my hfs+ undestructively. I will appreciate some pointers or links.

I've followed the 'HOWTO: Resize your HFS+ partition for free" thread but I couldn't resize my HFS+ partition. I am running OS 9.2.2 so I don't think I have Journaling.  I tried to install ubuntu 6.0.6 LTS from the desktop live cd on my iMac G3 (256MB, 10GB hard disk) I want to resize the hfs+ partition to 5G and the rest for swap and ubuntu.  I've tried the following:

1. Install ubuntu by clicking the desktop icon.  gparted resize button grey out, only delete partition is allowed.
2. Start gparted from the menu, same result.
3. Run parted from a terminal.  But I got the error message: "Data relocation left some data at the end of the volume.  Resizing the HFS+ volume has failed."
4. At the boot prompt use "install", manual edit partition table doesn't have edit partition option.
5. Tried to upgrade gparted from 0.1 that comes with the live CD to 0.2.5  Installed g++ but I think I don't have enough memory to compile the program.  (Screen went black and CD-ROM keeps moving)
6. Same thing when I try to upgrade parted to 1.7.1
7. Installed "alien" and try to use the 0.2.5 RPM.  Same result as #5
8. apt-get said I have the latest parted and gparted.
9. Couldn't get the "Testing" parted and gparted to work either.
10. Tried "alternative" ubuntu live CD but still no resize partition option.

I also tried Yellow Dog 4.0.1 and Debian Sarge and both of them won't allow me to edit the HFS+ partition.  There is another thread in the "Breezy Badger 5.10 > Ubuntu 5.10 Support (GNOME) > Ubuntu Macintosh/Apple/PPC Users" about the similiar problem but it is OSX and is ubuntu 5.10 instead of 6.06.1

Is there a gparted 0.2.5 or parted 1.7.1 binary that I can download and install?  I tried google it but no result.  

Perhaps I got the compiles wrong. If anyone think I should try again please let me know the proper procedured.

Any help will be appreciated.  I also include the print out from parted:

Disk geometry fro /dev/hda: 0kB - 10GB
Disk label type: mac

Number Start  End    Size   Filesystem  Name             Flags
1       1kB   32kB   32kB               Apple
2       33kB  65kB   33kB               Macintosh
3       66kB  98kB   33kB               Macintosh
4       98kB 360kB  260kB               Patch Partition
5      360kB  10GB   10GB   hfs+        MacOS

I tried:
resize 5 360kB 5GB

and other units but same result.

---

### Post by zxee on 2006-08-15
Resizing hfs volumes has always been a pain.
Maybe this thread will help?
[http://forums.macrumors.com/archive/index.php/t-66470.html](http://forums.macrumors.com/archive/index.php/t-66470.html)

---

