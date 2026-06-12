---
title: "Ho Hum... upgrade failed......"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by timeoff on 2005-02-15
Using using warty and synaptic I did the usual update then install and received the lastest kernel security upgrades with no apparent errors (well I wasn't paying a great deal of attention, but I didn't notice anything out of the ordinary!).
 
Foolishly I then rebooted and found myself without my wireless connection and no graphical display....... Having got my eth0 link going again I tried to use apt-get to install the linux-restricted-modules-2.6.686 which I assumed was needed to get the nvidia drivers (and wireless - madwifi) back again.  I get the error message 

"the following packages have been kept back linux-restricted-modules-2.6.686
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded"

when I try an apt-get upgrade.

Also tried apt-get install nvidia-glx but it reports nvidia-glx is the latest version.

So am reduced to booting from XP  :-?

Presumably the latest kernel security fixes have done something unpleasant to the nvidia and madwifi modules. Any suggestions on what to try next before I go back to reinstalling from scratch?

Thanks in anticipation..... :)


Alex

---

### Post by pavan on 2005-02-15
Same problem here. Would appreciate some help.

Pavan

---

### Post by s.deleeuw on 2005-02-15
[http://ubuntuforums.org/showthread.php?t=15579](http://ubuntuforums.org/showthread.php?t=15579)
[http://ubuntuforums.org/showthread.php?t=15563](http://ubuntuforums.org/showthread.php?t=15563)
[http://ubuntuforums.org/showthread.php?t=15538](http://ubuntuforums.org/showthread.php?t=15538)

Sander

---

### Post by pavan on 2005-02-15
Thanks Sander. I booted off my old kernel for now. Will wait till the broken package is fixed.

Pavan

---

