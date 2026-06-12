---
title: "problems running ubuntu within Windows"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by kenthink on 2012-02-06
The other day I installled Ubuntu on my old Acer that operates using  Windows Vista . I  used wubi to install it so  as to run within Windows.
    I was able to boot up Ubuntu and it ran fine.  But when I tried to boot into Vista Windows would not load. I used system repair but it said nothing was wrong. After many tries I was able to boot into safe mode and uninstalll Ubuntu. 
      I  always have trouble loading Windows on the computer. Even after removing Ubuntu it took three tries. Does this mean my Vista operating system has problems. I used chkdsk  and the hard drive is OK.

   I have Ubuntu running now within Windows XP on an old Seanix computer. Both XP and Ubuntu boot up fine. However in  Ubuntu I have no sound but in XP the sound is fine. 

   Why have I no sound when running the Ubuntu.

---

### Post by bcbc on 2012-02-06
How much disk space if available on the Vista machine? Ubuntu doesn't interfere with Windows, but it's possible if that you'd have issues if you're running low on space. Also, were you using Vista before you installed Ubuntu? (because if you were you'd know whether you had boot problems before installing Ubuntu).

I don't know much about sound problems in Ubuntu. If you're on 11.10, you could click on the sound icon, and then click on "Sound settings...", click on the "Hardware" tab, and then try some different options from the "Profile" drop down box. There's a "Test Speakers" button there as well.
I've just found the [Sound troubleshooting]("http://ubuntuforums.org/showthread.php?t=1885240") sticky thread that would be a good place to start. And then you can post in the [Multimedia and video subforum]("http://ubuntuforums.org/forumdisplay.php?f=334") if you still need help.

---

### Post by kenthink on 2012-02-06
I have 35 gigs free on Drive C where I installed it. I could install it on Drive D I guess which has 133 gigs.  I was running Vista before I installed Ubuntu to run within Windows using wubi. I have had problems booting Vista for about a year. Every time I install new updates I have problems rebooting. I use system restore and then of course I go back to an earlier version so Vista always wants me to install the updates again. Perhaps I should install Ubuntu on D in its own partition rather than run it within Windows.
   However I have it on my other old computer so I will probably just work with it there for a while. I will check out the sound controls you mention. I was just wondering if one is running within Windows if not all functions work. Perhaps it is better to simply install Ubuntu in a separate partition. Thanks for the information

---

### Post by kenthink on 2012-02-06
Thanks. Sound works fine now.

---

### Post by bcbc on 2012-02-06
It's always better to install Ubuntu in a separate partition, but this won't affect whether the sound works or not. Wubi uses a virtual disk and a different way to boot, but other than that it's the same as running a normal install. 
(Also you can't hibernate a wubi install since that requires a swap partition)

If you only had 35 gigs free then installing Ubuntu could have caused issues - depending on how big your install was. I don't know how much Windows requires (my xp install runs with very little space). I haven't tried a vista/win7 install with low space. But since it wasn't booting at all, I'd say the low space is a strong possibility.

---

### Post by kenthink on 2012-02-07
Thanks for your help. I think I will use Clonezilla to make an image of my disk with the Vista on an external hard drive as a backup and then install Ubuntu on my D drive where there is plenty of space and see how that works out. The old Acer is getting really bad at starting up. It is just like me getting going in the morning. Even plugging in a new USB flash drive can make it cranky and I have to remove it to get it to start. I just never know. I usually just put it to sleep but then it will often freeze and not wake up! 
   Meanwhile I am trying to slowly learn about Ubuntu from working with it on my old Seanix computer. I installed Ubuntu to work within Windows XP there and there seem to be no problems. The sound works just fine now.
   One difficulty I have found is that I cannot open wps files that is Works for Windows files. I may just save them as text files from Windows.
   Thanks again for your help.

---

### Post by bcbc on 2012-02-07
Doesn't libreoffice open .wps files?

---

