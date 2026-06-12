---
title: "Ubuntu Installation Issues"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by Pseudo You on 2012-01-07
I'm trying to install ubuntu on a Dell Inspiron mini 10 laptop to get rid of a bad virus it got on Windows XP. I'm installing ubuntu from a cd I burned on the ubuntu site (version 11.10). The start is fine until it gets to the start of the installation. When it's done copying the files and the actual installation starts, the screen turns black, the cursor is still there and it's frozen. Then I have to do a force shutdown on the laptop to turn it off.

---

### Post by serge_o on 2012-01-07
Hi there,

could be many reasons
1) damaged CD (CDs are unreliable, sometimes a "just burned" CD has incorrect data.
if could be the case.  I experienced this several times.

2) damaged burner - the burner "burns" incorrect data (maybe just one incorrect sector - would be enough). Experienced this as well. 

I assume you have not just tried once, but several times?


What I would suggest is create a bootable USB (according to the manual on ubuntu.com) and tell here whether it worked or not.

USB sticks do have their own problems with booting sometimes, but if the CD path does not work, this is the simplest workaround. 

if USB works then your problem is solved. If it hangs just like the CD, then the problem is deeper and with this particular laptop/kernel/hardware combination.

QUESTION: Does  Live CD mode work? or does it hang just like the installation.
if ubuntu starts ok as Live CD it is one thing. if it hangs all the same, this is another thing.
Please post your answer to this question, this will help.

> **Pseudo You said:**
> I'm trying to install ubuntu on a Dell Inspiron mini 10 laptop to get rid of a bad virus it got on Windows XP. I'm installing ubuntu from a cd I burned on the ubuntu site (version 11.10). The start is fine until it gets to the start of the installation. When it's done copying the files and the actual installation starts, the screen turns black, the cursor is still there and it's frozen. Then I have to do a force shutdown on the laptop to turn it off.

---

### Post by howefield on 2012-01-07
If it is only to get rid of a virus and clean your Windows install, you could try something like the AVG Rescue CD.

---

### Post by Pseudo You on 2012-01-07
Thank you for the info serge. I didn't try the live CD mode because the OS (Windows) had a very bad virus on it I was trying to rid of. I was trying to do the usb method for ubuntu , but got confused just on the needed software for the usb method. If you know of a bootable usb ubuntu guide that is easy to understand and not confusing, that would be great.

Thank you for your input howefield, but the computer had a really bad computer virus that lingered on the computer for months. I don't feel like getting another Windows virus on this computer and I don't have enough time to wait for the AVG rescue CD, because I am leaving to go someplace soon. But thank you for the help howefield.

---

### Post by darkod on 2012-01-07
Having a virus has nothing to do with trying if the cd will run in live mode (Try Ubuntu option). Do that first because it will show any hardware problem or problem with the cd. In this mode ubuntu runs from the cd, nothing to do with the hdd and the virus on it.

Also, when burning a OS install cd always use low speed, not more than 8x. CDs these days go up to 56x. Never burn a cd for OS installation as such high speeds, it makes errors during the burn.

---

### Post by Pseudo You on 2012-01-08
Thank you for this info Darkod. I slowed down the CD burn speed with imgburn and that did the trick. Now I got ubuntu on the laptop. :D:D:D:D:D

---

