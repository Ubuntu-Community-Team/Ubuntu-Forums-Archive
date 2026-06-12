---
title: "Ubuntu won't install on Intel machine"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by nyyppä on 2005-09-07
Hi!

Ubuntu won't install correctly on my computer. Or actually first part goes throug, before first restart, it only takes about 2½h. So something is wrong. Live CD works fine, system is ready in few minutes. So CD-rom seems to operate normaly. My computer is:

MSI 848P (Intel 848/ICH5)
Pentium 4 2.6GHz (Northwood, 533fsb)
2x512DDR 333MHz
Gainward Geforce 6800 LE
2x120gb Maxtor SATA
1x160gb Samsung IDE
NEC DVD-RW (model 2510?)

I've tried all possible hard drive combinations (all, only PATA, only SATA, on same cable with DVD and with seperate cable). Now after very long installing, system tries to boot up, it gives error with something about IRQ18. After while it tries to continue, but this error message comes again (several times). System tries to shut down IRQ18 but doesn't suceed.

Is there anything to do? I've tried all different BIOS setups that could affect, with no help. I'm using pressed CD, ordered directly from ubuntu (got it from friend). I've searched first 10 pages from this forum and Googled, with no luck.

Sorry for language, English is no my home language.

---

### Post by Steve1961 on 2005-09-07
I'm not sure what the problem is, but just to discount some of your hardware.  I have 2xMaxtor SATA hard drives and an NEC DVD RW and they work fine.

---

### Post by nyyppä on 2005-09-08
I've tested all H/W-combinations that are possible. So there is something else wrong, I suppose it has something to do with IDE-controller (it uses IRQ18 ) from the chipset.

---

### Post by lompolo on 2005-09-08
There could be some problems with pressed cd:s. My experience is Pressed live-cd works well, but install cd in the same box is bad. Don't now why.

---

### Post by nyyppä on 2005-09-08
Hmm...same cd worked well on another computer (with old HP 8200 -burner)

---

### Post by nyyppä on 2005-09-08
Forgot to mention, I allso tried to install with basic 52x CD-ROM drive. So it's not the problem.

I'll change my Intel 875 -Mobo when I get home, let's hope it works... Will post comments afterwards.

---

### Post by nyyppä on 2005-09-08
Problem solved, without changing MoBo. All I did was updated MoBo's BIOS and everything went normally. MSI says that this bios version only changes some CPU Microcodes, but it seems to do something else allso.

---

