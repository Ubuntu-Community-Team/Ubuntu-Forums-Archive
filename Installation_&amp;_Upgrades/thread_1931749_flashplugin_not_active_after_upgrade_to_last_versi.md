---
title: "flashplugin not active after upgrade to last version [11]"
date: 2012-02-26
forum: Installation &amp; Upgrades
---

### Post by manou on 2012-02-26
Hello,

Thanks for your time.

I upgrade the flashplugin to the last version and now I can't active it.

The plugin is installed but appears as *not active* in the plugins section.

Please, how could I active it and enjoy flash on the web-pages there are some .. ?

Thank you.

Here details:

.:: Screenshot ::.
[http://imagepaste.nullnetwork.net/viewimage.php?id=3363](http://imagepaste.nullnetwork.net/viewimage.php?id=3363)
[http://imagepaste.nullnetwork.net/viewimage.php?id=3364](http://imagepaste.nullnetwork.net/viewimage.php?id=3364)

---

.:: apt-show ::.

root@nomad2:~# clear;apt-cache show adobe-flashplugin

Package: adobe-flashplugin
Priority: optional
Section: web
Installed-Size: 16848
Maintainer: DL-Flash Player Ubuntu <FlashPlayerUbuntu@adobe.com>
Architecture: i386
Version: 11.1.102.62-0maverick1
Recommends: adobe-flash-properties-gtk (= 11.1.102.62-0maverick1) | adobe-flash-properties-kde (= 11.1.102.62-0maverick1)
Replaces: flashplugin (<< 6)
Suggests: firefox, konqueror-nsplugins, x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5), libnspr4-0d, libnss3-1d
Provides: flashplugin-nonfree
Depends: wget, fontconfig, libatk1.0-0 (>= 1.29.3), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgdk-pixbuf2.0-0 (>= 2.21.6), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.14.0), libpango1.0-0 (>= 1.14.0), libx11-6, libxext6, libxt6
Conflicts: flashplayer-mozilla, flashplugin (<< 6), flashplugin-downloader, flashplugin-installer, xfs (<< 1:1.0.1-5)
Filename: pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.62-0maverick1_i386.deb
Size: 6432564
MD5sum: a41290dfa9c39c49f918085dfff84ce6
SHA1: b10cb6159c23e3ae829a17f958c8caf1084211af
Description: Adobe Flash Player plugin version 11
 Adobe® Flash® Player is a cross-platform, browser-based application runtime
 that provides uncompromised viewing of expressive applications, content, and
 videos across browsers and operating systems.
Npp-File: libflashplayer.so
Npp-Mimetype: application/x-shockwave-flash
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: Adobe Flash Plugin ([http://www.adobe.com](http://www.adobe.com))
Npp-Name: Adobe Flash Plugin

---

### Post by Karlchen on 2012-02-26
Hello, Manou.

Have you tried clicking the [Activar] button on the Firefox plugin tab?
In case Firefox was loaded while Synaptic updated the flash plugin you may have to close and re-start Firefox in order to re-enable the flash plugin.

Kind regards,
Karl

---

### Post by winh8r on 2012-02-26
You might like to click on the link in my sig below entitled

"Help With Flash" which will take you to a link to install Flash Aid which will sort out issues with Flash in Firefox.

Hope this helps you.

---

### Post by bkleine on 2012-04-09
Hi,

this link has been most helpfull. Thanks a lot! I had used the official sources from Ubuntu, then those from Adobe for 11.2. r202 without any success. I had already installed flash-aid, took the file from your place and downgraded to flashplugin 11.1 and the flash elements from e.g. bundesliga.de and others are enabled again.

Merci vielmals, tak so myket, gracias

Bernhard

---

### Post by winh8r on 2012-04-09
Glad to hear you got it working again .

Good Luck.

---

