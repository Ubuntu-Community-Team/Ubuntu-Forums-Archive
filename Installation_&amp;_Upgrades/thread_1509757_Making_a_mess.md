---
title: "Making a mess"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by megnetz on 2010-06-14
Hello! I'm new to ubuntu and the first thing i did was going into the /bin folder and move some stuff around. Now it wont boot. Says it cant find files like mountall, hwclock, plymouth, hostname, etc. I had a double boot with win 7 to start with so I decided to reinstall ubuntu from the CD. So now I have "triple-boot" with two copies of ubuntu 10.04 and neither is working. Win 7 works as normal fortunately. I guess the easiest solution is to reinstall win 7 from a cd? Other solutions?

---

### Post by r m h on 2010-06-14
move all the s**t back into bin that you "moved around" by booting into single boot mode?

---

### Post by Calmor on 2010-06-14
I have to ask (for the purposes of others learning from your mistakes) - what possessed you to go into /bin and move things around?

As for fixing your problem... 

If you don't care much about the Ubuntu systems that now don't work, and don't feel like reinstalling Windows 7, boot to a live CD.  In the System - Administration menu, delete the partitions that house all of the Ubuntu stuff.  *Make sure you don't delete the Win7 partition*

Then just install as normal, and I'd hope things would be fine.

If you can move the stuff back into bin, it should continue to work.  I'm wondering if you broke/moved symlinks that can't be just as easily copied back in.

---

### Post by megnetz on 2010-06-15
[http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)

Easy solution!

I was using this guide [http://linuxcommand.org/](http://linuxcommand.org/) (moving a script into the bin folder and misstyped).

---

