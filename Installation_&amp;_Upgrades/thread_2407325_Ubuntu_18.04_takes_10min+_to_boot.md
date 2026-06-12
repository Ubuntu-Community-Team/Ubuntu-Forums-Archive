---
title: "Ubuntu 18.04 takes 10min+ to boot"
date: 2018-12-02
forum: Installation &amp; Upgrades
---

### Post by Marco_Ros on 2018-12-02
Hello
I have installed UBUNTU 18.04 in my computer, only to notice that it takes more than 10 minutes to boot.
while loading, there are the following messages onscreen

```

[drm:drm_atomic_helper_wait_for_flip_done [drm_kms_helper]] *ERROR* [crtc:34:PIPE a] flip_done timed out
[drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [crtc:34:PIPE a] flip_done timed out

```
(showed only some of them)

Also, after system is up and running, everytime I open CONFIGURATION, it takes about 2 minutes, white all my system appears as stalled (it accepts no input)), until configuration panel shows up.

I'm sure all this has something to do with the errors at start-up

Hw can this problem be diagnosed an corrected?


 Acer Aspire 2920 Laptop
UBUNTU 18.04 LTS
RAM: 4GB
Intel® Core™2 Duo CPU T7300 @ 2.00GHz × 2 
GRAPHICS:Intel® 965GM 
OS TYPE: 64 bits

---

### Post by freemedia2018 on 2018-12-02
Similar to [https://ubuntuforums.org/showthread.php?t=2348892](https://ubuntuforums.org/showthread.php?t=2348892)

The solution was to go from 16.10 back to 16.04 LTS. This is also a bug on launchpad. The thread on ubuntuforums is also for your Intel 965 chipset.

Edit: well that's no good, you're already using 16.04. 16.04.2 Seems to have the problem, 16.04.1 is recommended. 

Here is the launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1685442](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1685442) On launchpad, they recommend adding this kernel parameter: 

```
video=SVIDEO-1:d
```

---

### Post by Marco_Ros on 2018-12-03
Thanks free,
Where should I add the mentioned parameter?
[B][COLOR=#000080]
video=SVIDEO-1:d

[/COLOR][/B]An inconvenient in the solution suggested is that I'm using **18.04, NOT 16.10**.
I will take a try.

---

### Post by Marco_Ros on 2018-12-04
> **Marco_Ros said:**
> Thanks free,
Where should I add the mentioned parameter?
[B][COLOR=#000080]
video=SVIDEO-1:d

[/COLOR][/B]An inconvenient in the solution suggested is that I'm using **18.04, NOT 16.10**.
I will take a try.

After adding parameter to grub command and restarting, booting time reduced dramatically to about 3:20 min, that, if not perfect, tremendously convenient, after the eternal wait before that.

ADDITIONALLY:
every time I opened CONFIGURATION or any program that needed to "read" a configuration file, it was taking about 2:00-2:30 min, but as a consequence of modification to GRUB, it also was corrected.

---

