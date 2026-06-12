---
title: "Feisty Desktop Issues: icons, background"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by CApaddler on 2007-04-26
I performed an upgrade from Edgy to Feisty on my AMD64 system. The upgrade was successful until the final reboot, when X choked due to my use of the NVIDIA drivers in Edgy.. anyway, that is another issue.

My current problem:
1. Desktop background is blank. Setting a background is successful for a given login session, but upon logout/login or rebooting, the background returns to black
2. Desktop icons do not appear. Despite having enabled various icons under Apps/Nautilus/Desktop in gconf-editor, my desktop is entirely empty.

Neither of these issues were present before the upgrade. Can anyone offer assistance?

---

### Post by graphius on 2007-04-26
I am having a similar problem. It started before I upgraded to feisty, but I still cannot choose my desktop image. I can access "configure desktop" both by right clicking on the desktop or through system settings. I can choose any background, but when I click apply nothing happens. I still have a plain blue background (all my icons are ok) 
I am a photographer and I like to have a current favorite shot on my desktop.

What program do I have to reinstall / configure?

---

### Post by CApaddler on 2007-04-27
Another thing to mention: I cannot right click on my desktop - nothing happens, no right click menu appears.

Anyone have an idea how to get my "desktop" back? Where are my icons, background, and right-click ability?

Sean

---

### Post by Tuvic on 2007-04-29
I had similar issues: empty desktop, no icons, not being able to right-click. I found [this thread about a related issue]("http://ubuntuforums.org/showthread.php?t=425324"). I just opened a console, typed ```
nautilus &
``` and my desktop was back and functional. I hope it works for you too.

---

