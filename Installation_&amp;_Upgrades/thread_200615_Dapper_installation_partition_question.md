---
title: "Dapper installation partition question"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by AlexBryan on 2006-06-20
I have a laptop running XP on a hard drive with 2 partitions, one is 40BG and has Windows XP installed on it and the other is 50GB. Would it be best to let Ubuntu make its own partition or for me to make one for it using partition magic? Also whats the best size for a Ubuntu partition and what format e.g. Fat 32 or a linux format?
Thanks

---

### Post by OneL on 2006-06-20
The Dapper Live/Installation CD has a partition manager, GParted, you can use during the installation.  It will allow you to specify the size and format of any partitions you create during your install.

You'll want to go with a native Linux format for you installation; the default choice is Ext3 and that works.  You can create another partition which you can use to share data between Dapper and XP, and formatting that as FAT32 makes sense.

I'd suggest that you look at some of the forum threads about dual booting before you go ahead.  What Dapper will do is replace the Windows boot load with Grub, but you can boot into Windows from Grub.  If that's not to your liking, there are ways to change that.

In any event, be sure you have your XP installation disk handy.  If something does wrong, you can use it remove Grub from your MBR and get back into XP.

---

