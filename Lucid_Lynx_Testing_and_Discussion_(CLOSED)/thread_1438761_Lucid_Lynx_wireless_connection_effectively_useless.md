---
title: "Lucid Lynx wireless connection effectively useless, deceptive"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by joshuadugie on 2010-03-25
Since about 8.04 or 8.10, perhaps when Ubuntu switched over to  NetworkManager, my wireless connection has randomly dropped its  association with the access point, about every ten minutes.  For a  while, the connection will just die, then it will be detected and  NetworkManager will re-authenticate and re-associate.

In Lucid Lynx, this problem is now much more frequent (often exactly  every two or four minutes) and now Ubuntu does not report that the  connection has dropped.  Instead, it re-associates in the background,  eventually connecting to the access point again, all behind the scenes.   Thus, the only thing that has changed, aside from the greater  frequency, is that Ubuntu now doesn't report that it has dropped the  connection, which seems deceptive from previous versions.

I have attached the output of dmesg, which shows the problem (I have altered the bssid):

```
wlan0: deauthenticating from 00:00:00:00:00:00 by local choice (reason=3)
```Does anyone know how to keep my wireless card from dropping the connection all the time?  It should be noted that Windows Vista/7 does not suffer from this problem.

---

### Post by Naggobot on 2010-03-25
No help from here unfortunately, but some comforting on that you are not alone with this problem. See if some of these is same as yours and give feedback to development. Hopefully someone on this forum already has a work around

[https://bugs.launchpad.net/linux/+bug/279102](https://bugs.launchpad.net/linux/+bug/279102)
[https://bugs.launchpad.net/network-manager/+bug/37821](https://bugs.launchpad.net/network-manager/+bug/37821)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425455](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425455)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/361823](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/361823)
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/493342](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/493342)
[https://bugs.launchpad.net/ipw3945/+bug/163236](https://bugs.launchpad.net/ipw3945/+bug/163236)
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/220103](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/220103)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225851](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225851)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298198](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298198)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360002](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360002)
[https://bugs.launchpad.net/ubuntu/+bug/375252](https://bugs.launchpad.net/ubuntu/+bug/375252)

I searched for wireless connection disconnects and picked these up from first page. 

Great thing about open source is that you actually can file a bug report and try to participate in both promoting the fact that there is a problem and helping in supplying relevant information for developers. I personally do love this feature since it makes bugs a bit more tolerable. :)

---

