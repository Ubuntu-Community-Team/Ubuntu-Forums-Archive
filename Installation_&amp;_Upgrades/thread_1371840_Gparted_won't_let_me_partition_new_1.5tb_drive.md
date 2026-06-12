---
title: "Gparted won't let me partition new 1.5tb drive?"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by watson524 on 2010-01-03
I have a new 1.5tb internal drive I want to partition as NTFS (because Windoze machines need to see/use it) and in gparted, when I go to partition -> new, it says it could not add this operation to the list a partition cannot have a length of -1 sectors.

I recall having this issue on my 2tb external drive and I ended up creating the NTFS parition on a Windoze machine and then bringing it to the Linux box but since this is an internal drive, that's not an option.

I took all the defaults in the "Create new partition" screen.

Thanks in advance!

---

### Post by watson524 on 2010-01-03
Apparently the latest version of gParted in 8.04 is 0.3.5 and that has issues with drives over 1tb. I made a live CD of gParted (0.4.61 I think it was) and that let me make the partition I needed to so now that I carry on with life.

I wish 8.0.4 would get a package update.

thanks!

---

### Post by Francewhoa on 2011-12-19
@watson524: Thanks

@All: Direct link to GParted live bootable CD/USB/PXE/HD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

