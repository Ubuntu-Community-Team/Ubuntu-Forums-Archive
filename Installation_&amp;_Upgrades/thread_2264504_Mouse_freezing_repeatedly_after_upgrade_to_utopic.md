---
title: "Mouse freezing repeatedly after upgrade to utopic"
date: 2015-02-08
forum: Installation &amp; Upgrades
---

### Post by fondfire on 2015-02-08
I recently upgraded to Xubuntu 14.10 from Xubuntu 14.04 using the graphical upgrade tool. Ever since this upgrade was complete, my wired USB mouse periodically freezes up and the only way to fix it is to pull the USB plug. Usually, it freezes again within half an hour. The mouse and keyboard actually attach to a USB hub integrated in my monitor; the hub is attached to a USB port in the rear of my workstation.

This is an eight year old Dell Precision 490 workstation. I installed Xubuntu 7.04 on it when I got it. I've been upgrading for every Xubuntu release since then, so this was the *fifteenth* upgrade and the first time I've ever seen this sort of problem. I've tried analyzing the dmesg output, the /var/log/Xorg* files, and the /var/log/syslog* files... I can see the mouse get registered on the system and I can see it get reregistered if I pull loose the USB hub and reconnect it, but none of these sources seem to register any *error* with the mouse after it freezes up. I've tried reloading the psmouse driver after the mouse freezes up (as my keyboard is not having any problems) and that does not resolve the issue. I downgraded the kernel to the previous version; no love. (Maybe I needed to go further back with the kernel?)

This feels like a bug, but it's hard to even know how to file a bug report against this... Looking for any help on finding information or relating this to a known bug. I've never been this frustrated with Linux before!

--Fondfire

---

### Post by mörgæs on 2015-02-08
How does it work in a live boot of 14.10?

---

### Post by fondfire on 2015-02-26
Mörgæs, I apologize that I have not yet found time to boot my system onto install media to test if the problem occurs after utilizing the base system. However, I've just upgraded to kernel linux-generic version 3.16.0-31; also, Firefox was just upgraded to version 36.0. So far, the problem (which usually occurs many times a day) seems to have abated since this upgrade. So, unless I repost to this thread within the next week or so, I'd say the problem is most likely solved. I'm guessing it was a kernel driver bug...

Thanks!

--Fondfire

---

### Post by mörgæs on 2015-02-26
Good, could you please mark the thread 'solved'? 
If the problem reappears you can just remove the solved flag.

---

### Post by fondfire on 2015-04-23
OK, the kernel upgrade turns out not to have solved the problem after all.

After a lot of messing around, it slowly dawned on my slow-learning self that the mouse itself was breaking down. (The timing of the Utopic upgrade was just rather coincidental.) I replaced the flaky mouse (and my keyboard) with Logitech Unifying wireless stuff; I'm using the exact same USB port I had the old mouse plugged into for the Unifying receiver and no grief so far.

Thanks for the patient help on a wild goose chase! 8-[ :redface:

--Fondfire

---

