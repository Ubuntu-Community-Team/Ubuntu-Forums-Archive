---
title: "Cannot enable Compiz desktop effects with Radeon x1550"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Mercury_Alpha on 2010-04-24
Here's the chain of events: I do a clean install of 10.04 RC and retain my /home partition from 9.10. I notice that desktop navigation is very sluggish. I install the "radeonhd" package and remove the "radeon" and "ati" packages. Navigation performance improves. I install Docky, and it informs me that it needs compositing to operate.

I go to System>Preferences>Appearance>Visual Effects and select the "Normal" option. It says "Searching for available drivers" for several seconds, the screen flickers in and out for about ten seconds, and a pop-up appears which informs me that desktop effects could not be enabled.

I can simply enable Metacity's own compositing, but its performance is lacking. I don't mind downgrading back to 9.10, but I'd like to know if there's a simple tweak I could make before I go through that process.

Thanks for reading.

---

### Post by clhsharky on 2010-04-24
HI

Ubuntu 10.04 RC has 3D out of the box for your chip on radeon OSS drivers. 3D is needed for compiz so I'd say your config files brought forward on your home partition has compromised your 3D.
Remove your xorg.conf file and restart.

Sharky

---

### Post by Mercury_Alpha on 2010-04-24
I don't have such a file. As it turns out, Xorg doesn't use those files anymore. That part of the system was shifted to auto-detection in 9.10 onwards. You can create one manually, but the point is that I don't actually have such a file that would create the complication that you describe. But I appreciate your help :)

---

### Post by Tricast on 2010-04-24
Funny, i have opposite problem. I can't activate visual effects with the RadeonHD driver but the built-in Radeon driver works and is faster for me. Unfortunately it's a bit unstable. This is on a ati x1270.

---

### Post by Yellow Pasque on 2010-04-24
Some things to check
```
compiz --replace
LIBGL_DEBUG=verbose glxinfo
```
Finally, look in your /var/log/Xorg.0.log if that doesn't help.

---

### Post by Mercury_Alpha on 2010-04-24
"Compiz --replace" told me it had a fatal error regarding the detection of software rendering. This occurred with and without Metacity compositing enabled. Running without the "--replace" modifier produced the same error.

I was not running a failsafe GNOME session either.

At any rate, I have downgraded back to 9.10, where Compiz compositing works smoothly again. I was also having other problems, such as (1) being unable to add a Docky link to Evolution and (2) being unable to run a few programs (that are important for me) which apparently do not have 10.04 compatibility yet.

---

