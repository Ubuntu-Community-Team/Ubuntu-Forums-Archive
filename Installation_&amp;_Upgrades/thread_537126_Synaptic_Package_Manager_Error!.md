---
title: "Synaptic Package Manager Error!"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by xspikeyhairx on 2007-08-28
Ok so I just installed Ubuntu... I was installing something with synaptic until my pc froze. so I Pressed the X and turned of my computer (using the button on my computer). I then started back up and try to re-open synaptic and I get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report.

Could some-one help me with this?

---

### Post by canadianwriterman on 2007-08-28
The problem was created when the system shut down while Synaptic was downloading. Simply open the terminal and type the command shown in the error message and that should restore things.

---

### Post by xspikeyhairx on 2007-08-28
But when I do this it says I need Superuser privilages... and I'm the administrator so I don't know what this means.:confused:

---

### Post by Seisen on 2007-08-28
Add "sudo" in front of the command.

---

### Post by xspikeyhairx on 2007-08-28
Thnakyou very much! This solved my problem!

---

