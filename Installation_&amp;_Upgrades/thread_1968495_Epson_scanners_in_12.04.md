---
title: "Epson scanners in 12.04"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by everytimeref on 2012-04-29
Does anyone know how to get Epson scanners (mine is a v30) working on 12.04?

---

### Post by blitzit on 2012-04-29
I have a Canon LiDE 110 and it worked straightaway with Simple Scan. Didn't need any drivers. Did you try it out?

---

### Post by everytimeref on 2012-04-29
Yeah I've tried it. I'va also tried Epsons own Iscan, but no joy. I scan worked under natty

---

### Post by everytimeref on 2012-04-29
I Remembered.

In addition to the Iscan and I scan data files from epson, you also need the interpreter 

[http://linux.avasys.jp/drivers/iscan/plugins/esci-interpreter-gt-f720_0.0.0-1_amd64.deb](http://linux.avasys.jp/drivers/iscan/plugins/esci-interpreter-gt-f720_0.0.0-1_amd64.deb)

---

### Post by makitso on 2012-04-29
Was this a clean install or an  upgrade?
Have you installed xsane?
What is the results of the command scanimage -L

---

### Post by everytimeref on 2012-04-29
it is a clean intall. I've got it working now by installing Epson Iscan epson Iscan data (available as debs from Epson website) and the interpretter mentioned above.

Thanks for the help.

---

