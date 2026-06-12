---
title: "Dell Optiplex GX620 &amp; Ubuntu 6.10 Installation"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by soulchild on 2007-01-31
Hi folks,

I just tried installing Ubuntu 6.10 on a stock Dell Optiplex GX620. The desktop installation didn't work because of the known ATI video card problems so I tried the alternative installation CD in text mode but guess what: Textmode doesn't work either! All I get is completely unreadable junk on the screen. Any ideas on how to fix this? What the heck is Dell putting in their machines that they are causing such weird problems?

Thanks a lot!

--Soulchild

---

### Post by derby007 on 2007-01-31
Try this:
[http://ubuntuforums.org/showthread.php?t=231343&highlight=gx620](http://ubuntuforums.org/showthread.php?t=231343&highlight=gx620)

---

### Post by soulchild on 2007-01-31
Errr ... I was too quick! The replier suggests something that has to be done post installation if I'm understanding things because there is no GRUB (and thus no RECOVERY MODE) installed on my system yet. I can't even get the default textmode (ncurses-based?) installer to show up correctly.

---

### Post by derby007 on 2007-01-31
Sorry that didnt apply.
Did u try the 6.06 Dapper version ?
'What the heck is Dell putting in their machines ?' 
    >> My Dell has 3 primary partitions, 1: C:\  2: Recovery & 3: Dell Utilities
So......this means the last primary partition must be an Extended partition, where u can add other Logical partitions & this is where Ubuntu & Swap get written to.
Dont know if this helps.........
BUT then again : looks like your problem is a graphics issue......

---

