---
title: "Manual partition help:  keep Suse 9.1?"
date: 2004-11-15
forum: Installation &amp; Upgrades
---

### Post by dishbert on 2004-11-15
I'm a total Linux newbie, and I keep getting cold feet when I get to the manual partition section of the Ubuntu install:  the problem is that I'm not QUITE sure what will happen once I say "Yes".

I need to keep my XP for sure.

Ubuntu recognizes my only hard drive: IDE 1 hda 81.9 Gb Maxtor and:
#1 Primary 50.4 Gb ntfs  (my Windoze XP)
#2 Primary 523.8 Mb Swap
#3 Primary 30.9 Gb reiserfs (this is my Suse 9.1)

I'd like to replace my Suse with Ubuntu, so should I:
reformat #3 
to reiserts and 
/
Bootable "Yes"??????????

Or should I play it safe and keep Suse an repartition #3?  If so, how?

---

### Post by wazoo42 on 2004-11-16
The short answer is yes.  I don't believe I set my /boot (or any of my partitions) as bootable, and it still works.  You just want to make sure that  #2 and #3 are the only ones being formatted, but it should tell you before it does anything.  
PS  Sometimes it is nice to have separate /boot and /home partitions in addition to /.  This way after you get done booting /boot can be unmounted, that way it can't get screwed up.  The separate /home is nice if you need to re-install ubuntu and all of your data is saved to home.  Then you just format / and install.

---

### Post by dishbert on 2004-11-16
Thanks for the quick reply Wazoo.  

If I understand correctly your suggestion to reformat #2 and #3 will remove Suse and prepare the drive to install Ubuntu on #3.  What file format for the swap drive? Or will it make it own decision once I say "use as swap"?  How big should the boot and home partitions be out of the 30 Gb?  OK to go with reisferts for both?

---

### Post by mr_ed on 2004-11-16
Yes, once you select "use as swap" that's the end of that.

Yes, reiserfs is ok.
I wouldn't put /boot any more than 50MB.  More like 32MB.

For /home, well... it depends.. :)
Right now, my /home is at 9GB, and the rest of my system is 3G, with 15G free, but YMMV.  (My /home is not separate)

---

