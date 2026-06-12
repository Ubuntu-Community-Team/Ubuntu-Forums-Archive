---
title: "Laptop won't sleep after upgrade to 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by danielcraigie on 2011-10-15
Upgraded today from 11.04 and all went well except for an error installing adobe's flash installer package.

Unfortunately I have found that the laptop does not go to sleep when I close the lid, or if I select the sleep option from the main system menu.

I have an Asus Eee PC T101MT, it is quite normal for the touch screen to stop working after an upgrade but this time things are working straight away (except for the sleep problem).

I haven't seen any posts about this issue so just want to let people know.

---

### Post by divicos on 2011-10-16
here's the same with a samsung NC10..
i'm goin to report as bug to launchpad

---

### Post by danielcraigie on 2011-10-20
I found a [link]("http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html") that uses the uswsusp package to put the laptop to sleep with the s2ram and s2disk commands.

This method works and I can make the laptop suspend or hibernate by sudoing either command in a terminal window.

However, the page goes onto suggest tweaking the Hardware Access Library (hal) config files but they are not installed on this version of Ubuntu.

I had a look at the logs and found that the pm-utils logs were busy each time that I had tried and failed to make the laptop sleep.

Does anyone know how I can insert the s2ram and s2disk commands into the existing suspend and hibernate routines so that they trigger when the lid is closed?

---

### Post by PDG1 on 2011-10-28
> **divicos said:**
> here's the same with a samsung NC10..
i'm goin to report as bug to launchpad

I'm having the same problem with the same hardware ( T101MT )... do you have a link to the launchpad bug you made?

---

