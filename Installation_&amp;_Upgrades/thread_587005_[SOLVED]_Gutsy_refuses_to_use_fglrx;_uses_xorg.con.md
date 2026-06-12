---
title: "[SOLVED] Gutsy refuses to use fglrx; uses xorg.conf.failsafe"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by bmartin on 2007-10-22
I was using fglrx under Feisty and everything was fine...

Then I downgraded this desktop to Gutsy :-(

I've downgraded from Feisty to Gutsy on three computers so far; I'm thankful that I haven't hit the BBSOD (black boot screen of death) everyone's talking about. None of the computers were fully-functional after upgrading.

This one is using the same xorg.conf it always has. In the restricted drivers manager, fglrx appears to be enabled. lsmod reports that the kernel module is loaded. /var/log/Xorg.0.log contains the following interesting lines:
```
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(WW) "dbe" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "vbe" will not be loaded unless you've specified it to be loaded elsewhere.
```
Instead, I get the vesa driver. How convenient.

How can I track down what's wrong with my xorg.conf or configuration since all of the log files contain failsafe garbage? Is there a way I can disable this failsafe crap? I don't want it. If there's a problem with my settings, I want my computer to crash and burn.

---

### Post by alastair on 2007-10-22
> **bmartin said:**
> Instead, I get the vesa driver. How convenient.

After the X failure (fglrx) you should also have a log file :

```
/var/log/Xorg.0.log.old
```

Which may pinpoint the ATI driver failure better (the last log is the failsafe vesa log).

Alastair

---

### Post by bmartin on 2007-10-22
> **alastair said:**
> After the X failure (fglrx) you should also have a log file :

```
/var/log/Xorg.0.log.old
```
Unfortunately, that also contains a run-through of the xorg.conf.failsafe settings. I checked all of the log files. In there.

---

### Post by bmartin on 2007-10-25
I solved this by causing the failsafe file to fail, then looking into log and finding why my xorg.conf file wasn't working. It turned out to be the refresh rate of the monitor... I have no idea why it didn't fail  before Gutsy.

---

