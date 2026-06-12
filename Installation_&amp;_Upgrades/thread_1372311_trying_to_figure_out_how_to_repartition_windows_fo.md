---
title: "trying to figure out how to repartition windows for ubuntu"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by linuxluver on 2010-01-04
I want to install Ubuntu in a dual boot with the Windows XP that came preinstalled on my netbook. I do have an external CD/DVD drive, and my hard drive is 140 GB with 35.7 GB used by XP.

---

### Post by tachuela on 2010-01-04
Defrag once or twice, then use Gparted Live CD.
[http://sourceforge.net/projects/gparted/files/](http://sourceforge.net/projects/gparted/files/)
Use the ISO

---

### Post by linuxluver on 2010-01-04
Why would I need to use a gparted Live CD? Oh, and by the way, I'm not planning on installing 9.10, as 9.10 sucks. I'm installing 9.04.

---

### Post by underquark on 2010-01-04
Delete as much rubbish from Windows as you can.  Then defrag your hard drive from within Windows.  Get rid of any fixed-area data on the hard drive (they show up as green bars in Defrag) by disabling Windows swap file and deleting any restore point files before running the defrag utility.  Once all your Windows data is safely at one end of the disk you can boot from a Live CD (or a  USB stick) and use gparted to shrink the Windows partition down to, say, 50Gb.  Then install ubuntu and let it use the remaining space.  Set aside a bit for a swap file (many people say size of RAM x 1.5).  Read postings and consider whether you also want a separate partition for /usr/local although this latter isn't essential.

For one horrid moment I thought that your sig had something to do with liking Bridget Jones's Diary.

---

### Post by kansasnoob on 2010-01-04
> **linuxluver said:**
> I want to install Ubuntu in a dual boot with the Windows XP that came preinstalled on my netbook. I do have an external CD/DVD drive, and my hard drive is 140 GB with 35.7 GB used by XP.

Well it's always a good idea to defrag, and you really should backup anything important before any partitioning or installation procedure.

I also like to allow plenty of room for an existing OS, basically no more than 2/3 used, ie: with 35.7 GB used: 35.7 X 1.5 = 53.55 so I'd make Windows no smaller than 60GB (70 or 80GB minimum seems appropriate to me).

Then just follow this guide:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by tachuela on 2010-01-04
Don't forget to set PageFile to '0'. You can set it back to its normal value later.

---

### Post by blur xc on 2010-01-04
My $0.02- manually create /, /home, and swap partitions for ubuntu from gparted while in the live cd.  Then in the install processes select the advanced option from the partion/formatting step of the install process and select where you want each partition you created mounted.  Make the / 15 - 20 gigs, swap what you need it to be (lots of opinions on that one, same amount as you have ram, twice your ram, whatever) and leave the remainder for /home.

Good luck.

BM

---

