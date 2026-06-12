---
title: "very strange problem for all you gurus"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by mewho on 2008-07-09
hi all, i am an intermediate user of ubuntu....i have a very horrible and strange problem.  i bought a new laptop - fujitsu amilio xi2428.  everything works except for the fact that almost all operations freeze until i keypress or must continualy move the mouse ...this behaviour is also apparant when booting from the live cd i used partition editor to move some patition sizes around - and had to sit in front of the computer moving the mouse until it finished.  on startup, it just hangs unless i continually press a key - any key on the keyboard...this is driving me crazy. all bios settings are on defualt - i will attach any file that you need...please advise. oh...and this dual boots with stupid vista which loads fine.

---

### Post by Frozsyn on 2008-07-09
I think there is a bunch of thing to test:
- Have you tried the console mode (Ctrl-Alt-F1) ?
  * It will show clearly if the problem is related to the X server which seems to be the case because mouse is a "stimuli" of your problem
- Have tried the safe-mode of the live CD ? (I forgot the real name) ?
- Do you use any propietary driver ? (System -> Administration -> Hardware drivers)

My answer is a bit quick, but I didn't want to let you alone waiting so...

---

### Post by rogier.de.groot on 2008-07-09
I've had a similar problem on my laptop - until I installed using the alternate CD instead of the live cd.

---

### Post by mewho on 2008-07-09
thanks for the quick replies...
i checked all driver, and everything is ok...when i go to console during loading, no errors, but things only advance if i continually hit enter or space etc.  am downloading alternate installer cd now, and will re-install and let you know if it fixes the problem. thanks,
mewho

---

### Post by mewho on 2008-07-09
ok, desktop seems to be ok after text based install, although i had the same issues during the install itself...had to keep on moving the mouse the entire time.  now it is just taking a really long time to load - it seems to hang at 2 points - reading files needed to boot and preparing restricted drivers.  i have an nvidia 8600m gs card, and used envy to install, not restricted drivers.  any advice would be appreciated.

---

### Post by mewho on 2008-07-09
installed bootchart to see what was going on...image attached.  if i had not hit enter at 3 places during the boot, it would still be loading...i'm really stuck here...help!!!:confused: thanks

[[IMG]http://s2d2.turboimagehost.com/t/500909_hardy-20080709-2.png[/IMG]](http://www.turboimagehost.com/p/500909/hardy-20080709-2.png.html)

---

### Post by hal8000 on 2008-07-09
Install sysv-rc-conf

sudo apt-get install sysv-rc-conf

Then use sysv-rc-conf to remove boot services you dont need.
Default runlevel is 2 and a X means service is enabled.

You appear to be running ld_static, S20vboxdrv, find and grep ??

Have a look at the bootchart wiki:
[https://wiki.ubuntu.com/BootCharting?action=AttachFile&do=get&target=hardy-20080601-3.png](https://wiki.ubuntu.com/BootCharting?action=AttachFile&do=get&target=hardy-20080601-3.png)

some are starting in under 30 seconds.
You will have to google each service if you dont know what it does.

---

