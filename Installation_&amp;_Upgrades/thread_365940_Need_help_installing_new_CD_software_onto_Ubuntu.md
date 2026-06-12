---
title: "Need help installing new CD software onto Ubuntu"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by MapHound on 2007-02-20
I have Ubuntu installed on to my desktop intel pc. I love it! No more microsoft!
The problem is, when i put a CD software into my optical drive, it does not automatically load and install like it did with windows xp. The CD opens a "File Browser" and displays an icon on my desktop.
How do I install the software once it opens in this fashion?
Thank you.
:KS

---

### Post by justleen on 2007-02-20
What kind of Software CD are you loading in the drive?
if it is windows software, it wont load the setup as you were used to in windows.

---

### Post by NotPhil on 2007-02-20
> **MapHound said:**
> when i put a CD software into my optical drive, it does not automatically load and install like it did with windows xp.Ubuntu software usually comes in Debian packages  (.deb files). Synaptic will automatically install software for you if you get it through a repository. If you get a Debian package elsewhere, you should double-click it, first making sure you have all the dependencies (software, usually library files) that the program needs for it to run correctly.

The other way to install is from source code. Usually, you'll get a tarball (.tar.gz file), unpack it, then run ...```
./configure
make
sudo install
```... to build the application and install it.

---

