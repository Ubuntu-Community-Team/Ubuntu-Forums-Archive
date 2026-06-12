---
title: "Asterisk installation"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by longst on 2012-06-13
I am trying to upgrade Asterisk running on a ubuntu from version 1.6 to 1.8 or higher.

On this machine, the asterisk 1.6 was install via 
```
apt-get install asterisk
```
around 1.5 years ago.

I tried to uninstall asterisk with 
```
apt-get remove asterisk
```

after that I tried to use 
```
apt-get update
```

Then, when I try to use 
```
apt-get install asterisk
```

apt-get still installs an old asterisk 1.6 on my machine.

And I tried to use apt-cache show asterisk. 

```
Package: asterisk
Priority: optional
Section: universe/comm
Installed-Size: 9820
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian VoIP Team <pkg-voip-maintainers@lists.alioth.debian.org>
Architecture: i386
Version: 1:1.6.2.7-1ubuntu1
Provides: asterisk-1.6.2
Depends: libasound2 (>> 1.0.22), libc-client2007e, libc6 (>= 2.8), libcap2 (>= 2.10), libcurl3 (>= 7.16.2-1), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.12.0), libgmime-2.0-2a, libgsm1 (>= 1.0.13), libiksemel3, libldap-2.4-2 (>= 2.4.7), liblua5.1-0, libncurses5 (>= 5.7+20100313), libnewt0.52, libogg0 (>= 1.0rc3), libopenais3 (>= 1.1.2), libopenr2-3, libpopt0 (>= 1.16), libpq5 (>= 8.4~0cvs20090328), libpri1.4 (>= 1.4.10), libradiusclient-ng2, libsdl1.2debian (>= 1.2.10-1), libsnmp15 (>= 5.4.2.1~dfsg), libspandsp2, libspeex1 (>= 1.2~beta3-1), libspeexdsp1 (>= 1.2~beta3.2-1), libsqlite0 (>= 2.8.17), libss7-1 (>= 1.0), libssl0.9.8 (>= 0.9.8m-1), libstdc++6 (>= 4.1.1), libsybdb5 (>= 0.63), libtiff4, libtonezone2.0 (>= 1:2.2.1), libvorbis0a (>= 1.1.2), libvorbisenc2 (>= 1.1.2), libvpb0 (>= 4.2.22), libx11-6, libxml2 (>= 2.7.4), unixodbc (>= 2.2.11), zlib1g (>= 1:1.1.4), asterisk-config (= 1:1.6.2.7-1ubuntu1) | asterisk-config-custom, adduser, asterisk-prompt-en, dahdi
Recommends: sox
Suggests: asterisk-doc, asterisk-dev, asterisk-h323
Filename: pool/universe/a/asterisk/asterisk_1.6.2.7-1ubuntu1_i386.deb
Size: 3572716
MD5sum: 7f6652e9f0af40706bfd9ab1fd8cdd97
SHA1: 2ebc49b5b96f81287e94f7b76d0338b537906916
SHA256: 6fb45313aa83e4f1ab112a0c589b1b744f117cc33546dffb260544292282b1da
Description: Open Source Private Branch Exchange (PBX)
 Asterisk is an Open Source PBX and telephony toolkit.  It is, in a
 sense, middleware between Internet and telephony channels on the bottom,
 and Internet and telephony applications at the top.
 .
 Asterisk can be used with Voice over IP (SIP, H.323, IAX and more) standards,
 or the Public Switched Telephone Network (PSTN) through supported hardware.
 .
 Supported hardware:
 .
  * All Wildcard (tm) ISDN PRI cards from Digium (http://www.digium.com)
  * HFC-S/HFC-4S-based ISDN BRI cards (Junghanns.NET, beroNet, Digium etc.)
  * All TDM (FXO/FXS) cards from Digium
  * Various clones of Digium cards such as those by OpenVox
  * Xorcom Astribank USB telephony adapter (http://www.xorcom.com)
  * Voicetronix OpenPCI, OpenLine and OpenSwitch cards
  * CAPI-compatible ISDN cards (using the add-on package chan-capi)
  * Full Duplex Sound Card (ALSA or OSS) supported by Linux
  * Tormenta T1/E1 card (http://www.zapatatelephony.org)
  * QuickNet Internet PhoneJack and LineJack (http://www.quicknet.net)
 .
 This is the main package that includes the Asterisk daemon and most channel
 drivers and applications.
Homepage: http://www.asterisk.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

Package: asterisk
Priority: optional
Section: universe/comm
Installed-Size: 9720
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian VoIP Team <pkg-voip-maintainers@lists.alioth.debian.org>
Architecture: i386
Version: 1:1.6.2.7-1ubuntu1.2
Provides: asterisk-1.6.2
Depends: libasound2 (>> 1.0.22), libc-client2007e, libc6 (>= 2.8), libcap2 (>= 2.10), libcurl3 (>= 7.16.2-1), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.12.0), libgmime-2.0-2a, libgsm1 (>= 1.0.13), libiksemel3, libldap-2.4-2 (>= 2.4.7), liblua5.1-0, libncurses5 (>= 5.7+20100313), libnewt0.52, libogg0 (>= 1.0rc3), libopenais3 (>= 1.1.2), libopenr2-3, libpopt0 (>= 1.16), libpq5 (>= 8.4~0cvs20090328), libpri1.4 (>= 1.4.10), libradiusclient-ng2, libsdl1.2debian (>= 1.2.10-1), libsnmp15 (>= 5.4.3~dfsg), libspandsp2, libspeex1 (>= 1.2~beta3-1), libspeexdsp1 (>= 1.2~beta3.2-1), libsqlite0 (>= 2.8.17), libss7-1 (>= 1.0), libssl0.9.8 (>= 0.9.8m-1), libstdc++6 (>= 4.1.1), libsybdb5 (>= 0.63), libtiff4, libtonezone2.0 (>= 1:2.2.1), libvorbis0a (>= 1.1.2), libvorbisenc2 (>= 1.1.2), libvpb0 (>= 4.2.22), libx11-6, libxml2 (>= 2.7.4), unixodbc (>= 2.2.11), zlib1g (>= 1:1.1.4), asterisk-config (= 1:1.6.2.7-1ubuntu1.2) | asterisk-config-custom, adduser, asterisk-prompt-en, dahdi
Recommends: sox
Suggests: asterisk-doc, asterisk-dev, asterisk-h323
Filename: pool/universe/a/asterisk/asterisk_1.6.2.7-1ubuntu1.2_i386.deb
Size: 3535260
MD5sum: 68fe845d5f4ffce05cf8109dcec75480
SHA1: de97d64824b2b4e12094a916eb6b44d72b97e287
SHA256: 099e14a4d1ffce7f13eb15daaece9d209f0bc4cedc0292981e033540a3a534a9
Description: Open Source Private Branch Exchange (PBX)
 Asterisk is an Open Source PBX and telephony toolkit.  It is, in a
 sense, middleware between Internet and telephony channels on the bottom,
 and Internet and telephony applications at the top.
 .
 Asterisk can be used with Voice over IP (SIP, H.323, IAX and more) standards,
 or the Public Switched Telephone Network (PSTN) through supported hardware.
 .
 Supported hardware:
 .
  * All Wildcard (tm) ISDN PRI cards from Digium (http://www.digium.com)
  * HFC-S/HFC-4S-based ISDN BRI cards (Junghanns.NET, beroNet, Digium etc.)
  * All TDM (FXO/FXS) cards from Digium
  * Various clones of Digium cards such as those by OpenVox
  * Xorcom Astribank USB telephony adapter (http://www.xorcom.com)
  * Voicetronix OpenPCI, OpenLine and OpenSwitch cards
  * CAPI-compatible ISDN cards (using the add-on package chan-capi)
  * Full Duplex Sound Card (ALSA or OSS) supported by Linux
  * Tormenta T1/E1 card (http://www.zapatatelephony.org)
  * QuickNet Internet PhoneJack and LineJack (http://www.quicknet.net)
 .
 This is the main package that includes the Asterisk daemon and most channel
 drivers and applications.
Homepage: http://www.asterisk.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

I am wondering in this case how I am would be able to install a newer version of Asterisk.

Thanks

---

