---
title: "I need help on ubuntu boot up"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by sadaruwan12 on 2008-09-24
I've tried to install ubuntu on a laptop that has this configuration

    * Core 2 Duo T5800 2.0Ghz
    * 2Gb RAm
    * 160Gb HDD
    * DVD-RW
    * W/Lan


The thing is I got the system installed after very painful hours but alas the system doesn't boot in to the GUI it hangs at the progress bar. So I went into recovery mode on the kernel from the GRUB menu and saw that when the system is booting it's not detecting the secondary CPU core. It says the CPU is not detected and the boot up process hangs there. I don't know why is there any thing I could do any thing to work around this 'coz I cant get to the GUI.

Thanks
Sadaruwan

---

### Post by Sealbhach on 2008-09-24
Hi,

See thread here where somebody solved a similar problem:

[http://ubuntuforums.org/showthread.php?t=486018]("http://ubuntuforums.org/showthread.php?t=486018")

It would be a good idea to post here your output from:

```
cat /proc/cpuinfo
```

Someone else may have a solution for you.


.

---

