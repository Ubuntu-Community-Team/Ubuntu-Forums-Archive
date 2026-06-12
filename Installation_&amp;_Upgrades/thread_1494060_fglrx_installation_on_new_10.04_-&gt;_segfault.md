---
title: "fglrx installation on new 10.04 -&gt; segfault"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by Zebro on 2010-05-26
Hi, 

I have a new ubuntu 10.04 amd64 installation (kernel 2.6.32-22) with a Mobility Radeon HD 3650. I tried to install the fglrx drivers from ati via the Software-Center and via apt-get. After installation, when starting the ATI CCC the following error message (sorry in german) appears:

"Beim Initialisieren der Catalyst Control Center Linux-Version ist ein Problem aufgetreten.  Mögliche Gründe dafür sind:
Es ist kein ATI-Grafiktreiber installiert oder der ATI-Treiber funktioniert nicht ordnungsgemäß.
Bitte installieren Sie den richtigen Treiber für Ihre ATI-Hardware oder verwenden Sie den Befehl aticonfig."

Translation: Driver is either not correctly installed or it does not work properly.

If I try to execute fglrxinfo in the console I get a "segmentation fault".
I think I do not have to say that the driver does not work. I have removed and reinstalled the driver several times.

Anybody encountered something similar or knows how to deal with this?

Zebro

---

### Post by Zebro on 2010-06-01
I still have this problem. No one any idea?

---

### Post by obscurant1st on 2010-06-03
same issue here!! :(

---

### Post by TBABill on 2010-06-03
Try here [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by Chemtox on 2010-06-09
Looks like the driver is not being used at all. The automated installation sometimes doesn't creates an xorg.conf file, no idea why, so X keeps on using the xorg drivers.

You can check which driver are you running executing this from a terminal inside X:

```
perl -n0077 -e 'print "Using driver $1 v$3 by $2.\n" while /Module (radeon|fglrx|intel|nvidia|nv|vesa): vendor="([^"]+)"\n.*version = (\S+)/img;' /var/log/Xorg.${DISPLAY:1:1}.log
```

If the result is not fglrx, try ```
sudo aticonfig --initial
``` to create a basic xorg.conf, and restart X.

---

