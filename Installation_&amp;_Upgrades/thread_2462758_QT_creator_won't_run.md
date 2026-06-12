---
title: "QT creator won't run"
date: 2021-05-27
forum: Installation &amp; Upgrades
---

### Post by anneranch on 2021-05-27
In  "show applications" I have an icon  for Qt Creator .
[B]Opening new window should start / run it .
It does not .[/B]
So I decided  to o install qtcreator . 

This is what I get in terminal. 

And it ends with this cryptic  error 

Media change: please insert the disc labeled 
 'Ubuntu 21.04 _Hirsute Hippo_ - Release amd64 (20210420)' 
in the drive '/cdrom/' and press [Enter] 


**I do not have crrom , so what are my options to resolve this ? **

```

qr@qr-desktop:~$ sudo apt install qtcreator 
[sudo] password for qr:  
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
The following additional packages will be installed: 
  binfmt-support binutils binutils-common binutils-x86-64-linux-gnu clang-11 
  clang-12 clang-tidy clang-tidy-12 clang-tools-12 lib32gcc-s1 lib32stdc++6 
  libasan6 libatomic1 libbinutils libc-dev-bin libc-devtools libc6-dev 
  libc6-i386 libclang-common-11-dev libclang-common-12-dev libclang-cpp11 
  libclang-cpp12 libclang1-11 libclang1-12 libcrypt-dev libctf-nobfd0 libctf0 
  libdouble-conversion3 libffi-dev libgc1 libgcc-10-dev libitm1 
  libkf5syntaxhighlighting-data libkf5syntaxhighlighting5 libllvm12 liblsan0 
  libmd4c0 libncurses-dev libnsl-dev libobjc-10-dev libobjc4 libomp-12-dev 
  libomp5-12 libpcre2-16-0 libpfm4 libqt5concurrent5 libqt5core5a libqt5dbus5 
  libqt5designer5 libqt5designercomponents5 libqt5gui5 libqt5help5 
  libqt5network5 libqt5positioning5 libqt5printsupport5 libqt5qml5 
  libqt5qmlmodels5 libqt5qmlworkerscript5 libqt5quick5 libqt5quicktest5 
  libqt5quickwidgets5 libqt5sensors5 libqt5serialport5 libqt5sql5 
  libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5webchannel5 libqt5webkit5 
  libqt5widgets5 libqt5xml5 libqt5xmlpatterns5 libquadmath0 libstdc++-10-dev 
  libtinfo-dev libtirpc-dev libtsan0 libubsan1 libxcb-xinerama0 libxcb-xinput0 
  libyaml-cpp0.6 libz3-4 libz3-dev linux-libc-dev llvm-11 llvm-11-dev 
  llvm-11-linker-tools llvm-11-runtime llvm-11-tools llvm-12 llvm-12-dev 
  llvm-12-linker-tools llvm-12-runtime llvm-12-tools make manpages-dev 
  python3-pygments qdoc-qt5 qhelpgenerator-qt5 qml-module-qtgraphicaleffects 
  qml-module-qtqml qml-module-qtqml-models2 qml-module-qtquick-controls 
  qml-module-qtquick-layouts qml-module-qtquick-window2 qml-module-qtquick2 
  qmlscene qt3d5-doc qt5-assistant qt5-doc qt5-gtk-platformtheme 
  qt5-qmltooling-plugins qtattributionsscanner-qt5 qtbase5-dev-tools 
  qtbase5-doc qtcharts5-doc qtchooser qtconnectivity5-doc qtcreator-data 
  qtcreator-doc qtdatavisualization5-doc qtdeclarative5-dev-tools 
  qtdeclarative5-doc qtgraphicaleffects5-doc qtlocation5-doc qtmultimedia5-doc 
  qtnetworkauth5-doc qtquickcontrols2-5-doc qtquickcontrols5-doc qtscript5-doc 
  qtscxml5-doc qtsensors5-doc qtserialbus5-doc qtserialport5-doc qtsvg5-doc 
  qttools5-dev-tools qttools5-doc qttranslations5-l10n qtvirtualkeyboard5-doc 
  qtwayland5-doc qtwebchannel5-doc qtwebengine5-doc qtwebsockets5-doc 
  qtwebview5-doc qtx11extras5-doc qtxmlpatterns5-dev-tools qtxmlpatterns5-doc 
  rpcsvc-proto 
Suggested packages: 
  binutils-doc clang-11-doc clang-12-doc glibc-doc ncurses-doc libomp-12-doc 
  qt5-image-formats-plugins qtwayland5 libstdc++-10-doc llvm-11-doc 
  llvm-12-doc make-doc python-pygments-doc ttf-bitstream-vera qtbase5-dev 
  clazy cmake g++ git meson subversion valgrind 
Recommended packages: 
  libomp-11-dev 
The following NEW packages will be installed: 
  binfmt-support binutils binutils-common binutils-x86-64-linux-gnu clang-11 
  clang-12 clang-tidy clang-tidy-12 clang-tools-12 lib32gcc-s1 lib32stdc++6 
  libasan6 libatomic1 libbinutils libc-dev-bin libc-devtools libc6-dev 
  libc6-i386 libclang-common-11-dev libclang-common-12-dev libclang-cpp11 
  libclang-cpp12 libclang1-11 libclang1-12 libcrypt-dev libctf-nobfd0 libctf0 
  libdouble-conversion3 libffi-dev libgc1 libgcc-10-dev libitm1 
  libkf5syntaxhighlighting-data libkf5syntaxhighlighting5 libllvm12 liblsan0 
  libmd4c0 libncurses-dev libnsl-dev libobjc-10-dev libobjc4 libomp-12-dev 
  libomp5-12 libpcre2-16-0 libpfm4 libqt5concurrent5 libqt5core5a libqt5dbus5 
  libqt5designer5 libqt5designercomponents5 libqt5gui5 libqt5help5 
  libqt5network5 libqt5positioning5 libqt5printsupport5 libqt5qml5 
  libqt5qmlmodels5 libqt5qmlworkerscript5 libqt5quick5 libqt5quicktest5 
  libqt5quickwidgets5 libqt5sensors5 libqt5serialport5 libqt5sql5 
  libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5webchannel5 libqt5webkit5 
  libqt5widgets5 libqt5xml5 libqt5xmlpatterns5 libquadmath0 libstdc++-10-dev 
  libtinfo-dev libtirpc-dev libtsan0 libubsan1 libxcb-xinerama0 libxcb-xinput0 
  libyaml-cpp0.6 libz3-4 libz3-dev linux-libc-dev llvm-11 llvm-11-dev 
  llvm-11-linker-tools llvm-11-runtime llvm-11-tools llvm-12 llvm-12-dev 
  llvm-12-linker-tools llvm-12-runtime llvm-12-tools make manpages-dev 
  python3-pygments qdoc-qt5 qhelpgenerator-qt5 qml-module-qtgraphicaleffects 
  qml-module-qtqml qml-module-qtqml-models2 qml-module-qtquick-controls 
  qml-module-qtquick-layouts qml-module-qtquick-window2 qml-module-qtquick2 
  qmlscene qt3d5-doc qt5-assistant qt5-doc qt5-gtk-platformtheme 
  qt5-qmltooling-plugins qtattributionsscanner-qt5 qtbase5-dev-tools 
  qtbase5-doc qtcharts5-doc qtchooser qtconnectivity5-doc qtcreator 
  qtcreator-data qtcreator-doc qtdatavisualization5-doc 
  qtdeclarative5-dev-tools qtdeclarative5-doc qtgraphicaleffects5-doc 
  qtlocation5-doc qtmultimedia5-doc qtnetworkauth5-doc qtquickcontrols2-5-doc 
  qtquickcontrols5-doc qtscript5-doc qtscxml5-doc qtsensors5-doc 
  qtserialbus5-doc qtserialport5-doc qtsvg5-doc qttools5-dev-tools 
  qttools5-doc qttranslations5-l10n qtvirtualkeyboard5-doc qtwayland5-doc 
  qtwebchannel5-doc qtwebengine5-doc qtwebsockets5-doc qtwebview5-doc 
  qtx11extras5-doc qtxmlpatterns5-dev-tools qtxmlpatterns5-doc rpcsvc-proto 
0 upgraded, 149 newly installed, 0 to remove and 0 not upgraded. 
Need to get 339 MB/351 MB of archives. 
After this operation, 1,463 MB of additional disk space will be used. 
Do you want to continue? [Y/n] Y 
Media change: please insert the disc labeled 
 'Ubuntu 21.04 _Hirsute Hippo_ - Release amd64 (20210420)' 
in the drive '/cdrom/' and press [Enter]
```

---

### Post by coffeecat on 2021-05-27
I've added BBCode code tags to your terminal output. Please use code tags when posting terminal output or the contents of config files. This is to preserve columnar formatting and make the output readable. There's a link in my sig for using BBCode code tags if you need it.

The message about the CDROM is probably because you have the install medium set as a software source. Even if you originally installed with a USB flash drive, software sources shows this as CDROM.

Assuming you are using standard Ubuntu with the gnome desktop, open Software & Updates, and make sure you are viewing the Ubuntu Software tab. Under "Installable from CD-ROM/DVD", you'll see a checkbox. Untick it. Then run:

```
sudo apt update
```

That should stop the CD-ROM message from appearing.

The default with any installation is not to have the CD-ROM source ticked. Perhaps you ticked it accidentally or needed to enable it as a source for some other reason. It's worth knowing about this, because it trips up a lot of people. Let us know if that works.

---

