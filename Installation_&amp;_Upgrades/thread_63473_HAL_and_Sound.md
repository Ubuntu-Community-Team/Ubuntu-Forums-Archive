---
title: "HAL and Sound"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by kitplane01 on 2005-09-08
My new installation says "Failed to initalize HAL" on login.  

Can someone offer any helpful ideas?

Also, I don't have sound working yet.  Could this be related to my HAL problems?

-Thanks
-Kitplane01

---

### Post by skoal on 2005-09-08
[QUOTE=kitplane01]Also, I don't have sound working yet.  Could this be related to my HAL problems?[/QUOTE]
No, sir.  Your sound drivers are loaded long before the hal demon gets launched (through dbus-1).  I know there are several threads in these forums concerning HAL problems, with sol'n(s).  Type "initialize hal" up there in the search button and hopefully you won't have to dig too deep from all the hits returned.

What kind of sound card do you have?  If you don't know right off hand, 'lscpi' from a terminal should provide some insight.

\\//_

---

### Post by mlomker on 2005-09-08
HAL is Hardware Abstraction Layer.  It works with dbus and hotplug to enable plug-and-play to work well.  Some machines need a BIOS update to fix the issue...not sure how new your box is but I'd check that your BIOS is current first thing.

---

