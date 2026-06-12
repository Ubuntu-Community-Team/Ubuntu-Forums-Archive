---
title: "Ubuntu refuses to install"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by wjo53 on 2011-12-02
I've tried installing Ubuntu 9.10, 10.04, 11.04 (32 and 64bit), and now 11.10 (64bit)
 
They all refuse to install.
 
CPU - Intell Core2 Quad Q6600, ASUS Striker Extreme MB, 8 Gig RAM, Nvidia Geforce 8600GT video
 
The computer had been running Win7 64bit perfectly, and was retired due to an upgrade.
 
Can anyone offer any advice before I go get another license of Win7, admitting that Ubuntu doesn't cut the mustard? ;-)
 
Thanks in advance,
 
John

---

### Post by oldtimer7777 on 2011-12-03
Have you reset your BIOS recently? 

Set your BIOS to failsafe and see if it will boot using a Live USB Stick of Bootable Ubuntu. Avoid using a disc in case your drive is faulty.  

My guess is something is strange about your BIOS configuration.  I would check there and see if you or anyone else has made any kind of mods to that system.  Reset the BIOS if so. Disconnect your Power Supply and use the Jumper on the board to reset your CMOS. And see if that does the trick.  If this is a laptop, don't try that, and see if you can reset your BIOS from within BIOS itself. 

> **wjo53 said:**
> I've tried installing Ubuntu 9.10, 10.04, 11.04 (32 and 64bit), and now 11.10 (64bit)
 
They all refuse to install.
 
CPU - Intell Core2 Quad Q6600, ASUS Striker Extreme MB, 8 Gig RAM, Nvidia Geforce 8600GT video
 
The computer had been running Win7 64bit perfectly, and was retired due to an upgrade.
 
Can anyone offer any advice before I go get another license of Win7, admitting that Ubuntu doesn't cut the mustard? ;-)
 
Thanks in advance,
 
John

---

### Post by wjo53 on 2011-12-03
I can't say that I tired that.  The computer was never OC'd,  so there shouldn't be anything real strange going on.  Will try just the same.
 
J

---

### Post by wjo53 on 2011-12-07
Well, finally got around to trying the clear CMOS setting.  It appears that that is what was causing it to fail.
 
So, I guess I have some crow to eat for the 'crack' about Ubuntu not cutting the mustard.  :-)  Maybe mustard will help the crow.
 
That said, the installation wasn't completely pain-free.  Got it installed only to find no network connection.  Did some searching on the new machine, and found others with the same problem (nVidia MCP55) 4 years ago.  Found a workaround, tried it, and so far, so good.
 
So, oldtimer7777, Thank you for the suggestion.  My suspicion is the clock multiplier changed.  I think it had been at 6 on the weekend when I tried first, and tonight, after the CMOS reset, it's at 9.  Other than that, I don't know.
 
Cheers
 
J

---

### Post by oldtimer7777 on 2011-12-07
Whenever I have a system that I didn't build myself, I always reset the BIOS from the CMOS. Also I want it to fail before I get too involved in the process of installation of OS. A great way to tell the EOL of a MB is try the jumpers to reset from CMOS.  If it is very old, it will probably fail at that point, and just replace the part MB with a new one. Order of Operation in Computer Repair. 

Oh don't forget to mark this thread solved when you are done.. Thanks.

Cheers,

:popcorn:

> **wjo53 said:**
> Well, finally got around to trying the clear CMOS setting.  It appears that that is what was causing it to fail.
 
So, I guess I have some crow to eat for the 'crack' about Ubuntu not cutting the mustard.  :-)  Maybe mustard will help the crow.
 
That said, the installation wasn't completely pain-free.  Got it installed only to find no network connection.  Did some searching on the new machine, and found others with the same problem (nVidia MCP55) 4 years ago.  Found a workaround, tried it, and so far, so good.
 
So, oldtimer7777, Thank you for the suggestion.  My suspicion is the clock multiplier changed.  I think it had been at 6 on the weekend when I tried first, and tonight, after the CMOS reset, it's at 9.  Other than that, I don't know.
 
Cheers
 
J

---

