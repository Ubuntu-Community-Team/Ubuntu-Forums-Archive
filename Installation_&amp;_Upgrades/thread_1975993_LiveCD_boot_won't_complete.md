---
title: "LiveCD boot won't complete"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by dclement on 2012-05-08
Hello,

I'm struggling to get at least a live session on [_this kind of desktop_]("http://support.dell.com/support/edocs/systems/dim4550/specs.htm"): Dell Dimension 4550, 1 Gb ram, 2.4 GHz processor.

It can boot from a CD (not USB). The CD is good (it worked on another PC). But with the D4550, it hangs somewhere in the stages which end with [OK].

Just exactly where depends on the boot options I choose, but there are soo many combinations I'd rather not test them all.

Is there some optimal set of boot options that would ensure booting on this kind of old PC? I think Lubutnu would be nice on that hardware.

TIA - regards, Daniel

---

### Post by wilee-nilee on 2012-05-08
Web says this may be your graphics card  ATI X1300 run this command to confirm what it is.

```
lspci -nn | grep VGA
```If you run this it will show all the hardware most likely.

```
lspci
```Then check out this link.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

This link is for getting you in on a live cd possibly, you may have to just use a alternative cd to do a text install then fix from there.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by dclement on 2012-05-08
The graphics card is not ATI but Nvidia Geforce MX420, I should have mentioned it.

Also, this PC is not currently running Linux (otherwise I would gladly follow some upgrade path) but Win XP :-(

I'm trying to get Linux on it. The best result I had was to reach the "Welcome..." (text) message, but I never got to the graphical desktop.

---

### Post by mips on 2012-05-08
Have you tried booting with the nomodeset option?

You can always try the alternate cd image.

---

### Post by 2F4U on 2012-05-08
The Ubuntu documentation explicitly mentions problems with PCMCIA cards on Dell machines and there is also a section about problems with CD's:

[https://help.ubuntu.com/12.04/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/12.04/installation-guide/i386/boot-troubleshooting.html)

---

### Post by dclement on 2012-05-08
Thanks for help.

@mips: I hadn't tried _only_ the nomodeset option. I've done it. Different attempts give me different results:
- once it hanged after "Starting NTP service ntpd.......[OK]";
- once I got the "Welome to Ubuntu 12.04..." but followed by dreadful blinking cursor.

I could try an alternate CD, but I'd like a live session to check that everything works properly.

@2F4U: there is no PCMCIA (it is a desktop). But in the link you gave me, I noticed the options vga=788 and fb=false. Unfortunately, non of them worked. 

It's weird, because each attempt seems to give me a system which hangs at a different point (e.g. "Starting configure network device......[OK]" instead of the above). :confused:

---

