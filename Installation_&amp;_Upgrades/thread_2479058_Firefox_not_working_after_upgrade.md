---
title: "Firefox not working after upgrade"
date: 2022-09-13
forum: Installation &amp; Upgrades
---

### Post by portalan on 2022-09-13
I have just upgraded from 20.04 to 22.04, most things are working but not Firefox. The little wheels go round and nothing happens. Attempting to open a second window makes the pop-up panel jitter about. I tried reloading Firefox, then getting the deb version, with no effect. Any ideas?

---

### Post by &amp;KyT$0P# on 2022-09-13
Does this also happen in a new, clean [Firefox profile]("https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles") with all default settings and no extensions added?

---

### Post by portalan on 2022-09-13
As far as I know it re-installed with default settings. Your link describes how to use Profile Manager in Windows, I couldn't see a reference to Linux. This is the reply when I install Firefox:
```
graham@alan-inspiron-545:~$ sudo apt install firefox
[sudo] password for graham: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
firefox is already the newest version (1:1snap1-0ubuntu2).
The following packages were automatically installed and are no longer required:
  binutils-common bsdmainutils command-not-found-data cpp-9 enchant fakeroot
  gcc-10-base gcc-9-base geoip-database gettext gir1.2-accounts-1.0
  gir1.2-appindicator3-0.1 gir1.2-clutter-1.0 gir1.2-clutter-gst-3.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gnomebluetooth-1.0
  gir1.2-gtkclutter-1.0 gir1.2-signon-1.0 gnome-getting-started-docs
  gnome-software-common hddtemp intltool-debian ippusbxd iputils-arping
  libalgorithm-diff-perl libalgorithm-merge-perl libamtk-5-0 libamtk-5-common
  libaom0 libarchive-zip-perl libargon2-0 libart-2.0-2 libasan5
  libasn1-8-heimdal libasync-mergepoint-perl libatomic1 libavutil55
  libb-hooks-op-check-perl libbinutils libboost-date-time1.65.1
  libboost-date-time1.71.0 libboost-filesystem1.65.1 libboost-filesystem1.71.0
  libboost-iostreams1.65.1 libboost-iostreams1.71.0 libboost-locale1.71.0
  libboost-system1.65.1 libboost-thread1.65.1 libboost-thread1.71.0
  libbrlapi0.6 libbrlapi0.7 libc-dev-bin libcamel-1.2-62 libcapture-tiny-perl
  libcbor0.6 libcc1-0 libcdio17 libcdio18 libcgi-pm-perl
  libclass-method-modifiers-perl libclass-xsaccessor-perl libcmis-0.5-5v5
  libcodec2-0.9 libcpanel-json-xs-perl libcroco3 libcrypt-dev libctf0
  libdevel-size-perl libdns-export1100 libdns-export1109 libdns1100 libdvdnav4
  libdvdread4 libdvdread7 libedataserver-1.2-24 libedataserverui-1.2-2
  libegl1-mesa libenchant1c2a libexempi3 libexporter-tiny-perl
  libextutils-pkgconfig-perl libfakeroot libfcgi-perl libfcgi0ldbl
  libfile-copy-recursive-perl libfile-find-rule-perl libfuse2 libfuture-perl
  libfwupdplugin1 libgdbm5 libgdk-pixbuf-xlib-2.0-0 libgdk-pixbuf2.0-0
  libgeoclue0 libgeoip1 libgl1-mesa-glx libgmime-3.0-0 libgssapi3-heimdal
  libgtksourceview-3.0-common libgupnp-1.2-0 libgutenprint-common
  libgutenprint2 libgutenprint9 libgweather-3-15 libhandy-0.0-0
  libhcrypto4-heimdal libheimbase1-heimdal libheimntlm0-heimdal libhogweed5
  libhunspell-1.6-0 libhx509-5-heimdal libicu66 libigdgmm11 libilmbase12
  libilmbase24 libio-pty-perl libip6tc0 libipc-run-perl libiptc0
  libisc-export169 libisc169 libisccc160 libisccfg160 libisl19 libisl22
  libitm1 libjson-c3 libjson-c4 libjson-maybexs-perl libjuh-java libjurt-java
  libkrb5-26-heimdal libldap-2.4-2 liblibreoffice-java liblinux-epoll-perl
  liblist-compare-perl libllvm12 liblouis14 liblsan0 libmagickcore-6.q16-3
  libmagickcore-6.q16-3-extra libmagickwand-6.q16-3 libminiupnpc10 libmng2
  libmozjs-52-0 libmozjs-68-0 libmysofa0 libmysqlclient21 libnet-dns-perl
  libnet-dns-sec-perl libnet-domain-tld-perl libnet-ip-perl libnettle7
  libnm-util2 libnss-myhostname libntfs-3g88 libntfs-3g883
  libnumber-compare-perl libopenexr22 libopenexr24 liborcus-0.15-0
  libpackage-stash-xs-perl libpath-tiny-perl libperl4-corelibs-perl
  libperlio-gzip-perl libpgm-5.2-0 libphonenumber7 libpoppler73 libpoppler97
  libpostproc54 libprocps6 libprotobuf10 libprotobuf17 libpython2.7
  libpython2.7-minimal libpython2.7-stdlib libpython3.6-minimal libpython3.8
  libpython3.8-minimal libpython3.8-stdlib libqpdf21 libqpdf26 libraw16
  libraw19 libref-util-perl libref-util-xs-perl
  libreoffice-avmedia-backend-gstreamer libreoffice-style-tango libridl-java
  libroken18-heimdal libsane libsereal-decoder-perl libsereal-encoder-perl
  libsereal-perl libsignon-glib1 libstrictures-perl
  libsub-exporter-progressive-perl libsub-identify-perl libsub-quote-perl
  libswresample2 libswscale4 libtepl-4-0 libtest-fatal-perl
  libtest-refcount-perl libtext-glob-perl libtext-levenshtein-perl
  libtracker-control-2.0-0 libtracker-miner-2.0-0 libtracker-sparql-2.0-0
  libtsan0 libtype-tiny-perl libtype-tiny-xs-perl libunicode-utf8-perl
  libunoloader-java liburl-dispatcher1 libvariable-magic-perl libvpx5 libvpx6
  libwebp6 libwind0-heimdal libwmf0.2-7 libx264-152 libx264-155 libx265-146
  libx265-179 libxml-sax-base-perl libxml-writer-perl libxmlb1
  libyaml-libyaml-perl libzeitgeist-1.0-1 ltrace lz4 manpages-dev mysql-common
  ncal nplan patchutils pkg-config popularity-contest
  printer-driver-gutenprint python-talloc python3-asn1crypto
  python3-entrypoints python3-feedparser python3-html5lib python3-lxml
  python3-oauth python3-requests-unixsocket python3-sgmllib3k
  python3-simplejson python3-webencodings python3-zope.interface
  python3.6-minimal python3.8 python3.8-minimal qtchooser qtcore4-l10n ruby2.7
  syslinux-common syslinux-legacy unity-lens-applications unity-lens-files
  unity-lens-music unity-lens-video unity-scope-calculator unity-scope-devhelp
  unity-scope-manpages unity-scope-tomboy unity-scope-video-remote
  unity-scope-virtualbox unity-scopes-runner ure-java
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 15 not to upgrade.
```

