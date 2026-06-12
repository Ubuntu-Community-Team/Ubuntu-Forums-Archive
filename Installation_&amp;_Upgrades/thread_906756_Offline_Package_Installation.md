---
title: "Offline Package Installation?"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by theunixgeek on 2008-08-31
Would anyone like to do me a favor of going into Synaptic, checking off mysql-client-5.0, mysql-server-5.0, libgtk2.0-dev, and libgtk2.0-doc for installation (just checking the check box, not installing unless you want to) and then go to File>Generate Package Download Script, please? 

As in this picture: [http://2.bp.blogspot.com/_fs6jwQq0LQk/SLsbgxQZ7KI/AAAAAAAAAQw/FSqht56jDO8/s1600-h/Screenshot-Synaptic+Package+Manager+.png](http://2.bp.blogspot.com/_fs6jwQq0LQk/SLsbgxQZ7KI/AAAAAAAAAQw/FSqht56jDO8/s1600-h/Screenshot-Synaptic+Package+Manager+.png)

My Ubuntu PC currently can't access the internet - only my Mac. I plan on downloading the packages on my Mac (I have wget installed on it) and then transferring the files over on a pen drive. The script can just go on a pastebin, like rafb.net/paste

Thanks a bunch!
:)

---

### Post by lswb on 2008-08-31
Here you go:

```

#!/bin/sh
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-core/x11proto-core-dev_7.0.11-1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libice/libice-dev_1.0.4-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsm/libsm-dev_1.0.3-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxau/libxau-dev_1.0.3-2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpthread-stubs/libpthread-stubs0_0.1-2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpthread-stubs/libpthread-stubs0-dev_0.1-2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxdmcp/libxdmcp-dev_1.0.2-2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1-dev_1.1-1ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xlib0-dev_1.1-1ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-input/x11proto-input-dev_1.4.2-1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-kb/x11proto-kb-dev_1.0.3-2ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xtrans/xtrans-dev_1.0.4-1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-dev_1.1.3-1ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-xext/x11proto-xext-dev_7.0.2-5ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-fixes/x11proto-fixes-dev_4.0-2ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxfixes/libxfixes-dev_4.0.3-2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-composite/x11proto-composite-dev_0.4-2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcomposite/libxcomposite-dev_0.4.0-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-render/x11proto-render-dev_0.9.3-2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxrender/libxrender-dev_0.9.4-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcursor/libxcursor-dev_1.1.9-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-damage/x11proto-damage-dev_1.1.0-2build1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxdamage/libxdamage-dev_1.1.1-3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxext/libxext-dev_1.0.3-2build1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1-dev_2.0.1-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/z/zlib/zlib1g-dev_1.2.3.3.dfsg-7ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6-dev_2.3.5-1ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/libfontconfig1-dev_2.5.0-2ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xft/libxft-dev_2.1.12-2ubuntu5_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxi/libxi-dev_1.1.3-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-xinerama/x11proto-xinerama-dev_1.1.2-4ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxinerama/libxinerama-dev_1.0.2-1build1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-randr/x11proto-randr-dev_1.2.1-2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxrandr/libxrandr-dev_1.2.2-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libn/libnet-daemon-perl/libnet-daemon-perl_0.38-1.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libplrpc-perl/libplrpc-perl_0.2017-1.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbi-perl/libdbi-perl_1.601-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbd-mysql-perl/libdbd-mysql-perl_4.005-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-client-5.0_5.0.51a-3ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server-5.0_5.0.51a-3ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-dev_2.16.4-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/atk1.0/libatk1.0-dev_1.22.0-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pixman/libpixman-1-dev_0.10.0-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.15~beta5-3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cairo/libcairo2-dev_1.6.0-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-dev_1.20.5-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-dev_2.12.9-3ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-doc_2.12.9-3ubuntu4_all.deb

```

Just curious, why can't you do this on your own ubuntu box. Also, it is possible that I may have had some of the needed dependencies already installed in my system, and that they therefore would not be included in the download script.

---

### Post by manishtech on 2008-09-02
If you have net access on some other comp and has the same version of ubuntu installed, try this
[http://ubuntuforums.org/showpost.php?p=5710753&postcount=6](http://ubuntuforums.org/showpost.php?p=5710753&postcount=6)

---

### Post by ashtangiman on 2008-09-02
I am thinking of buying an Ubuntu Dell (Inspiron 530N) to use as a media server and PVR at home.  I do not have an internet account at home (or even a phone line).  So I wonder how easy it will be to download and install packages.  I have a G4 Powerbook that I can take to coffee shops, download stuff, and transfer on my home network to the Ubuntu box.  Will it be problematic to try to maintain various packages in this manner?

Thanks for your help, Paul.

---

