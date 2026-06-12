---
title: "update wants to remove 31 packages, no way!!"
date: 2009-06-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-06-25
Wondering why it wants to remove all these packages?? 
And as usual, I didn't let it.
```
[B]The following packages will be REMOVED:
  abiword{u} abiword-common{u} abiword-help{u} abiword-plugin-grammar{u} abiword-plugin-mathview{u} 
  gnumeric{u} gnumeric-common{u} gnumeric-doc{u} latex-xft-fonts{u} libaiksaurus-1.2-0c2a{u} 
  libaiksaurus-1.2-data{u} libaiksaurusgtk-1.2-0c2a{u} libempathy-gtk23{u} libempathy25{u} 
  libgda3-3{u} libgda3-bin{u} libgda3-common{u} libgdome2-0{u} libgdome2-cpp-smart0c2a{u} 
  libgoffice-0-8{u} libgoffice-0-8-common{u} libgtkmathview0c2a{u} liblink-grammar4{u} libots0{u} 
  libt1-5{u} libwv-1.2-3{u} link-grammar-dictionaries-en{u} mono-2.0-runtime{a} mono-common{a} [/B]
```

---

### Post by douham on 2009-06-25
Hi DougieFresh4u, we've all been hanging for the mono upgrades for a few days [http://ubuntuforums.org/showthread.php?t=1195859]("http://ubuntuforums.org/showthread.php?t=1195859").
Try; "sudo aptitude safe-upgrade" it'll show whats been held back because of dependancy issues, but you might be able to get some updates.

My names Doug too.

---

### Post by Bucky Ball on 2009-06-25
Because as usual, you didn't let it! You probably have a heap of updates backed up and you are doing yourself no favours as some of them are security updates.

You will find it wants to remove them so it can replace them with the upgraded, newer versions of the same file.

---

### Post by DougieFresh4U on 2009-06-25
> **Bucky Ball said:**
> Because as usual, you didn't let it! You probably have a heap of updates backed up and you are doing yourself no favours as some of them are security updates.

You will find it wants to remove them so it can replace them with the upgraded, newer versions of the same file.

I understand what you are saying, but there is no replacement for 'abiword'  and others that it wants to remove. I do carefully look through what it wants to 'update' and 'upgrade' to see if it is replacing packages that it wants to remove.

---

### Post by Bucky Ball on 2009-06-25
> **DougieFresh4U said:**
>  there is no replacement for 'abiword' 

Except the latest version of Abiword. Check the one it wants to download against the one you have installed and see if this is the case.

---

### Post by DougieFresh4U on 2009-06-25
> **Bucky Ball said:**
> Except the latest version of Abiword. Check the one it wants to download against the one you have installed and see if this is the case.