I did an autoremove for this and other items, with no improvement. There is a folder of "Old Firefox Data", should I try to delete this?

---

### Post by &amp;KyT$0P# on 2022-09-13
> **portalan said:**
> Your link describes how to use Profile Manager in Windows, I couldn't see a reference to Linux.

You should be able to select Linux in the sidebar on the right of that page.

> This is the reply when I install Firefox:
graham@alan-inspiron-545:~$ sudo apt install firefox
[sudo] password for graham: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
firefox is already the newest version (1:1snap1-0ubuntu2).

You did not get the .deb version of Firefox.  What instructions for installing .deb Firefox did you follow?  Can you try again following the instructions [here]("https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/")?

> There is a folder of "Old Firefox Data", should I try to delete this?

Not yet.  If you are seeing that, then Firefox did indeed try to reset itself to default settings as you said, and that "Old Firefox Data" is where your actual Firefox data is.  You'll need that folder if you will want to [restore your important Firefox data]("https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile") once you get the main issue resolved.

---

### Post by portalan on 2022-09-15
I tried again to get .deb but got the snap version again. There are issues with the display. Type gedit in the terminal and it opens OK, but sudo gedit doesn't, the response is "gedit position not supported". So I had to load the preferences statement in a different way.
Type firefox in the terminal and the response starts with: failed to load module "canberra-gtk-module". I don't know what that is or if its critical.

---

### Post by &amp;KyT$0P# on 2022-09-15
> **portalan said:**
> I tried again to get .deb but got the snap version again. 

Again, what instructions for installing .deb Firefox are you following?

You could also try the [official Mozilla build tar.bz2]("https://www.mozilla.org/firefox/all/#product-desktop-release")

---

