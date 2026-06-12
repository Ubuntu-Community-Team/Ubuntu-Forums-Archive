---
title: "Latest updates broke KDe4"
date: 2009-01-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gmclachl on 2009-01-26
I just done a bunch of updates including kde5libs and some other kde libraries and it seems to have killed my desktop. Now all I get is a blank screen with a cursor. 

There is nothing in the xorg log. I do have some errors in the kdm log 

(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path


but I very much doubt this is causing the issue

George

---

### Post by Mazza558 on 2009-01-26
Same here. It's annoying because it's quite tough to get back to the login screen from there without restarting.

---

### Post by gmclachl on 2009-01-26
By the looks of thing it may have been a partial upgrade which has caused the problems. I noticed a few packages have been kept back 

--
The following packages have been kept back:
  libx11-6 libx11-dev libxcb-render0 libxcb-render0-dev libxcb-shape0
  libxcb-shm0 libxcb-xv0 libxcb1 libxcb1-dev

I imaging it will be fixed when the rest of the updates appear

George

---

### Post by gmclachl on 2009-01-26
Spoke too soon, I will pulled down the rest of the updates and it's still broken. 

George

---

### Post by Progressive on 2009-01-26
My KDE has been broken for 4 or 5 days now. I really do like amiwm as a fallback option, but seriously this should've been fixed by now.

I'm running amd64... perhaps this is only for 64 bit?

---

### Post by inportb on 2009-01-26
32-bit here... and Plasma just started crashing on me.

I start Plasma... it crashes, tries again, gives up. The same thing happens with a fresh .kde

---

### Post by Vorian on 2009-01-26
All KDE core packages are being upgraded right now, the build machines are not done with them yet.

Once complete, you should experience a smooth transition into the KDE 4.2 final release

---

### Post by inportb on 2009-01-26
> **Vorian said:**
> All KDE core packages are being upgraded right now, the build machines are not done with them yet.

Once complete, you should experience a smooth transition into the KDE 4.2 final release

Ooh, I hadn't noticed the date. Thanks for the heads-up!

---

