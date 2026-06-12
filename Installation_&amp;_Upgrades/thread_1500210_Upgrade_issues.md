---
title: "Upgrade issues"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by Nonno Bassotto on 2010-06-02
I just upgraded from 9.10 to 10.04, and I have (at least) a couple of issues, related to the installed versions of some programs.

First, there are tzdata and tzdata-java; both appear now as manually installed (which is not the case, they were just upgraded one minute before dist-upgrade) with the version 2010j-0ubuntu0.9.10 The version 2010i-1 is available, but if I force this version, Java (openjdk-6-jre) and all its dependencies are removed. What is the current version in Lucid? I guess it is 2010i-1, so how do I restore it without messing up Java?

The second problem is with bluetooth. I used to have the Blueman PPA activated and its packages used to supersede the ones in the Ubuntu repos. But now the PPA is almost empty, and I'm left with the old versions of all Bluetooth packages. For instance bluez has version 1:4.39-0ubuntu2, and Lucid has available 4.63-0ubuntu7 and 4.60-0ubuntu8. What versions am I supposed to use?

Moreover the Bluetooth interface has changed, but I'm not sure whether this is because Blueman changed, or because Blueman has been replaced by the Gnome applet.

---

