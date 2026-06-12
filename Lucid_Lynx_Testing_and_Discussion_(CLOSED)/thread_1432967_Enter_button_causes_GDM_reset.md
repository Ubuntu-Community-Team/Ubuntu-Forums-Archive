---
title: "Enter button causes GDM reset??"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by forcecore on 2010-03-18
has anyone experienced this type problem, of course it may be Virtualbox fault. Press enter after desktop appears and boom Gnome dies and login appears.

Virtualbox 3.1.4 x86 with ubuntu live cd was my test, no real pc test but with beta1 coming i test it on real pc.

---

### Post by meborc on 2010-03-18
i think this is an issue related to plymouth and nvidia drivers

thry the 2 plymouth threads active in these forums for more info... ;)

[http://ubuntuforums.org/showthread.php?t=1416872](http://ubuntuforums.org/showthread.php?t=1416872)
[http://ubuntuforums.org/showthread.php?t=1432491](http://ubuntuforums.org/showthread.php?t=1432491)3

edit: also post #2 from [http://ubuntuforums.org/showthread.php?t=1428627](http://ubuntuforums.org/showthread.php?t=1428627)

---

### Post by forcecore on 2010-03-18
Virtualbox has nothing to do nvidia, but i tested daily 17 on real laptop with intel chip and everything was fine.

In virtualbox even alt button reseted GDM like something had killed GDM or x.org i dont know, anyway maybe it is Virtualbox fault and thats it. I did not even install guest addons just livecd from iso.

---

### Post by shafin on 2010-03-18
It happened once or twice here, with an enter in firefox, GDM restarted, and I've a physical install, not a virtual one. however, some upgrades came and I have not had them recently.

---

### Post by forcecore on 2010-03-18
even numbers causes reset, what is login username and password for livecd (after reset login appears) ? when i press just enter for user/pass then authentication failure ?

---

### Post by awam66 on 2010-03-18
Yes I get this all the time. First time pressing enter and you get logged out to the log in screen. Happens in a terminal also. Tried "update-grub" and pressed enter back to login. 32 bit installation on usb hard drive and amd athlon 64bit processor. 1g ram. It only happens the first time you press enter I think.

---

### Post by meborc on 2010-03-18
> **forcecore said:**
> Virtualbox has nothing to do nvidia, but i tested daily 17 on real laptop with intel chip and everything was fine.

In virtualbox even alt button reseted GDM like something had killed GDM or x.org i dont know, anyway maybe it is Virtualbox fault and thats it. I did not even install guest addons just livecd from iso.

sorry dude, :) i just had the exact same issue just due to plymouth...

I rarely run virtualbox images nowadays as usb install is so convenient, hope you find a fix!

---

### Post by forcecore on 2010-03-18
looks like it is quite rare crash and strange that keyboard buttons crashes Ubuntu xorg (i think) not GDM.

When crash happened and i saw second black screen then some strange characters had on upper left corner screen.

---

### Post by forcecore on 2010-03-19
Now i am quite sure it is Virtualbox fault because if installed it wont happen on Virtualbox but only on livecd mode so case closed.

---

### Post by awam66 on 2010-03-19
> **forcecore said:**
> Now i am quite sure it is Virtualbox fault because if installed it wont happen on Virtualbox but only on livecd mode so case closed.

No it is not a Virtualbox fault it happens on my desktop as I said above.

---

### Post by forcecore on 2010-03-19
> **awam66 said:**
> No it is not a Virtualbox fault it happens on my desktop as I said above.

is that happens lastest Lucid daily release too?

---

### Post by xc3RnbFO8P on 2010-03-19
Do you use Auto Login?

---

### Post by forcecore on 2010-03-19
> **Ringi said:**
> Do you use Auto Login?

if you asked me then that happened on **live cd** in VB, pressing enter, alt, 1234.. buttons caused reset.

---

### Post by xc3RnbFO8P on 2010-03-19
I'm asking all of you, I got this Firefox enter problem (have to login with username and password) and if I start Empathy or Update Manager I have to login with password.

---

### Post by xc3RnbFO8P on 2010-03-19
It seems like the last update has fixed  the problem.

---

### Post by combic on 2010-03-21
I have a similar problem. Ubuntu 9.10.
After logging in different time intervals (0-15 min) after pressing the ENTER key, resets the Xorg or GDM, and I have to re-login. After first logging in I can press Enter key many times before GDM will "autoreset". But, after logging in again (after reset) the problem no longer occurs, even after several days, until I shut down the system. When I turn it on again, after the first logging in GDM or Xorg is reset again... after random count of enter key press (in all system applications).
Can someone help me?

---

