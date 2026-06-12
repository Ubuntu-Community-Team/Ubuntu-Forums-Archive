---
title: "Unable to print - filter failed"
date: 2017-11-03
forum: Installation &amp; Upgrades
---

### Post by JKyleOKC on 2017-11-03
I don't print very often, so I can't pinpoint a time that the failure happened, but under 16.04.3 I'm suddenly unable to print to my Laserjet 1320, which worked just fine the last time I tried to use it. The error message is "filter failed" and I've searched for that, and tried many of the recommended cures -- but nothing seems to work, and the more I try, the worse things get. At the moment I'm trying to install the hplip package, which hangs up solid trying in install the build-essential dependency, apparently because the system is trying to load the "fakeroot" package from /media/cdrom rather than from the internet or the actual DVD in /media/jk but staying in a tight loop for as long as 10 minutes before I kill the task. The lsusb utility fails to show the printer at all. And because of the installed data, doing a clean install is not an immediate option for me, especially since I'm not certain that the printer itself may have failed. Suggestions?

---

### Post by kurt18947 on 2017-11-04
Is there some key combination for the printer that will print a self-test? I'm not sure about your printer but I have a Brother & a Samsung laser printer network connected. A live session of Ubuntu 17.10 will find them and do a driverless install and they do print. Would it be worth creating a 17.10 live USB to see if it finds your printer? That should at least help to isolate the problem I'd think.

---

### Post by JKyleOKC on 2017-11-04
I did a self-test first thing, and it worked fine. Finally solved the problem this morning: a new kitten had been romping in my computer room last week, and managed to pull the USB cable of the printer out of the hub -- which is almost hidden beneath the rats-nest of cabling behind that box. Plugging it back in brought everything back! failure of "lsusb" to show the printer made me suspect the cause, but visual inspection failed to show any unconnected plugs. Finally traced the cable by hand and found it hiding out of sight beneath a shelf!

---

### Post by kurt18947 on 2017-11-04
CATS!!!!  I know, we have 3 of the little furballs. But they can be adorable when it suits their purpose.

---

