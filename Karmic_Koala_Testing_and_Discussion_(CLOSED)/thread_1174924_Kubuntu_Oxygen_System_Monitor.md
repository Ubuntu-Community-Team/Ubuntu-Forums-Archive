---
title: "Kubuntu Oxygen System Monitor"
date: 2009-05-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by brm on 2009-05-31
I have used Kubuntu for several years and am currently running a fully-updated Karmic Alpha 1.

I use the [KDE 4 Oxygen System Monitor]("http://www.kde-look.org/content/show.php/Oxygen+System+Monitor?content=86664").

All functions worked perfectly under Ubuntu Jaunty. The CPU temperature is not displayed under Karmic. The two necessary support packages, lm-sensors and hddtemp, are both installed.

Another Ubuntuforums user is also reporting a failure to display the CPU temperature: [http://ubuntuforums.org/showthread.php?t=1174606]("http://ubuntuforums.org/showthread.php?t=1174606")

---

### Post by rbmorse on 2009-05-31
Does the version of lm-sensors in the Karmic repository support your hardware suite?

---

### Post by brm on 2009-05-31
> **rbmorse said:**
> Does the version of lm-sensors in the Karmic repository support your hardware suite?

The version in the jaunty repository supported my hardware. How would I check whether there has been a change between the jaunty and karmic versions which would lead to my ( early 2008 ) hardware not being supported in the later repository?

---

### Post by Kow on 2009-06-03
> **brm said:**
> The version in the jaunty repository supported my hardware. How would I check whether there has been a change between the jaunty and karmic versions which would lead to my ( early 2008 ) hardware not being supported in the later repository?

Take a look at the package source changelog. They simply "add-on" between releases.

[https://launchpad.net/ubuntu/+source/lm-sensors](https://launchpad.net/ubuntu/+source/lm-sensors) For lm-sensors. There has been 1 new (upstream) release since then. You'll have to go all the way to the lm-sensors website to find the changes for 2.10.8. Perhaps debian inadvertently broke something while cleaning up the debian/rules file.

---

