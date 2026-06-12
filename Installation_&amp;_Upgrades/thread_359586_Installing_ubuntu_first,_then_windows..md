---
title: "Installing ubuntu first, then windows."
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by Tmi on 2007-02-12
Hi.

I've been running a small partition with Ubuntu now for a few months and am now so happy with it I feel ready to switch away from windows. Thus I intend to format my drive and have a big Ubuntu partition. I do however intend to save about 10 Gb of disc space in an unused partition just in case I would need to install windows for some school thing or whatever.

Now I remember that I have many times heard people say "Install windows first, then linux", because the other way around might mess with the dual booting. Since I'm going to try to run without windows for a while I'm just wondering if this is still the case?

So in short my question is; Is it likely that I encounter dual booting problems if I install ubuntu first, then windows? If it is so, is it easilly fixed?

---

### Post by Tedd on 2007-02-12
The problem with installing Ubuntu first is that after you install Windows, it overwrites Ubuntu on the Master Boot Record. It's pretty easily fixed, just pop in your Ubuntu CD and type in "rescue" as a command line, it'll help you install the Grand Unified Bootloader.

Cheers,
-T

---

### Post by nike984 on 2007-02-12
This [link]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") has the solution for your case

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

