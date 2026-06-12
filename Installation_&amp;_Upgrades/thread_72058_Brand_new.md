---
title: "Brand new"
date: 2005-10-05
forum: Installation &amp; Upgrades
---

### Post by shadley on 2005-10-05
Pse help

I have just istalled Ubuntu on my old P1 333 and all went well untill it had to start up - there were about 10 little ubuntu screens and they were all shaking and unreadable. I think its got to do with the resolution. Old 14" inch screen - dont know what resolution to choose nor how.

---

### Post by Hairy_Palms on 2005-10-05
you need to go to the terminal and type sudo dpkg-reconfigure xserver-xorg and it will let you set up your screen etc.

---

### Post by SilentCacophony on 2005-10-05
Just to clarify, you should be able to get a usable console to do the **sudo dpkg-reconfigure xserver-xorg** from by pressing *ctrl-alt-F2* after bootup, and logging in there. You may need to reboot after the reconfiguration with:

**sudo shutdown -r now**

---

