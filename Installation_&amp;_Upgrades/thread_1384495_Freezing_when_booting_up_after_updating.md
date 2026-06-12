---
title: "Freezing when booting up after updating"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by LykkeLamaen on 2010-01-18
Hi

I just completed a fresh install of Ubuntu 9.10 from USB (On a Toshiba portege m200). The installation went fine, and I updated the packages and rebooted when asked to do so, but when the computer was starting again the Ubuntu logo became wierdly deformed and then nothing happened. After 5 minutes I hard-rebooted it (Is that what its called? I held down the power button). And booted up in recovery mode. Again the computer froze, with this message as the latest on screen:

```
fsck from util-linux-ng 2.16
[  4.7015221] Adding 2441840k swap on /dev/sda5. Priotity:-1 extends:1 across: 2441840k
/dev/sda1: clean, 152745/3514368 files, 894200/14040002 blocks
```

Any ideas

---

### Post by LykkeLamaen on 2010-01-18
I've tried to reboot a couple of more times now. It still freezes at the same spot.

GRUB gives me the option to boot memtest86+ or to start using some differet options or to start a command promt (this is before the computer freezes). Is there any of that, that would help me?

Thank you in advance

---

### Post by LykkeLamaen on 2010-01-18
I found this thread which I think is about the same problem that I'm having. 

[http://ubuntuforums.org/showthread.php?t=1331500](http://ubuntuforums.org/showthread.php?t=1331500)

Is there any way to make grub skip fsck from inside the grub commandline, or by adding an option to the boot command?

---

