---
title: "Lubuntu set up dual booting with Ubuntu"
date: 2013-05-19
forum: Installation &amp; Upgrades
---

### Post by rezbd on 2013-05-19
I have Lubuntu 11.10 and Ubuntu 12.04 LTS installed on my netbook([LEFT][COLOR=#4E5665][FONT=Helvetica]Intel® Atom™ CPU N455 @ 1.66GHz × 2" with 1 MB of RAM). [/FONT][/COLOR][/LEFT]I want to upgrade my Lubuntu 11.04 to Lubuntu 13.04. As my internet is very slow, I cannot do 11.10 > 12.04 > 12.10 > 13.04 upgrade. So, I might have to install Lubuntu 13.04 manually. How can I replace my Lubuntu 11.04 with Lubuntu 13.04 by keeping ubuntu 12.04 LTS intact? what's the procedure to do that?

---

### Post by jamesisin on 2013-05-19
If you have one installation for Ubuntu 12.04 and a separate installation on different partitions for Lubuntu 11.10, then you should be able to install Lubuntu 13.04 over Lubuntu 11.10 without interfering with Ubuntu 12.04.

Two things...

First, you will want to choose wisely when telling Lubuntu where to install the new version (so you don't accidentally install it over Ubuntu 12.04).

Second, you will want to run *sudo update-grub* once you boot into your new system.

---

