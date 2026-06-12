---
title: "Hardy Clean Install"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by bierhoff15 on 2008-04-25
I've searched around and having trouble with this question.  I'm running 7.10 and want to clean install to 8.04 'overtop' my 7.10 install.  How do I accomplish this?  Do I need to delete my current 7.10 partition then install in the space it leaves behind or can I select the 8.04 install to write over my 7.10 partition?  I'm currently dual booting to XP if that makes a difference.

-Thanks

---

### Post by Shinobi326 on 2008-04-25
I asked the same exact question yesterday.  Here are the responses I got:

[http://ubuntuforums.org/showthread.php?t=765128](http://ubuntuforums.org/showthread.php?t=765128)

I simply downloaded 8.04, burned it to DVD, popped it in the drive, rebooted, and followed the menus.  It was very explicit and intuitive on the partition screen about what you want to do.  I simply selected the option to do a guided install over the partition I wanted.  Wallah... no problems.

I was concerned about my grub being messed up.  Don't worry, it'll put a new one in there with your new 8.04 ubuntu selection on top and then your Windows XP partition on the bottom.  After I booted into my Ubuntu partition I edited my GRUB menu to simply make default = 4 (Windows XP partition line).  I have to do this to make my wife happy so it doesn't default going into Ubuntu.

I hope this helps.

---

