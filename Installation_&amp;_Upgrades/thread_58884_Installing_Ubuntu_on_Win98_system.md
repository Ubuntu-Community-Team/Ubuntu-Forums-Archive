---
title: "Installing Ubuntu on Win98 system"
date: 2005-08-21
forum: Installation &amp; Upgrades
---

### Post by billpett on 2005-08-21
Hi.  I'm a complete newbie ti Linux.  Have downloaded the Live CD image, burned it and had a look.  Impressed.  So, I have downloaded the Install image.  A little nervous as to where I go from here.  Hope the install is fairly dummie-proof!  I have an 80 gig hard-drive with 2 windows partitions (FAT32) now.  Can anyone lay out in simple steps how to safely install Ubuntu 5.04?

Thank.

---

### Post by humanity_to_others on 2005-08-21
Installation screenshots: [http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=1](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=1) just be careful with partitioning

---

### Post by jasmuz on 2005-08-21
If you have 2 FAT32 partitions you must sacrifice one, or resize it properly in order to make space for the root partition and swap space (2x your ram). The minimal root partition must have more than 1.6 gb (Ubuntu full install)  and no less than 9 gb available. 

Installation is fairly simple once you got the partitioning scheme figured out.

More Install screens: [http://mrbass.org/linux/ubuntu/install/](http://mrbass.org/linux/ubuntu/install/)

---

### Post by billpett on 2005-08-21
Had a look at screen shots.  Seems straight forward except for the partiotioning.  I don't want to format any existing partitions and lose data, so are there any specifics regarding setting up a partition(s) for Ubuntu?

Thanks for the help!  O:)

---

### Post by stevegreig on 2005-08-23
I have just spent 2 weeks trying to dual boot windowsxp (fat 32) with Ubuntu. I got there this morning. I had XP on a lap top with just one partition. I used a default install with the Ubuntu disk and after a number of simple questions you have to choose to 'manually edit partition table'. It then gets complicated. The only reason it worked for me was becuause I found a web site with instrucions on: ([http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html))

I just checked that site a moment ago and it has exceeded its banwidth quota. Presumably loads of people are checking it out but maybe it will come back on line soon.

I dont' know why Ubuntu doesn't provide clear instructions for dual booting in its introductiory pages. Not many people I know have time to get their head round all this stuff. If I wasn't unemployed I know I wouldn't.

Sorry I can't be more help and good luck :-|

---

