---
title: "After mygrating to 22.04 messages lost packages now only teminal access no gui"
date: 2023-10-04
forum: Installation &amp; Upgrades
---

### Post by jfvfin on 2023-10-04
Hope someone could help, have the same install since ubuntu 9, since then i have been migrating and after the last upgrade to 22.04 I started having many issues one of them unmet dependencies. After following many threads trying to solve this issue lost GUI and have now only terminal access.

Trying to re-install GUI I get the following message:

sudo apt-get install --reinstall ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libwebkit2gtk-4.0-37 : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not installable
 ubuntu-desktop : Depends: gnome-control-center but it is not installable
                  Recommends: libwmf0.2-7-gtk but it is not going to be installed
                  Recommends: thunderbird but it is not installable
                  Recommends: thunderbird-gnome-support but it is not installable
 ubuntu-desktop-minimal : Depends: gnome-control-center but it is not installable
                          Recommends: libwmf0.2-7-gtk but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by aljames2 on 2023-10-04
Did you say you are on your original install of Ubuntu 9, and been upgrading ever since?  9 was not even an LTS release, and there have been 7 LTS releases since.  Perhaps you meant "19", which also was not an LTS release.  A complete fresh reinstall is your answer.  Do you have backups?

---

### Post by MAFoElffen on 2023-10-04
Please post the results of this:
```

awk '{print $0; exit}' /var/log/installer/media-info

```

---

