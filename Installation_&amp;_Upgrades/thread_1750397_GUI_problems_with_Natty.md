---
title: "GUI problems with Natty"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by TrevP on 2011-05-05
Hi,

I recently installed Natty (64 bit version) and I have been enthusing about it on the testimonials page. Everything worked perfectly until tonight! I've been using the Unity interface with the Nouveau/Gallium 3D experimental driver and it has worked perfectly - but tonight the computer informed me that I do not have the required 3D support and defaulted to the Gnome interface with no Compiz available. I don't know what has happened but I can't get anything else to load.

I've tried re-installing the driver but it makes no difference. Has anyone any idea why this should have happened (I have an nvidia 7200 card installed)?

Any help would be gratefully received! I don't really want to install the "blob" and I don't see why I should have to when it worked before.

Iv'e tried installing an openGL game (Chromium BSU) and it runs perfectly so the 3D acceleration is working - unity should run!

---

### Post by TrevP on 2011-05-05
Hi Again,

I've solved this problem by adding the line: UNITY_FORCE_START=1 into /etc/environment

I'm not sure why I've had to do this now when it worked without this change before - weird!

---

