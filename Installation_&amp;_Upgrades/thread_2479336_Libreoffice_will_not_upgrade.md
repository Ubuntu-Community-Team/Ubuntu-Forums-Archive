---
title: "Libreoffice will not upgrade"
date: 2022-09-21
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-09-21
When I use terminal, I get:
~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  fonts-opensymbol liblibreoffice-java libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk3 libreoffice-help-common libreoffice-help-en-us
  libreoffice-impress libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-style-breeze libreoffice-style-colibre
  libreoffice-style-elementary libreoffice-style-yaru libreoffice-writer
  libuno-cppu3 libuno-cppuhelpergcc3-3 libuno-purpenvhelpergcc3-3 libuno-sal3
  libuno-salhelpergcc3-3 libunoloader-java python3-uno uno-libs-private ure
  ure-java
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.

They will not upgrade with Synaptic.  It makes the upgrades, but "Apply" is grayed out.

---

### Post by &amp;KyT$0P# on 2022-09-21
Those are phased updates that your system has not yet been phased into.  You'll get them eventually if the phasing in continues.

---

### Post by ian-weisser on 2022-09-21
You can see for yourself whether or not an upgrade is phasing:

```

$ apt-cache policy libreoffice
libreoffice:
  Installed: (none)
  Candidate: 1:7.3.6-0ubuntu0.22.04.1
  Version table:
     1:7.3.6-0ubuntu0.22.04.1 500 **(phased 70%)**
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
     1:7.3.2-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```

---

### Post by cigtoxdoc on 2022-09-21
Thank you very much for the help.

John

---

### Post by cigtoxdoc on 2022-09-22
Solved, Upgrades now completed.

---

