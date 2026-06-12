---
title: "Upgradeing from dapper to edgy"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by kampsuniahv on 2006-10-04
I tried to upgrade from dapper to edgy, but it ended with some errors. and now my Package manager wont work. And it says that the error was: Error: BrokenCount > 0.

Any help

---

### Post by Kateikyoushi on 2006-10-04
I saw a similar case.

Copy this to a terminal

```
sudo apt-get install -f
```

---

### Post by kampsuniahv on 2006-10-04
```
kasutaja@Arvut:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  gnome-keyring-manager
The following packages will be REMOVED
  amule libgl1-mesa-dev libgl1-mesa-dri libglu1-mesa-dev libsdl-net1.2-dev
  libsdl1.2-dev libwxgtk2.4-dev libwxgtk2.6-0 libxine-extracodecs
  libxine-main1 python-wxgtk2.6 ubuntu-desktop x-window-system-core xine-ui
The following NEW packages will be installed
  gnome-keyring-manager
0 upgraded, 1 newly installed, 14 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0B/162kB of archives.
After unpacking 65,8MB disk space will be freed.
Do you want to continue [Y/n]? y

```

```
debconf: Unable to initialise frontend: Kde
debconf: (Unable to load Qt -- is libqt-perl installed?)
debconf: falling back to frontend: Dialog
(Reading database ... dpkg: error processing libsdl-net1.2-dev (--remove):
 files list file for package `libxp6' is missing final newline
Errors were encountered while processing:
 libsdl-net1.2-dev
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by John.Michael.Kane on 2006-10-04
kampsuniahv dist-upgrading can be hairy. if you can your best off doing a clean install of edgy. (backing up what data you need)

---

### Post by liassic on 2006-10-17
So why include Adept in the distro?
Why include the possibility of upgrading?

As an end-user I don't want to have to re-install from scratch.
I want a clean upgrade that just works.

Personally, I'm lucky that I now have enough experience to "fiddle" about until I got the upgrade to complete successfully.

The whole point of Ubuntu to me is that it's meant to be easy.  Re-installing isn't easy.  Just my POV.  :D

---

