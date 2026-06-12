---
title: "Feisty update, sound problem for Gateway notebook"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by RHTopics on 2007-06-01
I just applied all the latest Ubuntu 7.04 updates to my notebook computer.  It is a Gateway MT6451 (AMD Turion 64x2).

I am running the 64 bit version:
```

Linux zippy 2.6.20-16-generic #2 SMP Wed May 23 00:30:47 UTC 2007 x86_64 GNU/Linux

```

This latest kernel update caused the sound to stop working.

Before installing feisty, I had the 32 bit version of Ubuntu 6.10 installed on this computer.  It also initially had a "sound not working" problem.

But after adding the following lines to the end of /etc/modprobe.d/alsa-base:

```

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=test enable-msi=1 probe-mask=1

```

I had sound after rebooting the computer.

I tried this same fix for feisty and it worked.  And booting into 2.6.20.15 with this fix in place, it still works as well.

Does anyone know the proper launchpad bug number on which to report this sound problem?

Other than this sound problem, the latest update does not seem to have caused problems for this computer.

---

