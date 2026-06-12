---
title: "Can't Boot from Ubuntu USB"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by cool_dude2 on 2015-12-21
Hi guys, 

I am trying to boot Ubuntu from a USB drive, however, when I open it, I get a "graphics initialization failed". I typed in "help" as discussed in this thread ([http://ubuntuforums.org/showthread.php?t=1594003&page=2](http://ubuntuforums.org/showthread.php?t=1594003&page=2)), however, then I get a message saying "System halted" and a bunch of random blinking symbols.

To be honest, this is one of the weirdest things I have ever seen!

Any idea how to get Ubuntu to boot for me ? o.O

[IMG]http://i.imgur.com/ugPJSFo.jpg[/IMG]

---

### Post by westie457 on 2015-12-21
Welcome to the Fora.

Before we can help you properly we need some info about your computer:

Make and Model
Amount of Ram
Manufacturer of Graphics card.

Also which version of Ubuntu you are trying to install.

At the moment a definitive help would just be guessing.

Also is there another OS on the computer?

---

### Post by cool_dude2 on 2015-12-21
Long Story: While I was using the Laptop, the battery failed and the PC hibernated. Then I turned it on to resume, however, the battery failed again and the PC hibernated while trying to resume previous hibernation. After the whole mess, Windows 7 won't boot and I  just get BIOS, blinking underscore, restart. 

Now I am trying to boot Ubuntu from a USB drive, so that I can backup my files, however, I am getting this problem now. I have previously ran Ubuntu on this laptop multiple times, so I am sure this is not an OS incompatibility.

Laptop Model: Acer eMachines E725
RAM: 3GB
Graphics Card: Intel Family Chipset 4th Series
Ubuntu Version: I am not 100 % sure, it's the latest version from Summer 2014. I have ran this version on the same laptop multiple times.
OS: PC "should" have Windows 7 on, however, I cannot get it to boot.

---

### Post by Bucky Ball on 2015-12-21
Welcome. Summer in which hemisphere? If you are talking 14.10, it is no longer supported and you should be using a supported release. If you mean 14.04 LTS, that is supported until 2017 and let's move on.

To confirm which it is, please open a terminal and:

```
lsb_release -a
```

Please confirm which release you are using. Pointless going much further with an unsupported release.

---

### Post by mrroberthadley on 2015-12-21
This looks like a hardware issue. I don't think this is related to the boot media.

---

### Post by cool_dude2 on 2015-12-21
Hi guys,

It seems that the problem was with the Ubuntu version, I installed the latest version on my flash drive and I was able to boot. Thanks a lot for the tips. Wish you all the best!

---

