---
title: "What happened to GNOME Classic Login!"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by machdohvah on 2012-01-09
OK... So, I was a dumb dumb and erased my entire hard disk (and that I did successfully with the use of the Ubuntu 11.10 installation CD with a choice of replace entire disk cutting the power almost as soon as it started erasing all the partitions and using an old DOS 6.20 installation diskette to FDISK it completely clean!)

Now, when I went back to install Ubuntu 11.10, I was surprised to find that my favorite login choice of "GNOME Classic" disappeared. I THOUGHT I was told that it would be there (and it was there until I decided to start over).

Do I have to rant about how lame the "Ubuntu" login choice really fails? I mean, even while in FireFox, all the windows are using the main menu bar at the top of the screen and not at the top of the window where it is suppose to be. Many times that is inconvenient for I may have many things going on at once, and using another WorkSpace to the right would not work at all.

I cannot tell that there are other windows open at all when I maximize the current window I am in. This shell is some lame I cannot truly begin to rant adequately enough to give it what it needs.

---

### Post by Bucky Ball on 2012-01-09
At the login in screen have you checked the 'Sessions' tab for Gnome classic? It should boot to that when selected and next time you boot that will be the default.

---

### Post by machdohvah on 2012-01-09
I am so embarrassed. My first search on the subject gave me an answer that worked.

**In terminal:** sudo apt-get install gnome-session-fallback

And, sure enough, the "GNOME Classic" was back. I am back in business and this thread is solved.

---

