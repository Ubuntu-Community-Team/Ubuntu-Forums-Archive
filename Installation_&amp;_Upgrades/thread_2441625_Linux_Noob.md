---
title: "Linux Noob"
date: 2020-04-25
forum: Installation &amp; Upgrades
---

### Post by drw1710 on 2020-04-25
I have recently installed Ubuntu 20.XXX  on this raspberry pi4 for a low buck folding at home rig and I am try hing to set it up. I would like to install Chrome but I get the following error and I have no idea how to correct it, Thank you in advance for your assistance.
The following packages have unmet dependencies:
 google-chrome-stable:amd64 : Depends: libappindicator3-1:amd64 but it is not installable
                              Depends: libasound2:amd64 (>= 1.0.16) but it is not installable
                              Depends: libatk-bridge2.0-0:amd64 (>= 2.5.3) but it is not installable
                              Depends: libatk1.0-0:amd64 (>= 2.2.0) but it is not installable
                              Depends: libatspi2.0-0:amd64 (>= 2.9.90) but it is not installable
                              Depends: libc6:amd64 (>= 2.16) but it is not installable
                              Depends: libcairo2:amd64 (>= 1.6.0) but it is not installable
                              Depends: libcups2:amd64 (>= 1.4.0) but it is not installable
                              Depends: libdbus-1-3:amd64 (>= 1.5.12) but it is not installable
                              Depends: libdrm2:amd64 (>= 2.4.38) but it is not installable
                              Depends: libexpat1:amd64 (>= 2.0.1) but it is not installable
                              Depends: libgbm1:amd64 (>= 8.1~0) but it is not installable
                              Depends: libgcc1:amd64 (>= 1:3.0) but it is not installable
                              Depends: libgdk-pixbuf2.0-0:amd64 (>= 2.22.0) but it is not installable
                              Depends: libglib2.0-0:amd64 (>= 2.39.4) but it is not installable
                              Depends: libgtk-3-0:amd64 (>= 3.9.10) but it is not installable
                              Depends: libnspr4:amd64 (>= 2:4.9-2~) but it is not installable
                              Depends: libnss3:amd64 (>= 2:3.22) but it is not installable
                              Depends: libpango-1.0-0:amd64 (>= 1.14.0) but it is not installable
                              Depends: libpangocairo-1.0-0:amd64 (>= 1.14.0) but it is not installable
                              Depends: libx11-6:amd64 (>= 2:1.4.99.1) but it is not installable
                              Depends: libx11-xcb1:amd64 but it is not installable
                              Depends: libxcb-dri3-0:amd64 but it is not installable
                              Depends: libxcb1:amd64 (>= 1.6) but it is not installable
                              Depends: libxcomposite1:amd64 (>= 1:0.3-1) but it is not installable
                              Depends: libxcursor1:amd64 (> 1.1.2) but it is not installable
                              Depends: libxdamage1:amd64 (>= 1:1.1) but it is not installable
                              Depends: libxext6:amd64 but it is not installable
                              Depends: libxfixes3:amd64 (>= 1:5.0) but it is not installable
                              Depends: libxi6:amd64 (>= 2:1.2.99.4) but it is not installable
                              Depends: libxrandr2:amd64 (>= 2:1.2.99.3) but it is not installable
                              Depends: libxrender1:amd64 but it is not installable
                              Depends: libxss1:amd64 but it is not installable
                              Depends: libxtst6:amd64 but it is not installable
                              Recommends: libvulkan1:amd64 but it is not installable
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ ^C

---

### Post by CatKiller on 2020-04-25
You can't install amd64 packages on a raspberry pi. The raspberry pi has an arm processor, a completely different instruction set.

---

