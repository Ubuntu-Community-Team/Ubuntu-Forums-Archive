---
title: "Vanilla kernel post-install quirks"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by beijingjj on 2005-11-16
I've had this happen with just about any distro I've ever used, including Ubuntu which I'm using now.

Out of the box install everything works. Then I install the latest kernel from kernel.org (unpatched) and strange things start happening, for example:

1. I have to manually load the modules for my wireless card (ipw2200).
2. Either I put "psmouse.proto=imps" as a kernel boot option and my touchpad works but my trackpoint doesn't, or I don't put that option and the trackpoint works but some of the features of the touchpad don't work.
3. Touchpad scrollings no longer works.

All of the scripts and config files are the same, all I've done is update the kernel, so I would like to understand where these differences come from. In this particular case I've even added my wireless card module to /etc/modules but still have to manually load it for it to work.

Although I want to find work-arounds to get these things working again I'd really like to understand why this is happening too.

Thanks in advance!

---

### Post by ubuntu_demon on 2005-11-16
Don't post questions in the customization section!

---

