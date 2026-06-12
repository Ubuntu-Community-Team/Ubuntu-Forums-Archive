---
title: "Warning: Do not install with windows dynamic disks and a question about fixing it"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by hwttdz on 2008-11-10
First a warning: Do not install ubuntu if you have windows using dynamic disks.  

I tried this, windows now does not recognize the drive on which windows is installed.  Interestingly ubuntu can read from this drive as if it is ntfs, because it is only a dynamic disk and does not have raid 0 or any such nonsense.  The reason behind this is when I was installing I tried to get raid 1 working on windows because I wanted a more reliable system.  Ironically this attempt has now made it more likely that I have to waste more time doing system repair which is what I was trying to avoid in the first place.  My plan at this point is to save the disk image of the "dynamic partition" which is really just ntfs then make the switch described in this readme: [http://www.wilderssecurity.com/showthread.php?t=191006](http://www.wilderssecurity.com/showthread.php?t=191006) .

Let me know if I'm doomed or if there is another way.  Also where's the best readme for repairing grub after installing windows (in case I have to do that again).  And of course the windows people think I'm pirating their software because I've had to activate it like 10 times in the past month.  Of course if it worked reasonably I wouldn't have had to activate it so often, but then again if it was reasonable I wouldn't have to activate it at all.  Evil windows.  Sorry rant, I'm upset and frustrated.

---

### Post by hwttdz on 2008-11-10
Yeah that didn't work at all.

---

