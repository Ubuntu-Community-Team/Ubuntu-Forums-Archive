---
title: "After upgrading to lucid, Qt apps don't seem to work"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by NilfiskAddictedCowboy on 2010-05-02
virtualbox, kid3-qt, keepassx all fail on undefined symbols
I tried reinstalling the apps first, then libqt4 core,gui, but to no avail.

VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: /usr/lib/libQtOpenGL.so.4: undefined symbol: _ZN14QPaintEngineEx15drawRoundedRectERK6QRectFddN2Qt8SizeModeE

kid3-qt: symbol lookup error: kid3-qt: undefined symbol: _ZN9QListData7detach3Ev

keepassx: symbol lookup error: keepassx: undefined symbol: _ZN9QListData7detach3Ev

---

### Post by NilfiskAddictedCowboy on 2010-05-02
problem fixed : problem caused by a non-ubuntu installer for beid.

removing
/usr/local/lib/beidqt/libQtGui.so.4 (0x00f97000)
/usr/local/lib/beidqt/libQtCore.so.4 
resolved my issue.



 ldd /usr/bin/keepassx
	linux-gate.so.1 =>  (0x00f96000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x004bf000)
	libXtst.so.6 => /usr/lib/libXtst.so.6 (0x002ed000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x0089b000)
	libQtXml.so.4 => /usr/lib/libQtXml.so.4 (0x00245000)
	libQtGui.so.4 => /usr/local/lib/beidqt/libQtGui.so.4 (0x00f97000)
	libQtCore.so.4 => /usr/local/lib/beidqt/libQtCore.so.4 (0x005dc000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00110000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00206000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00f46000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x002f3000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x0028a000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x0022c000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00230000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x002a4000)
	/lib/ld-linux.so.2 (0x00a69000)
	libaudio.so.2 => /usr/lib/libaudio.so.2 (0x00bdb000)
	libpng12.so.0 => /lib/libpng12.so.0 (0x00a25000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x0080f000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x008f4000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x002b2000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x002bb000)
	libz.so.1 => /lib/libz.so.1 (0x002d4000)
	libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x00e45000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x0044d000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00457000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x00998000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x00487000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00c12000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00a4f000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0x00933000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x008b4000)
	libuuid.so.1 => /lib/libuuid.so.1 (0x00e21000)
	libexpat.so.1 => /lib/libexpat.so.1 (0x00490000)

---

### Post by P4man on 2010-05-02
thanks for reporting back. Does beid work properly on lucid? Im about to upgrade a laptop to lucid which needs it, and our tax forms just came in, so Im a little hesitant.

---

### Post by NilfiskAddictedCowboy on 2010-05-02
After deleting the two libraries, the Belgian eID card application itself is still starting properly, so it looks OK, haven't tried taxonweb or anything though...

---

### Post by P4man on 2010-05-02
thanks. Ill take the jump then. Can always fill out taxonweb on a spare pc if need be. BTW, are you a Daan fan by any chance?

---

### Post by NilfiskAddictedCowboy on 2010-05-02
yes I am :-)

---

### Post by luc765 on 2010-06-05
Hello,

It is in french but easy to translate :

1) Install Beid on lucid without problem:
[http://users.skynet.be/linux-rixensart/app51_securite_applicative.html#eid](http://users.skynet.be/linux-rixensart/app51_securite_applicative.html#eid)

2) How to solve the qt problem regarding Virtualbox, Skype and Convertall and...

[http://users.skynet.be/linux-rixensart/1_suite.html#beid](http://users.skynet.be/linux-rixensart/1_suite.html#beid)

If you need more explanation you can mail me,

Lucien:p

---

### Post by valenstijn on 2010-06-18
thx for the usefull help

---

### Post by fedict_eid on 2010-06-21
Indeed, after installing the Belgium eID Middleware, other QT programs fail to launch.

The following commands solve this issue:

```
sudo sed -i 's/^\(\/usr\/local\/lib\/beidqt\)/#\1/' /etc/ld.so.conf
sudo rm /etc/ld.so.cache
sudo ldconfig
sudo apt-get install libqtgui4
```

---

### Post by luc765 on 2010-06-22
Manny thanks Fedict_eid 

Lucien

---

### Post by fedict_eid on 2010-06-22
FYI: on 22/06, a new version of eID MW for Ubuntu and Fedora is available that fixes the issue: 
[http://eid.belgium.be/nl/Hoe_installeer_je_de_eID/Linux/](http://eid.belgium.be/nl/Hoe_installeer_je_de_eID/Linux/)

---

### Post by Wim De Winter on 2010-12-17
> **fedict_eid said:**
> FYI: on 22/06, a new version of eID MW for Ubuntu and Fedora is available that fixes the issue: 
[http://eid.belgium.be/nl/Hoe_installeer_je_de_eID/Linux/](http://eid.belgium.be/nl/Hoe_installeer_je_de_eID/Linux/)

This indeed helps solving Qt problems. Thanks!

---

