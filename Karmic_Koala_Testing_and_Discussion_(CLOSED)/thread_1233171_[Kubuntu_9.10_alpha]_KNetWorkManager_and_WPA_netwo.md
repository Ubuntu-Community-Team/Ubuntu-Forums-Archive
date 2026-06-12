---
title: "[Kubuntu 9.10 alpha] KNetWorkManager and WPA networks"
date: 2009-08-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by skullmunky on 2009-08-06
Using the Kubuntu 9.10 alpha live cd, I can't connect to my home network using WPA.  KNetworkManager just repeatedly asks for the key, and eventually fails to connect.  I recall a similar bug in previous recent releases of Kubuntu; one workaround was running kwalletd first.  I tried that, no change.  I recall the other suggested workaround was just to install wicd instead, which is what I have running on my 9.04 install.  I can't try that with the live CD, though, a wireless connection is all I have.  Is this 

(a) actually just a quirk of my setup
(b) just a quirk of this alpha
(c) a known bug in knetworkmanager actively being tracked in kubuntu or upstream
(d) nothing to worry about because knetworkmanager will be replaced with Wicd in the final release?

btw: other than that little network problem, the alpha live CD already looks great.  Everything about the desktop is definitely a good bit more polished and runs noticeably faster than my KDE 4.2;  dolphin launches faster, window refresh is smoother, the new theme is smooth and lovely.  Lots of other stuff isn't functional but visually it's a treat.

---

### Post by taavikko on 2009-08-06
C is the correct answer. With a twist, it's not knetworkmanager, different package
Might want to use search... [https://bugs.launchpad.net/bugs/392593](https://bugs.launchpad.net/bugs/392593)

---

### Post by vishalrao on 2009-08-06
yup, please answer/respond to the call for testing:

[https://lists.ubuntu.com/archives/kubuntu-devel/2009-July/003100.html](https://lists.ubuntu.com/archives/kubuntu-devel/2009-July/003100.html)

[https://wiki.kubuntu.org/Kubuntu/PlasmaWidgetNetworkManager/0.0+svn1002781-0ubuntu1~ppa1](https://wiki.kubuntu.org/Kubuntu/PlasmaWidgetNetworkManager/0.0+svn1002781-0ubuntu1~ppa1)

---

### Post by skullmunky on 2009-08-06
Thanks!  I'll try that out.  Although first will have to look up again how to get packages to a machine with no internet.

Someone should make a nice visual diagram of the whole network stack ... between NetworkManager, nm-applet, KNetworkManager, plasma-widget-network-manager, wicd, wpa_supplicant, ndiswrapper, etc., I need a scorecard ... :)

---

### Post by vishalrao on 2009-08-06
> **skullmunky said:**
> Thanks!  I'll try that out.  Although first will have to look up again how to get packages to a machine with no internet.

Someone should make a nice visual diagram of the whole network stack ... between NetworkManager, nm-applet, KNetworkManager, plasma-widget-network-manager, wicd, wpa_supplicant, ndiswrapper, etc., I need a scorecard ... :)

:lolflag:

luckily i have a spare ethernet cable to hook up my tablet to my router...

---