### Post by col48 on 2022-09-15
> There is a folder of "Old Firefox Data", should I try to delete this?
Not yet. If you are seeing that, then Firefox did indeed try to reset itself to default settings as you said, and that "Old Firefox Data" is where your actual Firefox data is. You'll need that folder if you will want to restore your important Firefox data once you get the main issue resolved. Definitely take notice of this.  In fact, I'd be inclined to copy the old Firefox data to preserve it somewhere amongst your own data to guard against the faint(?) possibility that any reset/reinstall of Firefox will delete it as obsolete.  Once you have Firefox up and running, a simple profile to profile copy from the old data will restore all your emails and email folder structure.

---

### Post by portalan on 2022-09-15
Again, what instructions for installing .deb Firefox are you following? I followed your link as far as possible, sudo gedit didn't work (see above), similar instructions are at :

[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

These have an extra bit about automatic updates.

I will try your alternative if I can get the display/graphics to work properly.

---

### Post by &amp;KyT$0P# on 2022-09-15
> **portalan said:**
> similar instructions are at :

[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

These have an extra bit about automatic updates.

That should work if you do [FONT=Courier New]sudo apt-get purge firefox[/FONT] at some point (maybe before starting their steps?).

---

### Post by mIk3_08 on 2022-09-15
> **portalan said:**
> I have just upgraded from 20.04 to 22.04, most things are working but not Firefox. The little wheels go round and nothing happens. Attempting to open a second window makes the pop-up panel jitter about. I tried reloading Firefox, then getting the deb version, with no effect. Any ideas?
Have you tried their .tar.bz2? You can still use Firefox browser with their .tar.bz2. To download their .tar.bz2 here is the [link]("https://www.mozilla.org/en-US/"). Regards and cheers

---

### Post by SeijiSensei on 2022-09-16
Didn't work for me using the current 22.04 version.

See: [https://ubuntuforums.org/showthread.php?t=2479001](https://ubuntuforums.org/showthread.php?t=2479001)

Every time I try to update after following the procedure at ombubuntu, I always get the snap package.

I switched to Google Chrome, but it has long hands visiting sites that have lots of scripts and stuff. Now I'm back to chromium-browser again. It's also a snap, but I was able to load my password file into it, unlike my experience with the Firefox snap.

---

### Post by SeijiSensei on 2022-09-16
> **halogen2 said:**
> That should work if you do [FONT=Courier New]sudo apt-get purge firefox[/FONT] at some point (maybe before starting their steps?).

Didn't work for me using the current 22.04 version.

See: [https://ubuntuforums.org/showthread.php?t=2479001](https://ubuntuforums.org/showthread.php?t=2479001)

Every time I try to update after following the procedure at omgubuntu, I always get the snap package. That method worked in earlier 22.04 versions, but not the most recent, at least not for me.

I switched to Google Chrome, but it has long hangs visiting sites that have lots of scripts and stuff. Now I'm back to chromium-browser again. It's also a snap, but I was able to load my password file into it, unlike my experience with the Firefox snap. (All my browsers use the Ghostery and UBlock Origin extensions.)

---

### Post by &amp;KyT$0P# on 2022-09-16
> **SeijiSensei said:**
> Didn't work for me using the current 22.04 version.

See: [https://ubuntuforums.org/showthread.php?t=2479001](https://ubuntuforums.org/showthread.php?t=2479001)

Every time I try to update after following the procedure at omgubuntu, I always get the snap package. That method worked in earlier 22.04 versions, but not the most recent, at least not for me.

It works for me on an up-to-date Xubuntu 22.04 system without snapd and with no Firefox packages installed: following those instructions resulted in successfully getting the .deb Firefox, and updating the apt packages did not try to install the snap Firefox.  Did you see my post #3 in that other thread?

---

### Post by portalan on 2022-09-16
I tried disabling Wayland as described here from another thread:
Re: Browser problems in 22/04

    In one computer I switched from the default Wayland to X in order to make Firefox work. I think it was in a computer with nvidia graphics.

    Edit a configuration file,

    Code:

    sudo nano /etc/gdm3/custom.conf

    to uncomment (remove '#') the line containing
    Code:

    WaylandEnable=false

    and reboot.

To my surprise Firefox now works. Maybe I need a new graphics card if Wayland is a better option. I guess this counts as SOLVED.

---

### Post by portalan on 2022-09-16
I tried disabling Wayland as described here from another thread:
Re: Browser problems in 22/04

    In one computer I switched from the default Wayland to X in order to  make Firefox work. I think it was in a computer with nvidia graphics.

    Edit a configuration file,

    Code:

    sudo nano /etc/gdm3/custom.conf

    to uncomment (remove '#') the line containing
    Code:

    WaylandEnable=false

    and reboot.

To my surprise Firefox now works. Maybe I need a new graphics card if Wayland is a better option.  I guess this counts as SOLVED.

---

