---
title: "How to convince apt-get a package is already installed?"
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by AussieGuy on 2012-04-06
I am a dedicated user of the typesetting system TeX, and rather than use Ubuntu's own repositories, I downloaded and installed the most recent TeXlive from the TeX download site.

But whenever I wish to use apt-get to install a package requiring TeX, it wants to download and install TeXlive, because apt-get doesn't know that it's already on the system.

So how do I inform apt-get that TeXlive is already installed?

Thanks,
-A.

---

### Post by JRV on 2012-04-06
This might work:

Run synaptic
Find the package
Right click on it to highlight it
Click "Package"
Click "Lock Version"

I think this will work.
It will tell apt-get to not track the package.
If not you can undo it and no harm done.

---

