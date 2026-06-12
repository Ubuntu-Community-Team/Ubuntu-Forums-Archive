---
title: "Pentium 4 machine crazy slow on 12.04"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by triplemaya on 2012-05-12
Hi. I am trying to set up a p4 machine a dell dimension 3100 as a second pc. 1204 runs so slow it is not even possible to do set up work. It takes over 2 minutes to produce a terminal window from clicking on the icon! Simple. Off with ubuntu, on with xubuntu. But xubuntu will not work with the network card. I spend hours and hours and hours on this without success. I should have thrown the damn machine away, I could have begged enough money on the street to buy a working system in the time I have spent on this!
Ubuntu 12 is the obvious choice as all the hardware works on the spot. But there is this crazy slowness. I have done apt-get update and apt-get upgrade, but nothing helps. I used a 64 bit install as that is the version I use on my main pc, but I looked up this pc and it is supposed to be 64 bit ready. Maybe it is not and that is the problem? It has only half a gig of ram, but xp flies on it and so does xubuntu. But trying to get either the internal Buffalo card or the external tp usb network dongle to work with either has been a time sink of extraordinary proportions.

---

### Post by sudodus on 2012-05-12
> **triplemaya said:**
> ... But xubuntu will not work with the network card...
If your ubuntu and xubuntu are both 12.04, they have the same software under the hood to recognize and cooperate with hardware like wifi devices. So it should make no difference as far as I understand.

You can also do it like this: Install ***xubuntu-desktop*** into your 'vanilla' Ubuntu system, log out, change desktop environment clicking on the Ubuntu Logo symbol, select Xubuntu and log in again. Now you should have a more responsive desktop.

While doing this, you might also install ***lubuntu-desktop*** and test the ultra-light desktop environment LXDE.

And the hardware detection will be the same, because it does not depend on the desktop environment. If no go there, you need to check if your wifi chip is compatible with Ubuntu, see for example
[[COLOR="Red"]_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by triplemaya on 2012-05-12
> If your ubuntu and xubuntu are both 12.04, they have the same software under the hood to recognize and cooperate with hardware like wifi devices. So it should make no difference as far as I understand.

Tell me about it! I think this is very weird.

Many thanks for all this info - I didn't know I could install xubuntu that way; and presumably the system can't lose drivers in the process!!

(Clearly though the all the wireless is compatible with ubuntu as ubuntu 12 sees it all straight off and has no problem with it!)

---

### Post by sudodus on 2012-05-13
> **triplemaya said:**
> Tell me about it! I think this is very weird.

Many thanks for all this info - I didn't know I could install xubuntu that way; and presumably the system can't lose drivers in the process!!

(Clearly though the all the wireless is compatible with ubuntu as ubuntu 12 sees it all straight off and has no problem with it!)
Obviously you have observed different detection of the wireless device.

Maybe you have different versions of the core and some utility programs. There are (at least) two versions for 32-bit CPUs: non-pae and pae-enabled. The default version for Xubuntu is non-pae, while the default version for vanilla Ubuntu is pae-enabled. I did not think the hardware detection would be different, but maybe.

Another possibility is that your versions are not upgraded to the same date, so that there is slightly different code for hardware detection.

Anyway, it should be solved by installing xubuntu-desktop into a version, that recognizes you wireless device :-)

---

### Post by triplemaya on 2012-05-13
> **sudodus said:**
> Anyway, it should be solved by installing xubuntu-desktop into a version, that recognizes you wireless device :-)

Yes! Problem solved. Not only should but is! Thank you so much.

As a safety precursor I did download and install the 32 bit but it was every bit as slow and hopeless; but the xubuntu installed 'on top' sees the network fine and I so hugely prefer the interface anyway. (I am one of the many who REALLY don't get on with unity, or g3 as yet for that matter.)

---

### Post by sudodus on 2012-05-13
> **triplemaya said:**
> Yes! Problem solved. Not only should but is! Thank you so much ...
I'm glad it works for you now :KS

Please click on [COLOR="Red"]_Thread Tools_[/COLOR] at the top of this page and mark this thread as SOLVED

---

