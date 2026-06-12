---
title: "i can't upgrade dapper to eddy"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by jfca283 on 2007-06-29
this are my messages
**main.log**
```
2007-06-29 17:02:08,803 DEBUG Foreign: 
2007-06-29 17:02:08,804 DEBUG Obsolete: libdivxencore0 gaim-data vim-common murrine libglitz-glx1 stardict-tools beryl-plugins vlc-nox beryl-settings x11proto-gl-dev amule libglitz-glx1-dev beryl-settings-bindings libxfixes3 vlc libxcomposite1 xserver-xorg-input-synaptics glchess libares-gift emerald tcl8.5 libdvdcss2-dev glaurung mesa-common-dev python-wxversion x11proto-composite-dev beryl-settings-simple python-wxgtk2.6 mozilla-mplayer libxfixes-dev pptview libglu1-mesa pidgin-2.0.0beta7 faile libgl1-mesa libdvdcss2 metamorphose libberylsettings0 gaim-guifications libfasttrack-gift libxmms2client-glib xserver-xorg-driver-i810 w32codecs mesa-utils x11proto-fixes-dev stardict poppler-utils vim libwxgtk2.6-0 gxmame tcltls libxcomposite-dev amsn libberyldecoration0 glipper libcairo2 xserver-xorg-driver-ati libwnck-common libgl1-mesa-dri libxmms2client emerald-themes libgl1-mesa-dev libwnck18 python2.4-sip4-qt3 qjoypad libpoppler1-glib libwxbase2.6-0 mplayerplug-in xserver-xgl dvd95-1.1p1 grub-gfxboot kiba-dock libxss1 libglitz1 vlc-plugin-alsa tk8.5 libdivxdecore0 libglitz1-dev beryl-plugins-data pcmanfm libcairo2-dev beryl libvlc0 lastfm beryl-core beryl-manager mplayer vim-runtime libemeraldengine0 libpoppler1 gnome-session
2007-06-29 17:02:08,837 DEBUG updateSourcesList()
2007-06-29 17:02:09,202 DEBUG rewriteSourcesList()
2007-06-29 17:02:11,187 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted'
2007-06-29 17:02:11,188 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted' updated to new dist
2007-06-29 17:02:11,189 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted'
2007-06-29 17:02:11,200 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted' updated to new dist
2007-06-29 17:02:11,201 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted'
2007-06-29 17:02:11,201 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted' updated to new dist
2007-06-29 17:02:11,202 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted'
2007-06-29 17:02:11,203 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted' updated to new dist
2007-06-29 17:02:11,204 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu dapper-security main restricted'
2007-06-29 17:02:11,204 DEBUG entry 'deb http://security.ubuntu.com/ubuntu edgy-security main restricted' updated to new dist
2007-06-29 17:02:11,205 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted'
2007-06-29 17:02:11,207 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted' updated to new dist
2007-06-29 17:02:11,208 DEBUG examining: 'deb http://archive.canonical.com/ubuntu dapper-commercial main'
2007-06-29 17:02:11,214 DEBUG entry '# deb http://archive.canonical.com/ubuntu dapper-commercial main' was disabled (unknown mirror)
2007-06-29 17:02:11,214 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse'
2007-06-29 17:02:11,215 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse' updated to new dist
2007-06-29 17:02:11,219 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse'
2007-06-29 17:02:11,220 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse' updated to new dist
2007-06-29 17:02:11,221 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse'
2007-06-29 17:02:11,221 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse' updated to new dist
2007-06-29 17:02:11,223 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse'
2007-06-29 17:02:11,224 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse' updated to new dist
2007-06-29 17:04:19,544 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2007-06-29 17:04:19,562 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2007-06-29 17:04:19,570 DEBUG running edgyQuirks handler
2007-06-29 17:04:19,595 DEBUG Installing 'python-tk' (python2.4->python upgrade rule)
2007-06-29 17:04:19,924 DEBUG Installing 'python-pycurl' (python2.4->python upgrade rule)
2007-06-29 17:04:19,933 DEBUG Installing 'python-qt3' (python2.4->python upgrade rule)
2007-06-29 17:04:19,937 DEBUG Installing 'python-sqlite' (python2.4->python upgrade rule)
2007-06-29 17:04:19,960 DEBUG Installing 'python-egenix-mxtexttools' (python2.4->python upgrade rule)
2007-06-29 17:04:19,971 DEBUG Installing 'python-ldap' (python2.4->python upgrade rule)
2007-06-29 17:04:19,990 DEBUG Installing 'python-pysqlite2' (python2.4->python upgrade rule)
2007-06-29 17:04:19,992 DEBUG Installing 'xserver-xorg-input-synaptics' (xserver-xorg-input fixup rule)
2007-06-29 17:04:20,003 DEBUG Installing 'python-elementtree' (python2.4->python upgrade rule)
2007-06-29 17:04:20,019 DEBUG Installing 'python-clientcookie' (python2.4->python upgrade rule)
2007-06-29 17:04:20,038 DEBUG Installing 'python-soappy' (python2.4->python upgrade rule)
2007-06-29 17:04:20,039 DEBUG Installing 'python-xmpp' (python2.4->python upgrade rule)
2007-06-29 17:04:20,041 DEBUG Installing 'python-gadfly' (python2.4->python upgrade rule)
2007-06-29 17:04:20,054 DEBUG Installing 'python-reportlab' (python2.4->python upgrade rule)
2007-06-29 17:04:20,058 DEBUG Installing 'python-jabber' (python2.4->python upgrade rule)
2007-06-29 17:04:20,061 DEBUG Installing 'python-pylibacl' (python2.4->python upgrade rule)
2007-06-29 17:04:20,063 DEBUG Installing 'python-syck' (python2.4->python upgrade rule)
2007-06-29 17:04:20,074 DEBUG Installing 'python-ctypes' (python2.4->python upgrade rule)
2007-06-29 17:04:20,083 DEBUG Installing 'python-gtk2' (python2.4->python upgrade rule)
2007-06-29 17:04:20,088 DEBUG Installing 'python-unit' (python2.4->python upgrade rule)
2007-06-29 17:04:20,089 DEBUG Installing 'python-geoip' (python2.4->python upgrade rule)
2007-06-29 17:04:20,097 DEBUG Installing 'python-kjbuckets' (python2.4->python upgrade rule)
2007-06-29 17:04:20,101 DEBUG Installing 'python-id3lib' (python2.4->python upgrade rule)
2007-06-29 17:04:20,122 DEBUG Installing 'python-eunuchs' (python2.4->python upgrade rule)
2007-06-29 17:04:20,152 DEBUG Installing 'python-libxml2' (python2.4->python upgrade rule)
2007-06-29 17:04:20,160 DEBUG Installing 'python-glade2' (python2.4->python upgrade rule)
2007-06-29 17:04:20,164 DEBUG Installing 'python-pyxattr' (python2.4->python upgrade rule)
2007-06-29 17:04:20,171 DEBUG Installing 'python-imaging-sane' (python2.4->python upgrade rule)
2007-06-29 17:04:20,176 DEBUG Installing 'python-pyorbit' (python2.4->python upgrade rule)
2007-06-29 17:04:20,183 DEBUG Installing 'python-gdbm' (python2.4->python upgrade rule)
2007-06-29 17:04:20,196 DEBUG Installing 'python-pgsql' (python2.4->python upgrade rule)
2007-06-29 17:04:20,209 DEBUG Installing 'python-apt' (python2.4->python upgrade rule)
2007-06-29 17:04:20,210 DEBUG Installing 'python-pyopenssl' (python2.4->python upgrade rule)
2007-06-29 17:04:20,215 DEBUG Installing 'python-numeric' (python2.4->python upgrade rule)
2007-06-29 17:04:20,230 DEBUG Installing 'python-htmlgen' (python2.4->python upgrade rule)
2007-06-29 17:04:20,231 DEBUG Installing 'python-egenix-mxtools' (python2.4->python upgrade rule)
2007-06-29 17:04:20,234 DEBUG Installing 'python-simpletal' (python2.4->python upgrade rule)
2007-06-29 17:04:20,255 DEBUG Installing 'python-pymad' (python2.4->python upgrade rule)
2007-06-29 17:04:20,271 DEBUG Installing 'python-pexpect' (python2.4->python upgrade rule)
2007-06-29 17:04:20,274 DEBUG Installing 'python-libxslt1' (python2.4->python upgrade rule)
2007-06-29 17:04:20,279 DEBUG Installing 'python-egenix-mxproxy' (python2.4->python upgrade rule)
2007-06-29 17:04:20,281 DEBUG Installing 'python-htmltmpl' (python2.4->python upgrade rule)
2007-06-29 17:04:20,296 DEBUG Installing 'python-egenix-mxstack' (python2.4->python upgrade rule)
2007-06-29 17:04:20,297 DEBUG Installing 'python-pam' (python2.4->python upgrade rule)
2007-06-29 17:04:20,301 DEBUG Installing 'python-mysqldb' (python2.4->python upgrade rule)
2007-06-29 17:04:20,304 DEBUG Installing 'python-gd' (python2.4->python upgrade rule)
2007-06-29 17:04:20,320 DEBUG Installing 'python-imaging' (python2.4->python upgrade rule)
2007-06-29 17:04:20,331 DEBUG Installing 'python-xml' (python2.4->python upgrade rule)
2007-06-29 17:04:20,334 DEBUG Installing 'python-gnome2-extras' (python2.4->python upgrade rule)
2007-06-29 17:04:20,338 DEBUG Installing 'python-epydoc' (python2.4->python upgrade rule)
2007-06-29 17:04:20,343 DEBUG Installing 'python-adns' (python2.4->python upgrade rule)
2007-06-29 17:04:20,357 DEBUG Installing 'python-gnome2-desktop' (python2.4->python upgrade rule)
2007-06-29 17:04:20,358 DEBUG Installing 'python-gnome2' (python2.4->python upgrade rule)
2007-06-29 17:04:20,363 DEBUG Installing 'python-crypto' (python2.4->python upgrade rule)
2007-06-29 17:04:20,389 DEBUG Installing 'hpijs' (hpijs quirk upgrade rule)
2007-06-29 17:04:20,672 INFO Forcing downgrade of libgl1-mesa-dri for xgl.compz.info installs
2007-06-29 17:04:20,984 DEBUG no {ubuntu,edubuntu,kubuntu}-desktop pkg installed
2007-06-29 17:04:20,994 DEBUG guessing 'ubuntu-desktop' as missing meta-pkg
2007-06-29 17:04:21,356 ERROR failed to mark 'ubuntu-desktop' for install (E:Unable to correct problems, you have held broken packages.)
2007-06-29 17:04:47,913 ERROR Dist-upgrade failed: 'Can't upgrade required meta-packages'
```

so, what is wrong?
another issue, is that reading some experiencies of users, they say that the upgrade it isn't very acurate with the depencies, and the sistem isn't very stable
what happen if i download Feisty, i mount it some folder of ubuntu dapper
i can get an installation from there?
is it possible? i think not, but, who knows?
well, that's all
thanks

---

### Post by BlahMan_of.Doom on 2007-06-29
Burn a feisty CD, pop it in, then restart your computer. See if it installs not form Ubuntu.

---

