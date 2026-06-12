---
title: "How to upgrade 5.10 to 6.10?"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by daugirdas on 2006-10-26
Hi

I need to upgrade a fairly standard kubuntu / ubuntu 5.10 setup to the latest and greatest 6.10. I would really prefer to skip 6.06 since my network is rather slow (256 kbps ADSL). I am downloading alternate install kubuntu CD iso at the moment, and I have updated my sources.list accordingly.
When I run apt-get dist-upgrade I get a few package conflicts:
```
The following packages will be REMOVED:
  akode akode-mpeg amarok amarok-arts amarok-gstreamer amarok-xine base-config
  busybox-cvs-initramfs cupsys-driver-gimpprint-data gij-4.0 gnomemeeting hotplug
  hplip-base ifrename imake k3blibs kaffeine-gstreamer kde-guidance kdelibs-bin
  kdelibs4c2 kubuntu-desktop libarts1c2 libcupsys2-gnutls10 libdbus-1-1 libdbus-glib-1-1
  libgcj6 libgcj6-common libgksu1.2-0 libgksuui1.0-0 libgl1-mesa libgnomecupsui1.0-1
  libid3-3.8.3c2 libjack0.80.0-0 libkcal2a libkdepim1 libkleopatra0a libmimelib1a
  libmusicbrainz4c2 libnautilus-burn2 libnewt0.51 libnotify0 libopenexr2c2
  libopenh323-1.15.3c2 libpt-1.8.3c2 libtag1c2 libtunepimp2c2 libvte4 libxine1c2
  libxklavier10 makedepend mplayer-fonts mplayer-k6 mplayer-k7 mysql-common-4.1 netcdfg3
  openoffice.org-debian-files openoffice.org2 openoffice.org2-base openoffice.org2-calc
  openoffice.org2-common openoffice.org2-core openoffice.org2-draw
  openoffice.org2-evolution openoffice.org2-gnome openoffice.org2-impress
  openoffice.org2-kde openoffice.org2-l10n-en-us openoffice.org2-math
  openoffice.org2-writer python-kde3 python2.4-apt python2.4-cairo python2.4-crypto
  python2.4-dbus python2.4-gdbm python2.4-glade2 python2.4-gnome2 python2.4-gnome2-extras
  python2.4-gtk2 python2.4-kde3 python2.4-libxml2 python2.4-libxslt1 python2.4-numeric
  python2.4-pyorbit python2.4-tk python2.4-xml sanekonsole smeg ubuntu-base
  ubuntu-desktop ubuntu-minimal x-common xmkmf xorg-common xorg-driver-synaptics
  xserver-common xserver-xorg-driver-apm xserver-xorg-driver-ark xserver-xorg-driver-ati
  xserver-xorg-driver-chips xserver-xorg-driver-cirrus xserver-xorg-driver-cyrix
  xserver-xorg-driver-dummy xserver-xorg-driver-fbdev xserver-xorg-driver-glint
  xserver-xorg-driver-i128 xserver-xorg-driver-i740 xserver-xorg-driver-i810
  xserver-xorg-driver-imstt xserver-xorg-driver-mga xserver-xorg-driver-neomagic
  xserver-xorg-driver-newport xserver-xorg-driver-nsc xserver-xorg-driver-nv
  xserver-xorg-driver-rendition xserver-xorg-driver-s3 xserver-xorg-driver-s3virge
  xserver-xorg-driver-savage xserver-xorg-driver-siliconmotion xserver-xorg-driver-sis
  xserver-xorg-driver-tdfx xserver-xorg-driver-tga xserver-xorg-driver-trident
  xserver-xorg-driver-tseng xserver-xorg-driver-v4l xserver-xorg-driver-vesa
  xserver-xorg-driver-vga xserver-xorg-driver-via xserver-xorg-driver-vmware

```

AND

```
The following packages have been kept back:
  hpijs libggi2 python-adns python-clientcookie python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-eunuchs
  python-gadfly python-htmlgen python-htmltmpl python-imaging python-imaging-sane
  python-jabber python-kjbuckets python-ldap python-mysqldb python-opengl python-osd
  python-pam python-pexpect python-pgsql python-pylibacl python-pyopenssl python-pyxattr
  python-reportlab python-simpletal python-sqlite python-syck python-xmpp

```

The other packages are marked for an upgrade and I have quite a bit of new packages.

I just would like to ask what would be the best strategy to deal with this upgrade?

Many thanks for your help.

---

### Post by PriceChild on 2006-10-26
Do NOT skip versions.

You MUST go via 6.06 or you'll experience breakage and little support.

Check out [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) for more.

---

### Post by indigoshift on 2006-10-27
> **PriceChild said:**
> Check out [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) for more.

I don't mean to butt in, but I have a quick, related question:

I have a machine I upgraded from 5.10 to 6.04, and would like to keep it at 6.04 for the time being.

However, the desktop's panels still look like the 5.10 version.  What's worse is that certain things (most notably the clock) tend to float around instead of staying where they're supposed to be.

I looked over the page quoted above, and noticed this:

```
sudo apt-get install ubuntu-desktop 
```

Would that fix the problem?  I mean:  would it "see" that my panels are still stuck in 5.10 mode and say, "hey, these should be 6.04!  Let me fix that!"

Or would it just end up trying to put the 6.10 ubuntu-desktop on my 6.04 machine?

I may not have made any sense just now.  It's way past my bedtime.  :-|

---

