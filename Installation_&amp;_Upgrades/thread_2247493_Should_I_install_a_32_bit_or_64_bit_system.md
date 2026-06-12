---
title: "Should I install a 32 bit or 64 bit system?"
date: 2014-10-08
forum: Installation &amp; Upgrades
---

### Post by Dragonbite on 2014-10-08
I have an older Netbook, a Gateway LT2022U Netbook, which includes an AMD Atholon chip capable of 64bit, but the system is maxed out with 2 GB of RAM.
[ATTACH=CONFIG]257045[/ATTACH]
I am looking at refreshing it, and possibly making it dual-boot with Windows 7 (it originally came with Windows Vista Basic ).  Currently it has a 64-bit version of Linux.  Looking at the system requirements for Windows I noticed 32bit requires 1 GB of RAM while 64bit requires 2!  This got me thinking

    On a low-powered system like this, would there be any benefit to going 32bit instead of 64bit Linux? 
    Should I look at using a 32bit version of Linux even though the chip can take 64bit? 
    Is there a benefit to installing the 64bit version of Linux?


Performance with the 64 bit and Xfce is adequate at this point.  I would love to run Gnome shell on it but the system generally doesn't handle Gnome well (with a Live USB)

---

### Post by sudodus on 2014-10-08
I suggest a 32-bit system. The corresponding software needs less RAM compared to 64-bit, so with 2 GB RAM, I suggest 32-bits. A 64-bit system might be slightly faster, but not enough to select it in a that computer. Of course, you can also test two corresponding systems live before you decide. If you do that, please share your results :-)

XFCE (or Xubuntu) seems to be a good choice if 14.04.1 LTS works well. If you need 12.04.5 LTS to get good drivers for the ageing hardware, maybe you will like [Precise Gnome Classic Tweaks]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks"). Both promise support until April 2017. You get it directly installed with the tweaks using the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") and the tarball

```
GnomeClassic1204-oem.tar.xz            # in OEM mode, password: changeme
```

---

### Post by grahammechanical on 2014-10-08
What, in my opinion, will make or break the user experience is the capabilities or lack thereof of the graphic adapter and the amount of its own memory that it has. I do not think that the choice between a 32 bit OS and a 64 bit OS will make up for the deficiencies of the graphic adapter.

Regards.

---

### Post by Dragonbite on 2014-10-08
It is currently running Xubuntu 14.04[.1] and is alright. 

I'm going to refresh the system because I am considering installing Windows 7 Enterprise 32bit, which I already have, and thought it would be a good time to look at my Linux alternatives.

It even ran Ubuntu 14.04 w/Unity for a while.  It just seems that the system doesn't like Gnome.

I am thinking I was incorrect in the model. I think what I have is the  [Gateway LT3103u]("http://www.cnet.com/products/gateway-lt3103u/")

---

### Post by zvacet on 2014-10-08
Like other say before me, I will choose 32 bit version. With 2GB there is no need for 64 bit system.

---

### Post by Vladlenin5000 on 2014-10-08
```
Graphics    ATI Radeon X1270
```

isn't good news...

---

