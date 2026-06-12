---
title: "Wine and nvidia problem?"
date: 2015-08-30
forum: MINT
---

### Post by misterrollton on 2015-08-30
Hello.
First of all, sorry for my English and sorry for being a newb, probably.

Yesterday, I encountered some problem with my desktop environment.
After i launched a game via Wine, my screen stopped showing anything but big vertical stripe in the middle.
Reboot hasn't helped nor reinstalling nvidia drivers, though removing them helps to load correctly. The problem is, I
need my GeForce and don't want to leave it that way.
LightDM works good, problem starts after logging in in my user account.
Also, booting in recovery mode works fine even with drivers.
The most interesting thing: logging in with drivers and stuff as GUEST works perfectly well, too, even not in recovery.

So, any suggestions would be very appreciated.

---

### Post by dino99 on 2015-08-30
usually when such issue appear on my system, i purge the app then reinstall it (ok its quite brute force, but when you have no idea about the root cause)

should be good to know about which ubuntu version is used, which graphic driver, which wine too
if its a pure wine issue (borked settings) then rename .wine to .wineback (or whatever) then run wincfg to recreate a new .wine, where you can either reinstall your app or copy/paste from the .wineback

---

### Post by misterrollton on 2015-08-30
Purge and reinstallation not helped.
My system is Linux Mint 17.1, based on Ubuntu 14.04; tried 331, 340 and 346 versions of driver, none of them seem to work now.
Wine is not essential for the solution. It was a cause of the problem, but now it's irrelevant. Anyway, it's 1.7.1 with POL.

---

### Post by PaulW2U on 2015-08-30
*Thread moved to **MINT**.*

---

### Post by misterrollton on 2015-09-02
The problem was solved by deleting KDE config file.

---

