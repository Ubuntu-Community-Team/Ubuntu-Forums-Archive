---
title: "how to install wubi while offline?"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by naj690 on 2011-02-28
i installed ubuntu normally before but due to some problems i uninstalled it. i want to install using wubi this time but cannot install while online. i dont want to install the normal way bcoz the last time i uninstalled it my window cannot boot. so how to install wubi while offline? i already got the iso

p/s: yeah.. i know.. too many word "install"

---

### Post by bcbc on 2011-02-28
Either from a CD you burn from that ISO or see [How do I install Wubi on a machine with no Internet connection?]("https://wiki.ubuntu.com/WubiGuide#How do I install Wubi on a machine with no Internet connection?")

---

### Post by naj690 on 2011-03-01
i already got both of them on the same folder but wubi still want to download from internet

---

### Post by bcbc on 2011-03-01
1. The wubi.exe may not match the release of the ISO.

2. It still checks the md5sum if you're connected to the net and will reject it if the downloaded ISO is invalid. 

Post the name of the .iso you downloaded and the log file (wubi-xx.xx-revxxx.log from the %temp% directory) if you need more help.

---

