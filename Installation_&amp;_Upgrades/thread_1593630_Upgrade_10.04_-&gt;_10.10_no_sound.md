---
title: "Upgrade 10.04 -&gt; 10.10 no sound"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by chrisjoha on 2010-10-11
I just upgraded my Ubuntu 10.04 laptop to 10.10, and noticed that while the speakers where playing sound, my headphones (jack) where dead silent. I ended up reinstalling alsa, but to no avail. No I have no sound at all.

Lenovo Thinkpad T400s.

`alsamixer` -> "cannot open mixer: No such file or directory"

What I can do to debug/rectify this?

---

### Post by mörgæs on 2010-10-11
There are quite a few posts regarding this topic. 

I don't have a solution for you other than to follow this thread:
[http://ubuntuforums.org/showthread.php?t=1593095](http://ubuntuforums.org/showthread.php?t=1593095)

Temüjin is writing there. That is a good beginning.

---

### Post by chrisjoha on 2010-10-13
So I ditched the old setup and went for a clean 10.10 install. Now the sound is back in my speakers, but my headset (which is the only thing that matters to me) is dead. Any help on debugging this issue?

---

### Post by chrisjoha on 2010-10-13
Sound, sweet sound! This solved my problems: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

### Post by optimusmedia on 2010-11-13
> **chrisjoha said:**
> Sound, sweet sound! This solved my problems: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

After DAYS of trying many things, I too have finally have sound! Thanks!

---

