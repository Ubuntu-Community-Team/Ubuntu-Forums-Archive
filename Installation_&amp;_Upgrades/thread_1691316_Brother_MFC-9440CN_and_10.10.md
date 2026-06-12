---
title: "Brother MFC-9440CN and 10.10"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2011-02-19
I can get the printer working.  Scanner is the problem.  I added the lines to the 40-libsane.rules file that were suggested for 10.04 but I get the following error with xsane

Failed to open device 'brother3:bus3;dev1: Invalid argument

Need help here as my second office person is using my Ubuntu 10.10 PC

John

---

### Post by cigtoxdoc on 2011-02-27
I received some additional instruction from Brother.  Xsane will work when I am logged in as root.  It will not work from other user directories.

John.

---

### Post by cigtoxdoc on 2011-03-12
Scanner on MFC-9440CN will work only from "root", and it works perfectly from "root".  All files set up the same as they would be in Ubuntu 10.04 LTS.  However, it will not work from user accounts in 10.10.  Apparently, Xsane and SimpleScan cannot communicate with scanner when not in "root".

How are user accounts in 10.10 different from those in 10.04 LTS?

Either techs at Brother USA do not know the answer or they have not tried to fix problem/

John

---

### Post by cigtoxdoc on 2011-05-01
Probably the only reason to upgrade to 11.04.  My Brother MFC-9440CN will now scan from regular users, not just root.

John

---