```
[B]The following NEW packages will be installed:
  libempathy-gtk24{a} libempathy26{a} libgdl-1-2{a} libmagick++1{a} libtag1-vanilla{a} tcl8.4{a} 
  tix{a} tk8.4{a} 
The following packages will be REMOVED:
  abiword{u} abiword-common{u} abiword-help{u} abiword-plugin-grammar{u} abiword-plugin-mathview{u} 
  gnumeric{u} gnumeric-common{u} gnumeric-doc{u} latex-xft-fonts{u} libaiksaurus-1.2-0c2a{u} 
  libaiksaurus-1.2-data{u} libaiksaurusgtk-1.2-0c2a{u} libempathy-gtk23{u} libempathy25{u} 
  libgda3-3{u} libgda3-bin{u} libgda3-common{u} libgdl-1-0{u} libgdome2-0{u} 
  libgdome2-cpp-smart0c2a{u} libgoffice-0-8{u} libgoffice-0-8-common{u} libgtkmathview0c2a{u} 
  liblink-grammar4{u} libots0{u} libt1-5{u} libwv-1.2-3{u} link-grammar-dictionaries-en{u} 
  mono-2.0-runtime{a} mono-common{a} mono-jit{a} planner{u} 
The following packages will be upgraded:
  aspell-en balanzan-theme busybox-initramfs byobu chromium-browser cups-driver-gutenprint ecj 
  ecj-gcj empathy fakeroot fast-user-switch-applet fglrx-modaliases firefox-3.6 
  firefox-3.6-branding firefox-3.6-dbg firefox-3.6-dev firefox-3.6-gnome-support foo2zjs 
  foomatic-db-engine foomatic-filters gdm-balanzan-theme gnome-balanzan-theme gnome-nettool 
  gnome-panel gnome-panel-data gnome-panel-dbg google-chrome-unstable grub-common 
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gtk-balanzan-theme 
  icon-balanzan-theme inkscape kbd libasound2 libaudiofile0 libcairo2 libecj-java libecj-java-gcj 
  libempathy-common libempathy-gtk-common libgdl-1-common libgksu2-0 libgl1-mesa-dri 
  libgl1-mesa-glx libglu1-mesa libgutenprint2 libmono-corlib2.0-cil libmono-data-tds2.0-cil 
  libmono-data2.0-cil libmono-getoptions2.0-cil libmono-posix2.0-cil libmono-security2.0-cil 
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil 
  libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libnss-mdns libpanel-applet2-0 
  libpurple-bin libpurple0 libsnmp-base libsnmp15 libtag1c2a linux-backports-modules-karmic 
  memtest86+ mesa-utils mono-2.0-gac mono-gac mono-runtime netbase pidgin pidgin-data 
  python-eggtrayicon python-gdl python-gksu2 python-gnome2-extras python-gtkhtml2 
  python-gtkmozembed python-gtkspell python-software-properties python-telepathy rdesktop screen 
  software-properties-gtk splix telepathy-butterfly thunderbird-3.0 thunderbird-3.0-dev 
  thunderbird-3.0-gnome-support udev-extras update-manager update-manager-core 
  wallpaper-balanzan-theme xserver-common xserver-xorg-core xserver-xorg-video-nv xulrunner-1.9.2 
  xulrunner-1.9.2-gnome-support 
102 packages upgraded, 8 newly installed, 32 to remove and 0 not upgraded.
[/B]
```

---

### Post by MacUntu on 2009-06-25
Output of ```
sudo apt-cache policy abiword
```?

---

### Post by taavikko on 2009-06-25
> **MacUntu said:**
> Output of ```
sudo apt-cache policy abiword
```?

Offtopic-->
Doesn't require "sudo" to work.

sudo is used little too much, even on commands that doesn't require them.

---

### Post by DougieFresh4U on 2009-06-25
> **MacUntu said:**
> Output of ```
sudo apt-cache policy abiword
```?

> **taavikko said:**
> Offtopic-->
Doesn't require "sudo" to work.

sudo is used little too much, even on commands that doesn't require them.

abiword:
  Installed: 2.6.8-5ubuntu1
  Candidate: 2.6.8-5ubuntu1
  Version table:
 *** 2.6.8-5ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status

---

### Post by nyarnon on 2009-06-25
Lets face it, these are the kind of troubles you run ito if you alfatest in a production environment. Test it, do the upgrade and then if anything is wrong file a bug report. Thats what testing is about.

---

### Post by ad_267 on 2009-06-25
Just give it a bit of time, this kind of thing often happens in an alpha version. When the next lot of updates come the problem will probably be sorted and they won't need to be removed.

---

### Post by ELD on 2009-06-25
> **Bucky Ball said:**
> Except the latest version of Abiword. Check the one it wants to download against the one you have installed and see if this is the case.

Wrong it will be in the packages to be upgraded section, removed packages are removed as the name suggests.

---

### Post by MacUntu on 2009-06-25
> **taavikko said:**
> Offtopic-->
Doesn't require "sudo" to work.

sudo is used little too much, even on commands that doesn't require them.

That's the "sudo apt"-combination that lives in my fingers. I often do "sudo apt-get source ..." and end up with files owned by root in my home folder. :D

---

