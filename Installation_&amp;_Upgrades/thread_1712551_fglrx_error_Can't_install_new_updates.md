---
title: "fglrx error Can't install new updates"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by Reginthorn on 2011-03-22
Here is a picture of my problem![IMG]http://www.imageurlhost.com/images/coor3n36dua75zawjm.png[/IMG]

---

### Post by areeda on 2011-03-23
Try going into system->administration->additional drivers and disabling the ATI proprietary drivers.  That worked for my nVidia upgrade.

Once the upgrade is complete you should be able to turn them back on, maybe you'll need to download newer versions first.

Joe

---

### Post by Mark Phelps on 2011-03-23
According to Google, that model notebook comes with Intel GMA 4500 graphics.  Does yours have an add-on ATI card?

Also, does yours support "switchable graphics"?

Asking because we're seeing a lot of posts from folks with the latter and they have been unable to figure out how to disable the onboard Intel graphics in Ubuntu to get the ATI add-on card working.  Appears that in some PCs, the BIOS does NOT provide an option to disable the onboard Intel graphics.

---

