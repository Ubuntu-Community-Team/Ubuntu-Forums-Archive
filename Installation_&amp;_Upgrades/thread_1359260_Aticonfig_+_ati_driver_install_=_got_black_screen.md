---
title: "Aticonfig + ati driver install = got black screen?"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by daok on 2009-12-19
Hi,

I just formated a new partition and here is the complete command executed:

1) sudo apt-get update
2) sudo apt-get install xorg-driver-fglrx
3) sudo aticonfig --initial
4) Go on internet and download ati driver installer and catalyst
5) sudo sh ./ati-driver-installer..... .run
This is poping an installation Wizard, I do Next Next Next with the automatic installer.
This require a reboot.

Rebooted, I see the Kubuntu loading and then BOOM black screen.

Questions:
How to fix that without simply getting back the old xorg.conf file?
Why it's so complicated???

---

### Post by Mark Phelps on 2009-12-19
This happens most often when folks force the installation of the wrong video driver.  Since you didn't mention which ATI card/chip you're using, we don't know if you installed the wrong driver.

But, to remove that driver, follow the instructions below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

