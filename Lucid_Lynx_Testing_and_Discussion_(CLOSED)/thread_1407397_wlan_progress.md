---
title: "wlan progress?"
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sartic on 2010-02-15
How's wlan progressing in lucid? Jaunty is faster and better than Karmic on my toshiba notebook (ath 5k1). I will try alpha3 on 25th if there is any progress (real words will be correction of this regression :)

---

### Post by baizon on 2010-02-15
+1

Hope my problem will be fixed.

[http://ubuntuforums.org/showthread.php?t=1309703]("http://ubuntuforums.org/showthread.php?t=1309703")

---

### Post by sartic on 2010-02-17
no progress? i am dissapointed,

---

### Post by Ibidem on 2010-02-18
It all depends on the driver/card.
AR5007+ath5k is working decently here.
Which card do you have?

---

### Post by sartic on 2010-02-18
Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

old ath_pci works great, new karmic ath5k slow or can not work widthout backport kernel modules

---

### Post by Ibidem on 2010-02-18
That's madwifi,
[http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz)
is the one version with proprietary HAL that *might* work with the latest kernel.
You'd have to build it yourself.
madwifi-hal might work alright, but has its own HAL version that may or may not work as well.

Ibidem

---

### Post by sartic on 2010-02-19
Aha, that's why ubuntu killed it (hal).
Only reason to kill hal was fast boot. As desktop user I prefer good (w)lan over faster boot. Now my notebook boots in 40s. Only 20s less than Intrepid on same machine.
Do not believe that Lucid be near 30s.

---

### Post by Ibidem on 2010-02-19
Different HAL, stands for the same thing (hardware abstraction layer).
Madwifi's HAL is a proprietary (binary) interface to the network card, without which the driver won't build.
The HAL that was removed from Lucid is an open-source library+daemon that deals with all the hardware on your PC.
It was replaced with other stuff.

If you compile madwifi, that *should *make the network work better.

---

### Post by sartic on 2010-02-21
I know that, but it is mess. And I have now philosophy if it can not be done through click do not do it. Example, my ex win users r converted becuase "wanna do it, click it". If it is not in synaptic or deb i won't except it. My time is precious ;)

ps: I just stick my older atheros pcmcia and work in Karmic (problem is only 2 remember to plug in :)

---

### Post by sartic on 2010-03-21
beta 1 works out of box as jaunty on same machine. hooray ;)

---

### Post by baizon on 2010-03-24
Nice, thanks for the info. Will upgrade to Lucid then :)

---

### Post by sartic on 2010-03-25
Wait for beta 2 at least if u have notebook! Everything works except wake up from sleep for me.
ps: i see no gui plymouth (but who cares ; , i have 30s rock solid boot)

---

