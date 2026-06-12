---
title: "initial reboot after upgrade 11.10 froze at login and now..."
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by cernenus on 2011-10-14
after upgrading from 11.04 to 11.10 today i restarted my computer as instructed and the new login screen appeared and i thought all was well, however after selecting my login(with the mouse) the login screen froze. so unfortunately I had to hard reset... leading to the real problem, now I have a blank screen(no BIOS screen no hard drive activity no nothing just the power on light.) can someone please help i am using someone elses computer to write here as my only baby now seems to be dead.:

---

### Post by MAFoElffen on 2011-10-14
> **cernenus said:**
> after upgrading from 11.04 to 11.10 today i restarted my computer as instructed and the new login screen appeared and i thought all was well, however after selecting my login(with the mouse) the login screen froze. so unfortunately I had to hard reset... leading to the real problem, now I have a blank screen(no BIOS screen no hard drive activity no nothing just the power on light.) can someone please help i am using someone elses computer to write here as my only baby now seems to be dead.:
Sounds like there was a graphics problem (possibly with the graphics driver) that caused a segfault the carried around the the bios/cmos, which affected a subsequent boot...

If you have a laptop --> Turn off > remove battery > wait 10 mintues > boot > enter Bios Settings > exit without saving > Boot.

If a desktop--> Turn off CPU and Monitor. > Turn off ATX power switch on PSU.  If no switch, unplug pwer cord. > Unplug network cable, video cable and Monitor power cable. Plug everything back in and power up monitor and CPU. > Enter Bios settings, then exit. > Boot.

Can you get to a Grub menu?  If you select Rescue Mode from the boot menu, will it boot into a failsafemode / low graphics?  If so, if you go into system settings > additional drivers... can you install a driver?

If you go to a terminal session, what does this say about your GPU?
```

lspci -vnn | grep VGA

```
Please post your /var/log/Xorg.1.log

---

### Post by cernenus on 2011-10-14
thanks i will give that a try, i'll repost in ten minutes.

---

### Post by cernenus on 2011-10-14
um here is were being a rookie sucks. when me and my wife move to her dads house i was paranoid that he would hack my machine so i put a BIOS pass in and have no idea what it was so i guess all hope is lost.

---

### Post by MAFoElffen on 2011-10-14
> **cernenus said:**
> um here is were being a rookie sucks. when me and my wife move to her dads house i was paranoid that he would hack my machine so i put a BIOS pass in and have no idea what it was so i guess all hope is lost.
LOL!  That's still okay... Just getting to that BIOS password prompt should be enough to clear the affected cache.  <Cntrl><alt><del> from there should get you booting again.

Sidenote-- You may later what to clear your CMOS so you can either reset that password or to disable BIOS password setting.  Desktop, laptop, different models- vary on how to do that.

---

### Post by cernenus on 2011-10-14
sadly no first thing is pass and c.a.d. only leads back to pw screen i have a back up laptop but the only distro i have is mint 11.? trying that it keeps freezing so i may have to call a quits :(

---

### Post by GoodGuy98 on 2011-10-14
Almost all BIOS have a jumper or reset switch to allow clearing
the CMOS which clears out the BIOS password. If you call the
manufacturer of the laptop, they should be able to tell you how to access the jumper or switch on your model. I bought an old desktop PC at a garage sale which had a BIOS password required.
I did the above procedure and was able to boot it without a
password prompt.

---

### Post by MAFoElffen on 2011-10-14
> **GoodGuy98 said:**
> Almost all BIOS have a jumper or reset switch to allow clearing
the CMOS which clears out the BIOS password. If you call the
manufacturer of the laptop, they should be able to tell you how to access the jumper or switch on your model. I bought an old desktop PC at a garage sale which had a BIOS password required.
I did the above procedure and was able to boot it without a
password prompt.
If it is a desktop, you just pull the cmos battery and jump the cmos clear pins for 10 seconds.  If it is a laptop... then things are different.

---

### Post by cernenus on 2011-10-15
cleared the BIOS password (quite easy on my laptop) and voila working perfectly i should have read the release notes I'm kinda sad that there is no gnome desktop anymore oh well it is what it is. thanks everyone.

---

