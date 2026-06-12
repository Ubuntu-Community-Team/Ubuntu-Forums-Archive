---
title: "[SOLVED] Partial Upgrade has broken radio"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by Peter09 on 2008-06-01
The problems with the upgrades of the last few days have broken my radio link. I have a Toshiba Sattelite which uses the ipw2200 driver. I have never hadtrouble with this driver through Fiesty or Gutsy or Hardy.

Yesterday my laptop froze and on reboot - no wireless enabled.

I have managed to do some work :

```
sudo rmod -f ipw2200
sudo modprobe ipw2200 disable=0
```

After this doing 

```
lshw -C network
```
shows the device is setup, it has an interface (eth1) and appears to be configured except it shows a statement.

> wireless=radio off

I just cannot get the radio back on. Any help would really be appreciated.

PC

---

### Post by Peter09 on 2008-06-01
A little more information.

In /etc/network/interfaces my wireless is shown as wlan0

In lshw -C network its shown as eth1

however changing wlan0 to eth1 does not make any difference.

PC

---

### Post by zvacet on 2008-06-01
See if [this]("http://ubuntuforums.org/showthread.php?t=684495") can be of any help to you.

---

### Post by Peter09 on 2008-06-01
Thanks Zvacet but I could not find anything that helped.

PC

---

### Post by Peter09 on 2008-06-02
Anyone else have any ideas on this,  just cannot seem to get anywhere.

PC

---

