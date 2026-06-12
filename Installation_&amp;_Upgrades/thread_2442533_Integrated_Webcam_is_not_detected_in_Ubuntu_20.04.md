---
title: "Integrated Webcam is not detected in Ubuntu 20.04"
date: 2020-05-04
forum: Installation &amp; Upgrades
---

### Post by akromi on 2020-05-04
Hi Support Team,
After Ubuntu 20.04 installation, no integrated webcam is detected on Zoom or cheese or skype.These issue's also exists in Ubuntu 19.10 also.
```
uname -a
Linux akromi 5.4.0-28-generic #32-Ubuntu SMP Wed Apr 22 17:40:10 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```
Laptop Model
Lenovo Miix 320-10ICR - Type 80XF
```
akromi@akromi:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0a2a Intel Corp.
Bus 001 Device 015: ID 048d:8911 Integrated Technology Express, Inc. USB2.0 Hub
Bus 001 Device 019: ID 1ea7:0064 SHARKOON Technologies GmbH
Bus 001 Device 014: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
akromi@akromi:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 20.04 LTS
Release: 20.04
Codename: focal
akromi@akromi:~$
```
Please advise for resolving this bug where integrated webcam is detected on zoom or cheese or skype.

---

### Post by fyfe54 on 2020-05-04
I just had this using a private label version of zoomand solved it using keyboard combo for turning webcam on/off - in my case Fn+F10. Yours may be different.  Press the combo, start Cheese or similar.  If no video, close Cheese, press combo again and restart Cheese.  Worked for me.

---

