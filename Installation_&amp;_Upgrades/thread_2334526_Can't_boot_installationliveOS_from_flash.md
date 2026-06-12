---
title: "Can't boot installation/liveOS from flash"
date: 2016-08-20
forum: Installation &amp; Upgrades
---

### Post by anawizowski on 2016-08-20
Hey!

I recently bought a new PC and want to install Ubuntu as a secondary OS on it, but can't load the installation/liveOS from my flash drive. After the ubuntu loading screen, everything turns black and I can't do anyhing. The installation media is not corrupted, because it boots perfectly on my laptop.

The PC specs are these, if it may help ( I think it might be fault of thegpu? ):
MOBO: MSI b150m,
CPU: i5-6600,
GPU: MSI r9 390.

---

### Post by sudodus on 2016-08-20
It might help with the boot option ***nomodeset***. But if you want/need to run Radeon graphics with a proprietary driver to make the graphics work, you should start by installing ***Ubuntu 14.04.1 LTS***, because [I think] there is no suitable proprietary driver for 16.04.1 LTS.

Ubuntu version 14.04.1 has long time support until April 2019.

See this link if you need help to add a boot option: [Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by anawizowski on 2016-08-20
Thank you, I will try with 14.04.1.

---

