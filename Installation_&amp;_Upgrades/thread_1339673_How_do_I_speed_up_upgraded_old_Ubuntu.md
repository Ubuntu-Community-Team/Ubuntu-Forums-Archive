---
title: "How do I speed up upgraded old Ubuntu"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by leden on 2009-11-27
Hi all!

I have been using Ubuntu on my laptop computer from release 8.10, so I had 2 distribution upgrades. Boot time was always fast (at least compared to any Windows I had), but when I did partial upgrade to Karmic Koala (9.10), followed by kernel upgrade, the boot time increased dramatically.
So, today I installed another Ubuntu 9.10 on other partition just to compare boot times between the two.
The results were staggering:
from GRUB to log-in screen: 60+ s (clean is 32 s)
from log-in screen to 0% HDD activity: 70+ s old user, 45 new user (clean is 16 s)

My old (upgraded) Ubuntu runs only sshd and default services like the clean one does, so how  still couldn't explain an additional minute during boot.

What is the explanation of the so much inferior boot time with upgraded vs. clean? I simply don't understand this.
Btw, both of them are using ext3 file system.

I do not accept "tons of applications have cluttered everything" or similar, because I can't see how that affects boot performance since none of them are actually running at boot.

And I am sure that there must be a way to improve boot time, so that its as fast as a clean one.

I know that it is highly advisable to do clean install, but I am not interested in that.

---

### Post by mkvnmtr on 2009-11-27
I too have upgraded to 9.10 on one of my systems and the boot time is slower. I think that is because a clean install uses an new partition scheme ext4 and a new grub. An upgrade does not change your grub or the format of your partition. I believe the only solution is a fresh install.

---

### Post by leden on 2009-11-27
But I did a clean install with ext3. 
Even if I didn't we are speaking about a whole minute of boot time not a few seconds.

---

