---
title: "Upgrade to 8.10 did not complete, now dpkg problems."
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by chadgauth on 2008-10-16
I am guessing when my computer went into sleep mode my upgrade to 8.10 did not complete.  When I turned my computer off and back on nvidia had graphics problems so I rebooted into:
 
Ubuntu intrepid (development branch), kernel 2.6.24-19-generic (recovery)

and then I ran 
"dpkg Repair broken packages"

  It seemed to work fine so i decided to resume.  Got to the login screen and then after login it changed the screen to an orange color and it had a cursor, but nothing loaded after that.  I tried to run dpkg again and it said to run: 
"dpkg --configure -a"

 I dropped to root then ran that and there are a bunch of problems that say:

"dpkg dependency problems prevent configuration of ______: dependency problems - leaving unconfigured"

  At the end of these errors it says:

"dpkg: too many errors, stopping
dpkg: ../../src/packages.c:265: process_queue: Assertion '!queue.length' failed.
Aborted"

I just want to get this working again, does anyone have any ideas?

---

### Post by Manasia on 2008-10-27
You can bump this, I got the same error today when I tried to upgrade to 8.10

---

### Post by Manasia on 2008-10-27
Hey Chad,

You need to find which package cannot be configured properly and remove then reinstall it. For example my problem package was dbus so here are my resolution steps:

sudo dpkg --force-all -r dbus
sudo aptitude install dbus

This installed my problem package dbus. Let me know if this helps.

---

### Post by sampoli on 2008-11-06
I was having this exact same problem. I tried what Manasia suggested and it worked!

Thanks!

---

### Post by iansuth on 2008-11-18
Manasia, Thanks, that solved the problem.
Ian

---

