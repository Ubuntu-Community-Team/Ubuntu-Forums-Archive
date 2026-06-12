---
title: "Cannot Install Feisty: No HDD detected"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by Janissary on 2007-05-12
Hi,
I've just purchased a new PC:

Intel Core2Duo E6600
Gigabyte DS3 Mainboard with JMicron SATA Controller
320GB WD SATAII 
2GB DDR2 Ram

I've read that linux was not good with jmicrons but, in other topics and launchpad bugs it says JMicron is working with 2.6.20... so what's the problem ?

---

### Post by confused57 on 2007-05-12
I don't have a JMicron chipset, but I recently installed SimplyMepis and there was an option to install on a JMicron chipset pc.  Here's a thread in the Mepis forums that you might want to read:
[http://www.mepislovers.org/forums/showthread.php?t=6250&highlight=JMicron](http://www.mepislovers.org/forums/showthread.php?t=6250&highlight=JMicron)

Someone also mentioned they successfully installed Sabayon.

Sorry I can't help your with installing Ubuntu.

---

### Post by Janissary on 2007-05-12
Thanks for your reply, but I need to install Ubuntu =)

---

### Post by otchie1 on 2007-05-15
Yeah, Feisty seems to blow when it comes to SATA.

I have an Asus M2N-SLi that uses NVidia MCP55 SATA controller and feisty refuses to see /dev/sda so it isn't just a jmicron problem. (The board does have a Jmicron controller but only for RAID and that is all turned off in BIOS - the disk is attached to the MCP).

I was forced back down to Edgy.

---

### Post by otchie1 on 2007-10-07
Best bit of 6 months later and the problem still hasn't been addressed. Same problems in Gutsy with MCP55 SATA as with Feisty, I guess the devs don't use MCP55 SATA :mad:

---

