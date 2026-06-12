---
title: "Upgrade from 6.10 to 7.04 broken- Averatec Notebook"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by tom_in_co on 2007-04-28
I have an Averatec 3200 Notebook with a mobile Athlon XP-M200+ chip, 512MB RAM and an integral 802.11g wireless unit. Edgy (6.10) installed like a dream- runs great. When 7.04 came out, I ran the upgrade (from the Update Manager)- after doing the install, a reboot got me the slowest reboot in history. The mouse chunks across the screen and after several frustrating minutes I could login- however the login never completes. I reinstalled from a live CD, vice the network upgrade- same results. I ended up having to reinstall Edgy. I've looked at all the threads that seemed relevant, but have found no explicit reason or fix.... does anyone have a similar problem and perhaps a solution? Thanks!!

---

### Post by dborko on 2007-05-04
Exactly the same symptoms, I have tried a variety of strategies to install, nothing seems to fix the problem

---

### Post by bdwill on 2007-10-17
Bump!

Anyone have an idea on how to resolve this issue? Has anyone installed 7.10 on the Averatec 3200 series yet?

---

### Post by paul_sc1 on 2007-10-20
Same problem here. This is my first search since ripping 7.10, so, maybe there is still an answer in the forums.

I really want to try out 7.10 x/k/ubuntu, but unable to boot on my averatec av3270-eh1. I have tried a couple of boot commands I have seen in on the net, but still no go. :(

I should add...I generally have no problems at all with a few other distros such as puppy, pclinuxos and mepis 7b, but, I would like to try ubuntu.

---

### Post by bdwill on 2007-10-23
On the GRUB manager, select e to edit the kernel line and add the following new line:

```
acpi=noirq
```

I'm not sure what it does (found it on another site) and it works great! Also, I never managed to keep that line added to the kernel parameters. I assume once you're in Ubuntu, it's quite simple.

Unfortunately, after upgrading to 7.10, the wireless doesn't work anymore. It has an ip address but it says Destination Host Unreachable when I try to ping my router.

If anyone can help with this, I would great appreciate it.

---

### Post by smeger on 2008-01-12
I have gotten 7.10 working on my Averatec 3200 with only a few minor problems. I had to use the text installer on the alternative CD for unknown reasons. The only thing I have left to do is fix the problem with the wireless driver; I just need to figure out how to do it without my LAN card (its fried).

---

### Post by musicman247 on 2008-01-18
Let us know what you do to fix the wlan. It worked fine with Fiesty, but I can't get it to work with Gutsy.

---

