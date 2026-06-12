---
title: "Wireless 2.6.31"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by infamousrev on 2009-09-12
I have been waiting for months now and still dont see any progress in the wireless of the 2.6.31 kernel.

This concerns the ath9k driver, on a asus eeepc 1000HE.

Downgrading my kernel to 2.6.28-10 fixed the problem, and wireless works perfect. However with this kernel the graphics become unbearably slow.

Even now when 2.6.31 is marked stable it has not been fixed.

Does anyone here know any workarounds?

Note: The exact same driver is used on my 2.6.28-10 and 2.6.31 kernel, however at the 2.6.28-10 it runs perfect, and on the 2.6.31 it runs horribly unstable.


>   *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wmaster0
                version: 01
                serial: 00:22:43:71:51:93
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.1.5 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:19 memory:fbef0000-fbefffff


---

### Post by infamousrev on 2009-09-12
lspci

01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by excogitation on 2009-09-12
Same here with a Sony Vaio P and AR928X

---

### Post by stonelinux on 2009-09-12
I have had the same issue.  I didn't have this problem on Karmic Koala alpha 3.
In my case Karmic Koala alpha 4 & 5 work fine until I turn on wireless, in about 6 minutes system locks up.  I have no problem when connected via eth0.

---

### Post by Smidley on 2009-10-03
Same here under 2.6.31.1.

```
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

I updated to 2.6.31.1 to fix video acceleration loss after running dual monitors with a TV and laptop display.  In other words, Compiz worked great [under 2.6.28-15.52] until I plugged in the TV via VGA cable.  After that, it seems like video acceleration has vanished.

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
```

---

### Post by darco on 2009-10-03
I just did a clean install of KK on a 3yr old Toshiba laptop (Satellite A105-S4254) and wireless was not detected on boot up. 
```
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```
Ran ndiswrapper -l and returned that I needed install the ndiswrapper-common app which I did...still no wifi.
ran this command ```
sudo apt-get install ndisgtk
```
and bam I was up and running.....

KK looks so nice...cant wait to have it run on my main system...

darco

---

### Post by praveenmarkandu on 2009-10-03
> **Smidley said:**
> Same here under 2.6.31.1.

```
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```



i have a broadcom bcm4315 network card. this blog post helped me. it should work for you as well. [http://paulphilippov.com/articles/restricted_modules_in_ubuntu_karmic_koala](http://paulphilippov.com/articles/restricted_modules_in_ubuntu_karmic_koala)

supposedly karmic doesnt do ubuntu-restricted-modules anymore and therefore somethings dont work out of the box. a step backwards for ubuntu if you ask me. they are not helping the cause

---

