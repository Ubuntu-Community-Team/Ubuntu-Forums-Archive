---
title: "APT shows 3 Pkgs to Upgrade, but Holds them Back ???"
date: 2019-09-19
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2019-09-19
After recently upgrading from v16.04 to v18.04 ...
Curious why it shows 3 pkgs after 'update' but then holds those pkgs back ?!?!?

```

 sudo apt update
Hit:1 http://deb.opera.com/opera-stable stable InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic InRelease                    
Hit:3 http://archive.canonical.com/ubuntu bionic InRelease               
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Hit:5 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease
Fetched 88.7 kB in 1s (59.7 kB/s)                 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.

~$ apt list --upgradable
Listing... Done
imagemagick/bionic-security,bionic-updates 8:6.9.7.4+dfsg-16ubuntu6.7 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.14]
imagemagick-6.q16/bionic-security,bionic-updates 8:6.9.7.4+dfsg-16ubuntu6.7 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.14]
qtchooser/bionic 64-ga1b6736-5 amd64 [upgradable from: 52-gae5eeef-2build1~gcc5.2]

~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  imagemagick imagemagick-6.q16 qtchooser
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


```

Any suggestions, or should we be concerned - as 'imagemagick' is a Security Update?
And just so you know, Yes I did do the following ...

```

~$ sudo apt autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  imagemagick imagemagick-6.q16 qtchooser
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


```

---

### Post by mc4man on 2019-09-19
Maybe it needs to install new packages..
You could try this simulation (-s)
```
sudo apt-get -s --with-new-pkgs upgrade
```

If it works ok then rerun without the -s

Otherwise  try singly.
sudo apt install qtchooser
sudo apt install imagemagick

---

### Post by Rick St. George on 2019-09-19
> **mc4man said:**
> Maybe it needs to install new packages..
You could try this simulation (-s)
```
sudo apt-get -s --with-new-pkgs upgrade
```

If it works ok then rerun without the -s

Otherwise  try singly.
sudo apt install qtchooser
sudo apt install imagemagick

WOW ... this is what I get ... 

```

~$ sudo apt-get -s --with-new-pkgs upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  imagemagick imagemagick-6.q16 qtchooser
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

~$ sudo apt install qtchooser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  extlinux fonts-dejavu hyphen-en-gb hyphen-en-us libflac++6v5 libpodofo0.9.3 libportsmf0v5
  libsoundtouch1 libvamp-hostsdk3v5 luckybackup-data scribus-data unetbootin-translations
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  audacity drumkv1 ffado-mixer-qt4 hydrogen libattica0.4 libdbusmenu-qt2 libkdecore5 libkdeui5
  libphonon4 libqca2 libqca2-plugins libqjson0 libqt4-dbus libqt4-declarative libqt4-designer
  libqt4-help libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql libqt4-svg
  libqt4-test libqt4-xml libqt4-xmlpatterns libqtassistantclient4 libqtcore4 libqtdbus4 libqtgui4
  libqtscript4-core libqtwebkit4 libsuil-0-0 lmms luckybackup phonon phonon-backend-gstreamer
  python-qt4 python-qt4-dbus qasconfig qashctl qasmixer qdbus qmidiarp qmidiroute samplv1 scribus
  soprano-daemon synthv1 unetbootin
The following packages will be upgraded:
  qtchooser
1 upgraded, 0 newly installed, 49 to remove and 4 not upgraded.
Need to get 24.1 kB of archives.
After this operation, 191 MB disk space will be freed.
Do you want to continue? [Y/n] 


```

Wants to REMOVE 49 now ??? Doesn't seem safe. Why did autoclean and autoremove NOT Remove them ???
Holding off till further analysis and comments .... Thanks!

(EDIT) Just noticed, qtchooser IS installed !!! And imagemagick has unmet dependencies !!!

---

### Post by #&amp;thj^% on 2019-09-19
Could you please post the return for:
```
sudo apt -o Debug::pkgProblemResolver=yes install imagemagick imagemagick-6.q16 qtchooser
```
Also post back:
```
inxi -r
```

---

### Post by Rick St. George on 2019-09-19
> **1fallen said:**
> Could you please post the return for:
```
sudo apt -o Debug::pkgProblemResolver=yes install imagemagick imagemagick-6.q16 qtchooser
```
Also post back:
```
inxi -r
```

Remember ... You asked for it ...

```

~$ sudo apt -o Debug::pkgProblemResolver=yes install imagemagick imagemagick-6.q16 qtchooser
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Starting pkgProblemResolver with broken count: 47
Starting 2 pkgProblemResolver with broken count: 47
Investigating (0) libqtgui4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK NPb Ib >
Broken libqtgui4:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqtcore4:amd64 0 as a solution to libqtgui4:amd64 26
  Added libqtcore4:amd64 to the remove list
  Fixing libqtgui4:amd64 via keep of libqtcore4:amd64
Investigating (0) gem-plugin-magick:amd64 < 1:0.93.3-9build1 @ii mK Ib >
Broken gem-plugin-magick:amd64 Depends on libmagickcore-6.q16-2:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mR > (>= 8:6.8.8.2)
  Considering libmagickcore-6.q16-2:amd64 0 as a solution to gem-plugin-magick:amd64 12
  Added libmagickcore-6.q16-2:amd64 to the remove list
  Fixing gem-plugin-magick:amd64 via keep of libmagickcore-6.q16-2:amd64
Investigating (0) imagemagick-6-common:amd64 < none -> 8:6.9.7.4+dfsg-16ubuntu6.7 @un uN Ib >
Broken imagemagick-6-common:amd64 Breaks on libmagickcore-6.q16-2:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mK Ib > (< 8:6.9.6.2+dfsg-3~)
  Considering libmagickcore-6.q16-2:amd64 0 as a solution to imagemagick-6-common:amd64 4
  Added libmagickcore-6.q16-2:amd64 to the remove list
  Fixing imagemagick-6-common:amd64 via remove of libmagickcore-6.q16-2:amd64
Investigating (0) libmagick++-6.q16-5v5:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mK Ib >
Broken libmagick++-6.q16-5v5:amd64 Depends on libmagickcore-6.q16-2:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mR > (>= 8:6.8.9.9)
  Considering libmagickcore-6.q16-2:amd64 0 as a solution to libmagick++-6.q16-5v5:amd64 -1
  Removing libmagick++-6.q16-5v5:amd64 rather than change libmagickcore-6.q16-2:amd64
Investigating (0) libmagickwand-6.q16-2:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mK Ib >
Broken libmagickwand-6.q16-2:amd64 Depends on libmagickcore-6.q16-2:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mR > (>= 8:6.8.9.9)
  Considering libmagickcore-6.q16-2:amd64 0 as a solution to libmagickwand-6.q16-2:amd64 -1
  Removing libmagickwand-6.q16-2:amd64 rather than change libmagickcore-6.q16-2:amd64
Investigating (1) qtchooser:amd64 < 52-gae5eeef-2build1~gcc5.2 -> 64-ga1b6736-5 @ii pumU Ib >
Broken qtchooser:amd64 Breaks on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK > (< 4:4.8.7+dfsg-7~)
  Considering libqtcore4:amd64 0 as a solution to qtchooser:amd64 10000
  Added libqtcore4:amd64 to the remove list
  Fixing qtchooser:amd64 via remove of libqtcore4:amd64
Investigating (1) libqtgui4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK NPb Ib >
Broken libqtgui4:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqtcore4:amd64 0 as a solution to libqtgui4:amd64 26
  Added libqtcore4:amd64 to the remove list
  Fixing libqtgui4:amd64 via keep of libqtcore4:amd64
Investigating (1) gem-plugin-magick:amd64 < 1:0.93.3-9build1 @ii mK Ib >
Broken gem-plugin-magick:amd64 Depends on libmagick++-6.q16-5v5:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mR > (>= 8:6.8.9.9-6)
  Considering libmagick++-6.q16-5v5:amd64 -1 as a solution to gem-plugin-magick:amd64 12
  Added libmagick++-6.q16-5v5:amd64 to the remove list
Broken gem-plugin-magick:amd64 Depends on libmagickcore-6.q16-2:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mR > (>= 8:6.8.8.2)
  Considering libmagickcore-6.q16-2:amd64 0 as a solution to gem-plugin-magick:amd64 12
  Added libmagickcore-6.q16-2:amd64 to the remove list
  Fixing gem-plugin-magick:amd64 via keep of libmagick++-6.q16-5v5:amd64
  Fixing gem-plugin-magick:amd64 via keep of libmagickcore-6.q16-2:amd64
Investigating (1) imagemagick-6-common:amd64 < none -> 8:6.9.7.4+dfsg-16ubuntu6.7 @un uN Ib >
Broken imagemagick-6-common:amd64 Breaks on libmagickcore-6.q16-2:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mK Ib > (< 8:6.9.6.2+dfsg-3~)
  Considering libmagickcore-6.q16-2:amd64 0 as a solution to imagemagick-6-common:amd64 4
  Added libmagickcore-6.q16-2:amd64 to the remove list
  Fixing imagemagick-6-common:amd64 via remove of libmagickcore-6.q16-2:amd64
Investigating (1) libmagick++-6.q16-5v5:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mK Ib >
Broken libmagick++-6.q16-5v5:amd64 Depends on libmagickcore-6.q16-2:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mR > (>= 8:6.8.9.9)
  Considering libmagickcore-6.q16-2:amd64 0 as a solution to libmagick++-6.q16-5v5:amd64 -1
  Removing libmagick++-6.q16-5v5:amd64 rather than change libmagickcore-6.q16-2:amd64
Investigating (2) qtchooser:amd64 < 52-gae5eeef-2build1~gcc5.2 -> 64-ga1b6736-5 @ii pumU Ib >
Broken qtchooser:amd64 Breaks on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK > (< 4:4.8.7+dfsg-7~)
  Considering libqtcore4:amd64 0 as a solution to qtchooser:amd64 10000
  Added libqtcore4:amd64 to the remove list
  Fixing qtchooser:amd64 via remove of libqtcore4:amd64
Investigating (2) libqtgui4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK NPb Ib >
Broken libqtgui4:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqtcore4:amd64 10000 as a solution to libqtgui4:amd64 26
  Removing libqtgui4:amd64 rather than change libqtcore4:amd64
Investigating (2) libqt4-declarative:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken libqt4-declarative:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqtcore4:amd64 10000 as a solution to libqt4-declarative:amd64 24
  Removing libqt4-declarative:amd64 rather than change libqtcore4:amd64
Investigating (2) libqtdbus4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken libqtdbus4:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqtcore4:amd64 10000 as a solution to libqtdbus4:amd64 21
  Removing libqtdbus4:amd64 rather than change libqtcore4:amd64
Investigating (2) libqt4-network:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken libqt4-network:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqtcore4:amd64 10000 as a solution to libqt4-network:amd64 13
  Removing libqt4-network:amd64 rather than change libqtcore4:amd64
Investigating (2) gem-plugin-magick:amd64 < 1:0.93.3-9build1 @ii mK Ib >
Broken gem-plugin-magick:amd64 Depends on libmagick++-6.q16-5v5:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mR > (>= 8:6.8.9.9-6)
  Considering libmagick++-6.q16-5v5:amd64 -1 as a solution to gem-plugin-magick:amd64 12
  Added libmagick++-6.q16-5v5:amd64 to the remove list
Broken gem-plugin-magick:amd64 Depends on libmagickcore-6.q16-2:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mR > (>= 8:6.8.8.2)
  Considering libmagickcore-6.q16-2:amd64 0 as a solution to gem-plugin-magick:amd64 12
  Added libmagickcore-6.q16-2:amd64 to the remove list
  Fixing gem-plugin-magick:amd64 via keep of libmagick++-6.q16-5v5:amd64
  Fixing gem-plugin-magick:amd64 via keep of libmagickcore-6.q16-2:amd64
Investigating (2) libqt4-xml:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken libqt4-xml:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqtcore4:amd64 10000 as a solution to libqt4-xml:amd64 11
  Removing libqt4-xml:amd64 rather than change libqtcore4:amd64
Investigating (2) qdbus:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken qdbus:amd64 Depends on libqt4-xml:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqt4-xml:amd64 10000 as a solution to qdbus:amd64 4
  Removing qdbus:amd64 rather than change libqt4-xml:amd64
Investigating (2) imagemagick-6-common:amd64 < none -> 8:6.9.7.4+dfsg-16ubuntu6.7 @un uN Ib >
Broken imagemagick-6-common:amd64 Breaks on libmagickcore-6.q16-2:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mK Ib > (< 8:6.9.6.2+dfsg-3~)
  Considering libmagickcore-6.q16-2:amd64 12 as a solution to imagemagick-6-common:amd64 4
  Holding Back imagemagick-6-common:amd64 rather than change libmagickcore-6.q16-2:amd64
Investigating (2) libqt4-dbus:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken libqt4-dbus:amd64 Depends on libqtdbus4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqtdbus4:amd64 10000 as a solution to libqt4-dbus:amd64 4
  Removing libqt4-dbus:amd64 rather than change libqtdbus4:amd64
Investigating (2) libqt4-script:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken libqt4-script:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqtcore4:amd64 10000 as a solution to libqt4-script:amd64 3
  Removing libqt4-script:amd64 rather than change libqtcore4:amd64
Investigating (2) libqt4-svg:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken libqt4-svg:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqtcore4:amd64 10000 as a solution to libqt4-svg:amd64 2
  Removing libqt4-svg:amd64 rather than change libqtcore4:amd64
Investigating (2) libmagickwand-6.q16-3:amd64 < none -> 8:6.9.7.4+dfsg-16ubuntu6.7 @un uN Ib >
Broken libmagickwand-6.q16-3:amd64 Depends on imagemagick-6-common:amd64 < none | 8:6.9.7.4+dfsg-16ubuntu6.7 @un uH > (>= 8:6.9.6.2+dfsg-3)
  Considering imagemagick-6-common:amd64 4 as a solution to libmagickwand-6.q16-3:amd64 2
  Holding Back libmagickwand-6.q16-3:amd64 rather than change imagemagick-6-common:amd64
Investigating (2) libmagickcore-6.q16-3-extra:amd64 < none -> 8:6.9.7.4+dfsg-16ubuntu6.7 @un uN Ib >
Broken libmagickcore-6.q16-3-extra:amd64 Depends on libmagickwand-6.q16-3:amd64 < none | 8:6.9.7.4+dfsg-16ubuntu6.7 @un uH > (>= 8:6.9.6.8)
  Considering libmagickwand-6.q16-3:amd64 2 as a solution to libmagickcore-6.q16-3-extra:amd64 1
  Holding Back libmagickcore-6.q16-3-extra:amd64 rather than change libmagickwand-6.q16-3:amd64
Investigating (2) libqt4-xmlpatterns:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken libqt4-xmlpatterns:amd64 Depends on libqt4-network:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqt4-network:amd64 10000 as a solution to libqt4-xmlpatterns:amd64 1
  Removing libqt4-xmlpatterns:amd64 rather than change libqt4-network:amd64
Investigating (2) libqt4-opengl:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken libqt4-opengl:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqtcore4:amd64 10000 as a solution to libqt4-opengl:amd64 0
  Removing libqt4-opengl:amd64 rather than change libqtcore4:amd64
Investigating (2) libqt4-sql:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK NPb Ib >
Broken libqt4-sql:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqtcore4:amd64 10000 as a solution to libqt4-sql:amd64 0
  Removing libqt4-sql:amd64 rather than change libqtcore4:amd64
Investigating (2) libmagickcore-6.q16-2:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mK Ib >
Broken libmagickcore-6.q16-2:amd64 Depends on imagemagick-common:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mR > (= 8:6.8.9.9-7ubuntu5.14)
  Considering imagemagick-common:amd64 2 as a solution to libmagickcore-6.q16-2:amd64 12
  Added imagemagick-common:amd64 to the remove list
  Fixing libmagickcore-6.q16-2:amd64 via keep of imagemagick-common:amd64
Investigating (2) libsuil-0-0:amd64 < 0.8.2~dfsg0-1 @ii mK Ib >
Broken libsuil-0-0:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.5.3)
  Considering libqtcore4:amd64 10000 as a solution to libsuil-0-0:amd64 0
  Removing libsuil-0-0:amd64 rather than change libqtcore4:amd64
Investigating (2) scribus:amd64 < 1.4.6+dfsg-2ubuntu0.1 @ii mK Ib >
Broken scribus:amd64 Depends on libqt4-network:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.5.3)
  Considering libqt4-network:amd64 10000 as a solution to scribus:amd64 0
  Removing scribus:amd64 rather than change libqt4-network:amd64
Investigating (2) libphonon4:amd64 < 4:4.8.3-0ubuntu3 @ii mK Ib >
Broken libphonon4:amd64 Depends on libqt4-dbus:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.8.1)
  Considering libqt4-dbus:amd64 10000 as a solution to libphonon4:amd64 0
  Removing libphonon4:amd64 rather than change libqt4-dbus:amd64
Investigating (2) libqt4-designer:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken libqt4-designer:amd64 Depends on libqt4-script:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqt4-script:amd64 10000 as a solution to libqt4-designer:amd64 -1
  Removing libqt4-designer:amd64 rather than change libqt4-script:amd64
Investigating (2) libkdecore5:amd64 < 4:4.14.16-0ubuntu3.2 @ii mK Ib >
Broken libkdecore5:amd64 Depends on libqt4-dbus:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.8.0)
  Considering libqt4-dbus:amd64 10000 as a solution to libkdecore5:amd64 -1
  Removing libkdecore5:amd64 rather than change libqt4-dbus:amd64
Investigating (2) drumkv1:amd64 < 0.7.1-1 @ii mK NPb Ib >
Broken drumkv1:amd64 Depends on libqt4-xml:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.5.3)
  Considering libqt4-xml:amd64 10000 as a solution to drumkv1:amd64 -1
  Removing drumkv1:amd64 rather than change libqt4-xml:amd64
Investigating (2) qasconfig:amd64 < 0.18.0-1 @ii mK Ib >
Broken qasconfig:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.7.0~beta1)
  Considering libqtcore4:amd64 10000 as a solution to qasconfig:amd64 -1
  Removing qasconfig:amd64 rather than change libqtcore4:amd64
Investigating (2) python-qt4:amd64 < 4.11.4+dfsg-1build4 @ii mK Ib >
Broken python-qt4:amd64 Depends on libqt4-dbus:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.8.0-1~)
  Considering libqt4-dbus:amd64 10000 as a solution to python-qt4:amd64 -1
  Removing python-qt4:amd64 rather than change libqt4-dbus:amd64
Investigating (2) synthv1:amd64 < 0.7.1-1 @ii mK NPb Ib >
Broken synthv1:amd64 Depends on libqt4-xml:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.5.3)
  Considering libqt4-xml:amd64 10000 as a solution to synthv1:amd64 -1
  Removing synthv1:amd64 rather than change libqt4-xml:amd64
Investigating (2) qashctl:amd64 < 0.18.0-1 @ii mK Ib >
Broken qashctl:amd64 Depends on libqt4-svg:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.5.3)
  Considering libqt4-svg:amd64 10000 as a solution to qashctl:amd64 -1
  Removing qashctl:amd64 rather than change libqt4-svg:amd64
Investigating (2) libqt4-test:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken libqt4-test:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqtcore4:amd64 10000 as a solution to libqt4-test:amd64 -1
  Removing libqt4-test:amd64 rather than change libqtcore4:amd64
Investigating (2) hydrogen:amd64 < 0.9.6.1-1build1 @ii mK Ib >
Broken hydrogen:amd64 Depends on libqt4-network:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.5.3)
  Considering libqt4-network:amd64 10000 as a solution to hydrogen:amd64 -1
  Removing hydrogen:amd64 rather than change libqt4-network:amd64
Investigating (2) libqca2-plugins:amd64 < 2.1.1-2ubuntu1 @ii mK Ib >
Broken libqca2-plugins:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.8.0)
  Considering libqtcore4:amd64 10000 as a solution to libqca2-plugins:amd64 -1
  Removing libqca2-plugins:amd64 rather than change libqtcore4:amd64
Investigating (2) phonon-backend-gstreamer:amd64 < 4:4.8.2-0ubuntu2 @ii mK Ib >
Broken phonon-backend-gstreamer:amd64 Depends on libphonon4:amd64 < 4:4.8.3-0ubuntu3 @ii mR > (>= 4:4.7.1~)
  Considering libphonon4:amd64 10000 as a solution to phonon-backend-gstreamer:amd64 -1
  Removing phonon-backend-gstreamer:amd64 rather than change libphonon4:amd64
Investigating (2) samplv1:amd64 < 0.7.1-1 @ii mK NPb Ib >
Broken samplv1:amd64 Depends on libqt4-xml:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.5.3)
  Considering libqt4-xml:amd64 10000 as a solution to samplv1:amd64 -1
  Removing samplv1:amd64 rather than change libqt4-xml:amd64
Investigating (2) libmagick++-6.q16-5v5:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mK Ib >
Broken libmagick++-6.q16-5v5:amd64 Depends on libmagickwand-6.q16-2:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mR > (>= 8:6.8.8.9)
  Considering libmagickwand-6.q16-2:amd64 -1 as a solution to libmagick++-6.q16-5v5:amd64 12
  Added libmagickwand-6.q16-2:amd64 to the remove list
  Fixing libmagick++-6.q16-5v5:amd64 via keep of libmagickwand-6.q16-2:amd64
Investigating (2) unetbootin:amd64 < 608-1 @ii mK Ib >
Broken unetbootin:amd64 Depends on libqt4-network:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.5.3)
  Considering libqt4-network:amd64 10000 as a solution to unetbootin:amd64 -1
  Removing unetbootin:amd64 rather than change libqt4-network:amd64
Investigating (2) qasmixer:amd64 < 0.18.0-1 @ii mK Ib >
Broken qasmixer:amd64 Depends on libqt4-network:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.5.3)
  Considering libqt4-network:amd64 10000 as a solution to qasmixer:amd64 -1
  Removing qasmixer:amd64 rather than change libqt4-network:amd64
Investigating (2) python-qt4-dbus:amd64 < 4.11.4+dfsg-1build4 @ii mK Ib >
Broken python-qt4-dbus:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.8.0-1~)
  Considering libqtcore4:amd64 10000 as a solution to python-qt4-dbus:amd64 -1
  Removing python-qt4-dbus:amd64 rather than change libqtcore4:amd64
Investigating (2) libqt4-help:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken libqt4-help:amd64 Depends on libqt4-network:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqt4-network:amd64 10000 as a solution to libqt4-help:amd64 -1
  Removing libqt4-help:amd64 rather than change libqt4-network:amd64
Investigating (2) libattica0.4:amd64 < 0.4.2-2 @ii mK Ib >
Broken libattica0.4:amd64 Depends on libqt4-network:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.7)
  Considering libqt4-network:amd64 10000 as a solution to libattica0.4:amd64 -1
  Removing libattica0.4:amd64 rather than change libqt4-network:amd64
Investigating (2) qmidiroute:amd64 < 0.3.0-2 @ii mK Ib >
Broken qmidiroute:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.7.0~beta1)
  Considering libqtcore4:amd64 10000 as a solution to qmidiroute:amd64 -1
  Removing qmidiroute:amd64 rather than change libqtcore4:amd64
Investigating (2) qmidiarp:amd64 < 0.6.3-1 @ii mK NPb Ib >
Broken qmidiarp:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.7.0~beta1)
  Considering libqtcore4:amd64 10000 as a solution to qmidiarp:amd64 -1
  Removing qmidiarp:amd64 rather than change libqtcore4:amd64
Investigating (2) libqtassistantclient4:amd64 < 4.6.3-7 @ii mK Ib >
Broken libqtassistantclient4:amd64 Depends on libqt4-network:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.8.1)
  Considering libqt4-network:amd64 10000 as a solution to libqtassistantclient4:amd64 -1
  Removing libqtassistantclient4:amd64 rather than change libqt4-network:amd64
Investigating (2) libqt4-scripttools:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mK Ib >
Broken libqt4-scripttools:amd64 Depends on libqt4-script:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (= 4:4.8.7+dfsg-5ubuntu2)
  Considering libqt4-script:amd64 10000 as a solution to libqt4-scripttools:amd64 -1
  Removing libqt4-scripttools:amd64 rather than change libqt4-script:amd64
Investigating (2) luckybackup:amd64 < 0.4.8-2 @ii mK Ib >
Broken luckybackup:amd64 Depends on libqt4-network:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.5.3)
  Considering libqt4-network:amd64 10000 as a solution to luckybackup:amd64 -1
  Removing luckybackup:amd64 rather than change libqt4-network:amd64
Investigating (2) libqca2:amd64 < 2.1.1-2ubuntu1 @ii mK Ib >
Broken libqca2:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.8.0)
  Considering libqtcore4:amd64 10000 as a solution to libqca2:amd64 -1
  Removing libqca2:amd64 rather than change libqtcore4:amd64
Investigating (2) libdbusmenu-qt2:amd64 < 0.9.3+16.04.20160218-0ubuntu1 @ii mK Ib >
Broken libdbusmenu-qt2:amd64 Depends on libqt4-dbus:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.5.3)
  Considering libqt4-dbus:amd64 10000 as a solution to libdbusmenu-qt2:amd64 -1
  Removing libdbusmenu-qt2:amd64 rather than change libqt4-dbus:amd64
Investigating (2) libqtwebkit4:amd64 < 2.3.2-0ubuntu11 @ii mK Ib >
Broken libqtwebkit4:amd64 Depends on libqt4-network:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.7.0~beta1)
  Considering libqt4-network:amd64 10000 as a solution to libqtwebkit4:amd64 -1
  Removing libqtwebkit4:amd64 rather than change libqt4-network:amd64
Investigating (2) lmms:amd64 < 1.1.3-1build1 @ii mK Ib >
Broken lmms:amd64 Depends on libqt4-xml:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.5.3)
  Considering libqt4-xml:amd64 10000 as a solution to lmms:amd64 -1
  Removing lmms:amd64 rather than change libqt4-xml:amd64
Investigating (2) libqtscript4-core:amd64 < 0.2.0-1 @ii mK Ib >
Broken libqtscript4-core:amd64 Depends on libqt4-script:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.8.0)
  Considering libqt4-script:amd64 10000 as a solution to libqtscript4-core:amd64 -2
  Removing libqtscript4-core:amd64 rather than change libqt4-script:amd64
Investigating (2) soprano-daemon:amd64 < 2.9.4+dfsg1-0ubuntu3 @ii mK NPb Ib >
Broken soprano-daemon:amd64 Depends on libqt4-dbus:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.5.3)
  Considering libqt4-dbus:amd64 10000 as a solution to soprano-daemon:amd64 -2
  Removing soprano-daemon:amd64 rather than change libqt4-dbus:amd64
Investigating (2) libkdeui5:amd64 < 4:4.14.16-0ubuntu3.2 @ii mK NPb Ib >
Broken libkdeui5:amd64 Depends on libattica0.4:amd64 < 0.4.2-2 @ii mR > (>= 0.4.2)
  Considering libattica0.4:amd64 10000 as a solution to libkdeui5:amd64 -2
  Removing libkdeui5:amd64 rather than change libattica0.4:amd64
Investigating (2) libqjson0:amd64 < 0.8.1-3 @ii mK Ib >
Broken libqjson0:amd64 Depends on libqtcore4:amd64 < 4:4.8.7+dfsg-5ubuntu2 @ii mR > (>= 4:4.7.0~beta1)
  Considering libqtcore4:amd64 10000 as a solution to libqjson0:amd64 -2
  Removing libqjson0:amd64 rather than change libqtcore4:amd64
Investigating (2) phonon:amd64 < 4:4.8.3-0ubuntu3 @ii mK Ib >
Broken phonon:amd64 Depends on libphonon4:amd64 < 4:4.8.3-0ubuntu3 @ii mR > (>= 4:4.8.3-0ubuntu3)
  Considering libphonon4:amd64 10000 as a solution to phonon:amd64 -2
  Removing phonon:amd64 rather than change libphonon4:amd64
Investigating (3) imagemagick-6.q16:amd64 < 8:6.8.9.9-7ubuntu5.14 -> 8:6.9.7.4+dfsg-16ubuntu6.7 @ii pumU NPb Ib >
Broken imagemagick-6.q16:amd64 Depends on libmagickwand-6.q16-3:amd64 < none | 8:6.9.7.4+dfsg-16ubuntu6.7 @un uH > (>= 8:6.9.6.8)
  Considering libmagickwand-6.q16-3:amd64 2 as a solution to imagemagick-6.q16:amd64 10015
  Re-Instated imagemagick-6-common:amd64
  Re-Instated libmagickwand-6.q16-3:amd64
Investigating (3) imagemagick-6-common:amd64 < none -> 8:6.9.7.4+dfsg-16ubuntu6.7 @un uN Ib >
Broken imagemagick-6-common:amd64 Breaks on imagemagick-common:amd64 < 8:6.8.9.9-7ubuntu5.14 @ii mK > (< 8:6.9.2.10+dfsg-1~)
  Considering imagemagick-common:amd64 12 as a solution to imagemagick-6-common:amd64 4
  Holding Back imagemagick-6-common:amd64 rather than change imagemagick-common:amd64
Investigating (3) libmagickwand-6.q16-3:amd64 < none -> 8:6.9.7.4+dfsg-16ubuntu6.7 @un uN Ib >
Broken libmagickwand-6.q16-3:amd64 Depends on imagemagick-6-common:amd64 < none | 8:6.9.7.4+dfsg-16ubuntu6.7 @un uH > (>= 8:6.9.6.2+dfsg-3)
  Considering imagemagick-6-common:amd64 4 as a solution to libmagickwand-6.q16-3:amd64 2
  Holding Back libmagickwand-6.q16-3:amd64 rather than change imagemagick-6-common:amd64
Investigating (3) audacity:amd64 < 2.1.2-1 @ii mK Ib >
Broken audacity:amd64 Depends on libsuil-0-0:amd64 < 0.8.2~dfsg0-1 @ii mR > (>= 0.8.0~dfsg0)
  Considering libsuil-0-0:amd64 10000 as a solution to audacity:amd64 1
  Removing audacity:amd64 rather than change libsuil-0-0:amd64
Investigating (3) ffado-mixer-qt4:amd64 < 2.2.1-3 @ii mK Ib >
Broken ffado-mixer-qt4:amd64 Depends on python-qt4:amd64 < 4.11.4+dfsg-1build4 @ii mR >
  Considering python-qt4:amd64 10000 as a solution to ffado-mixer-qt4:amd64 -1
  Removing ffado-mixer-qt4:amd64 rather than change python-qt4:amd64
Investigating (4) imagemagick-6.q16:amd64 < 8:6.8.9.9-7ubuntu5.14 -> 8:6.9.7.4+dfsg-16ubuntu6.7 @ii pumU NPb Ib >
Broken imagemagick-6.q16:amd64 Depends on libmagickwand-6.q16-3:amd64 < none | 8:6.9.7.4+dfsg-16ubuntu6.7 @un uH > (>= 8:6.9.6.8)
  Considering libmagickwand-6.q16-3:amd64 2 as a solution to imagemagick-6.q16:amd64 10015
  Considering libmagickwand-6.q16-3:amd64 2 as a solution to imagemagick-6.q16:amd64 10015
Investigating (4) libmagickcore-6.q16-3:amd64 < none -> 8:6.9.7.4+dfsg-16ubuntu6.7 @un uN Ib >
Broken libmagickcore-6.q16-3:amd64 Depends on imagemagick-6-common:amd64 < none | 8:6.9.7.4+dfsg-16ubuntu6.7 @un uH > (>= 8:6.9.6.2+dfsg-3)
  Considering imagemagick-6-common:amd64 4 as a solution to libmagickcore-6.q16-3:amd64 4
  Holding Back libmagickcore-6.q16-3:amd64 rather than change imagemagick-6-common:amd64
Investigating (5) imagemagick-6.q16:amd64 < 8:6.8.9.9-7ubuntu5.14 -> 8:6.9.7.4+dfsg-16ubuntu6.7 @ii pumU NPb Ib >
Broken imagemagick-6.q16:amd64 Depends on libmagickcore-6.q16-3:amd64 < none | 8:6.9.7.4+dfsg-16ubuntu6.7 @un uH > (>= 8:6.9.6.8)
  Considering libmagickcore-6.q16-3:amd64 4 as a solution to imagemagick-6.q16:amd64 10015
    Reinst Failed because of imagemagick-6-common:amd64
  Considering libmagickcore-6.q16-3:amd64 4 as a solution to imagemagick-6.q16:amd64 10015
Broken imagemagick-6.q16:amd64 Depends on libmagickwand-6.q16-3:amd64 < none | 8:6.9.7.4+dfsg-16ubuntu6.7 @un uH > (>= 8:6.9.6.8)
  Considering libmagickwand-6.q16-3:amd64 2 as a solution to imagemagick-6.q16:amd64 10015
  Considering libmagickwand-6.q16-3:amd64 2 as a solution to imagemagick-6.q16:amd64 10015
Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 imagemagick-6.q16 : Depends: libmagickcore-6.q16-3 (>= 8:6.9.6.8) but it is not going to be installed
                     Depends: libmagickwand-6.q16-3 (>= 8:6.9.6.8) but it is not going to be installed
                     Recommends: libmagickcore-6.q16-3-extra but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


~$ inxi -r
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
           deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted #Added by software-properties
           deb http://us.archive.ubuntu.com/ubuntu/ bionic-security main restricted
           deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-security main restricted #Added by software-properties
           deb [arch=amd64] http://download.virtualbox.org/virtualbox/debian bionic contrib
           deb http://archive.canonical.com/ubuntu bionic partner
           Active apt sources in file: /etc/apt/sources.list.d/kdenlive-ubuntu-kdenlive-stable-xenial.list
           deb http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu bionic main
           Active apt sources in file: /etc/apt/sources.list.d/opera.list
           deb http://deb.opera.com/opera-stable/ stable non-free
           Active apt sources in file: /etc/apt/sources.list.d/thomas-schiex-ubuntu-blender-xenial.list
           deb http://ppa.launchpad.net/thomas-schiex/blender/ubuntu bionic main
           Active apt sources in file: /etc/apt/sources.list.d/webupd8team-ubuntu-java-xenial.list
           deb http://ppa.launchpad.net/webupd8team/java/ubuntu bionic main
           Active apt sources in file: /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list
           deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic main


```

Any hints? Is something wrong I can fix?? BTW did release upgrade according to;
[https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver](https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver)
The Debian Way.

---

### Post by #&amp;thj^% on 2019-09-19
> **Rick St. George said:**
> Remember ... You asked for it ...
 

I did, I did. :lolflag:
> **Rick St. George said:**
> 
 BTW did release upgrade according to;
[https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver](https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver)
The Debian Way.

Yep thought so. But this is a bit worrisome, **"ProblemResolver with broken count: 47"**
I need to think long and hard on this one.:(
Congrats you have the highest broken count I personally have seen. :p
What happens with:
```
sudo apt -s install -f
```

---

### Post by Rick St. George on 2019-09-19
> **1fallen said:**
> 
What happens with:
```
sudo apt -s install -f
```

The following;


```

~$ sudo apt -s install -f
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```


In Synaptic Pkg Mgr, I get this ...

```

E: Unable to correct dependencies
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the list directory

```

---

### Post by #&amp;thj^% on 2019-09-19
Mr St. George I can be a handful on these types of problems, now I'm thinking a nuclear approach would work, but bare in mind I used the term "_THINK_" here. :)
But if your willing to try:
```
dpkg -l | grep ^iU | awk '{print $2}' | xargs sudo dpkg --purge
```
That should remove all broken packages. (Might not hurt to check against the list you just showed me) 
Now again run:
```
sudo apt install -f
```
To finish.
And as Always>>>Back-ups Back-ups Back-ups.

---

### Post by mc4man on 2019-09-19
On cell phone so basically forget me..
However it would appear nothing critical is broken so method of subtraction, then addition should be  doable.. 
Just keep track of applications removed  so you can put them back. 
( applications will install any needed libs..

---

### Post by #&amp;thj^% on 2019-09-19
> **mc4man said:**
> On cell phone so basically forget me..

We will never forget you! ;)

---

### Post by mc4man on 2019-09-19
It would appear one of the key libs here is libmagickcore-6.q16-2
See what trying to upgrade it involves and what would happen if it was removed

---

### Post by Rick St. George on 2019-09-22
Here is what WORKED ...  #1 install 'aptitude'; then 

```

~$ sudo aptitude update
Hit http://deb.opera.com/opera-stable stable InRelease
Hit http://download.virtualbox.org/virtualbox/debian bionic InRelease           
Hit http://us.archive.ubuntu.com/ubuntu bionic InRelease            
Hit http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu bionic InRelease
Hit http://archive.canonical.com/ubuntu bionic InRelease               
Get: 1 http://us.archive.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]  
Hit http://ppa.launchpad.net/rvm/smplayer/ubuntu bionic InRelease               
Get: 2 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Hit http://ppa.launchpad.net/thomas-schiex/blender/ubuntu bionic InRelease      
Fetched 177 kB in 2s (77.7 kB/s)
                                         
~$ sudo aptitude upgrade
Resolving dependencies...                
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
~$ sudo aptitude dist-upgrade
The following NEW packages will be installed:
  imagemagick-6-common{ab} libllvm6.0{a} libmagickcore-6.q16-3{a} 
  libmagickcore-6.q16-3-extra{a} libmagickwand-6.q16-3{a} 
  libopenimageio1.8{a} libopenshadinglanguage1.9{a} 
The following packages will be REMOVED:
  gdal-data{u} libaec0{u} libarmadillo8{u} libarpack2{u} libblosc1{u} 
  libboost-iostreams1.58.0{u} libboost-locale1.58.0{u} 
  libboost-system1.58.0{u} libboost-thread1.58.0{u} libcharls1{u} 
  libdap25{u} libdapclient6v5{u} libepsilon1{u} libfreexl1{u} libfyba0{u} 
  libgdal20{u} libgdcm2.8{u} libgeos-3.6.2{u} libgeos-c1v5{u} 
  libgeotiff2{u} libhdf4-0-alt{u} libhdf5-100{u} libjemalloc1{u} 
  libkmlbase1{u} libkmldom1{u} libkmlengine1{u} libllvm4.0{u} 
  liblog4cplus-1.1-9{u} libminizip1{u} libmysqlclient20{u} libnetcdf13{u} 
  libogdi3.2{u} libopencv-core3.2{u} libopencv-imgcodecs3.2{u} 
  libopencv-imgproc3.2{u} libopencv-videoio3.2{u} libopenimageio1.7{u} 
  libopenshadinglanguage1.8{u} libopenvdb3.1{u} libpq5{u} libproj12{u} 
  libqhull7{u} libsocket++1{u} libspatialite7{u} libsuperlu5{u} libsz2{u} 
  liburiparser1{u} libxerces-c3.2{u} proj-bin{u} proj-data{u} 
The following packages will be upgraded:
  blender{b} imagemagick imagemagick-6.q16 
3 packages upgraded, 7 newly installed, 50 to remove and 0 not upgraded.
Need to get 72.3 MB of archives. After unpacking 58.6 MB will be freed.
The following packages have unmet dependencies:
 blender : Depends: libavdevice57 (>= 7:3.4.6) which is a virtual package and is not provided by any available package

           Depends: libopenvdb5.0 which is a virtual package and is not provided by any available package

           Depends: libpython3.7 (>= 3.7.0) which is a virtual package and is not provided by any available package

 imagemagick-6-common : Breaks: imagemagick-common (< 8:6.9.2.10+dfsg-1~) but 8:6.8.9.9-7ubuntu5.14 is installed
                        Breaks: libmagickcore-6.q16-2 (< 8:6.9.6.2+dfsg-3~) but 8:6.8.9.9-7ubuntu5.14 is installed
The following actions will resolve these dependencies:

     Remove the following packages:                       
1)     blender [2.79.b~1521727842-0thomas~xenial0 (now)]  
2)     gem-plugin-magick [1:0.93.3-9build1 (now)]         
3)     imagemagick-common [8:6.8.9.9-7ubuntu5.14 (now)]   
4)     libmagick++-6.q16-5v5 [8:6.8.9.9-7ubuntu5.14 (now)]
5)     libmagickcore-6.q16-2 [8:6.8.9.9-7ubuntu5.14 (now)]
6)     libmagickwand-6.q16-2 [8:6.8.9.9-7ubuntu5.14 (now)]

     Leave the following dependencies unresolved:         
7)     gem recommends gem-plugin-magick | gem-plugin-image
8)     ubuntustudio-video recommends blender              
9)     ubuntustudio-graphics recommends blender           



Accept this solution? [Y/n/q/?] y
The following NEW packages will be installed:
  imagemagick-6-common{a} libmagickcore-6.q16-3{a} 
  libmagickcore-6.q16-3-extra{a} libmagickwand-6.q16-3{a} 
The following packages will be REMOVED:
  blender{a} gdal-data{u} gem-plugin-magick{a} imagemagick-common{a} 
  libaec0{u} libarmadillo8{u} libarpack2{u} libblosc1{u} 
  libboost-iostreams1.58.0{u} libboost-locale1.58.0{u} 
  libboost-system1.58.0{u} libboost-thread1.58.0{u} libboost-wave1.65.1{u} 
  libcharls1{u} libdap25{u} libdapclient6v5{u} libepsilon1{u} libfreexl1{u} 
  libfyba0{u} libgdal20{u} libgdcm2.8{u} libgeos-3.6.2{u} libgeos-c1v5{u} 
  libgeotiff2{u} libglew1.13{u} libhdf4-0-alt{u} libhdf5-100{u} 
  libjemalloc1{u} libkmlbase1{u} libkmldom1{u} libkmlengine1{u} 
  libllvm4.0{u} liblog4cplus-1.1-9{u} libmagick++-6.q16-5v5{a} 
  libmagickcore-6.q16-2{a} libmagickwand-6.q16-2{a} libminizip1{u} 
  libmysqlclient20{u} libnetcdf13{u} libogdi3.2{u} libopencolorio1v5{u} 
  libopencv-core3.2{u} libopencv-imgcodecs3.2{u} libopencv-imgproc3.2{u} 
  libopencv-videoio3.2{u} libopenimageio1.7{u} libopenshadinglanguage1.8{u} 
  libopensubdiv{u} libopenvdb3.1{u} libpq5{u} libproj12{u} libqhull7{u} 
  libsocket++1{u} libspatialite7{u} libspnav0{u} libsuperlu5{u} libsz2{u} 
  libtinyxml2.6.2v5{u} liburiparser1{u} libxerces-c3.2{u} 
  libyaml-cpp0.5v5{u} proj-bin{u} proj-data{u} python3-numpy{u} 
The following packages will be upgraded:
  imagemagick imagemagick-6.q16 
2 packages upgraded, 4 newly installed, 64 to remove and 0 not upgraded.
Need to get 2,469 kB of archives. After unpacking 395 MB will be freed.
Do you want to continue? [Y/n/?] y
Get: 1 http://us.archive.ubuntu.com/ubuntu bionic-security/main amd64 imagemagick amd64 8:6.9.7.4+dfsg-16ubuntu6.7 [14.2 kB]
Get: 2 http://us.archive.ubuntu.com/ubuntu bionic-security/main amd64 imagemagick-6.q16 amd64 8:6.9.7.4+dfsg-16ubuntu6.7 [423 kB]
Get: 3 http://us.archive.ubuntu.com/ubuntu bionic-security/main amd64 imagemagick-6-common all 8:6.9.7.4+dfsg-16ubuntu6.7 [60.3 kB]
Get: 4 http://us.archive.ubuntu.com/ubuntu bionic-security/main amd64 libmagickcore-6.q16-3 amd64 8:6.9.7.4+dfsg-16ubuntu6.7 [1,615 kB]
Get: 5 http://us.archive.ubuntu.com/ubuntu bionic-security/main amd64 libmagickwand-6.q16-3 amd64 8:6.9.7.4+dfsg-16ubuntu6.7 [293 kB]
Get: 6 http://us.archive.ubuntu.com/ubuntu bionic-security/main amd64 libmagickcore-6.q16-3-extra amd64 8:6.9.7.4+dfsg-16ubuntu6.7 [62.4 kB]
Fetched 2,469 kB in 2s (1,060 kB/s)                   
Reading changelogs... Done
(Reading database ... 308968 files and directories currently installed.)
Removing blender (2.79.b~1521727842-0thomas~xenial0) ...
Removing libopenshadinglanguage1.8 (1.8.10-thomas~bionic1) ...
Removing libopenimageio1.7 (1.7.17~dfsg0-1ubuntu2) ...
Removing libopencv-videoio3.2:amd64 (3.2.0+dfsg-4ubuntu0.1) ...
Removing libopencv-imgcodecs3.2:amd64 (3.2.0+dfsg-4ubuntu0.1) ...
Removing libgdal20 (2.2.3+dfsg-2) ...
Removing gdal-data (2.2.3+dfsg-2) ...
Removing gem-plugin-magick (1:0.93.3-9build1) ...
Removing libmagick++-6.q16-5v5:amd64 (8:6.8.9.9-7ubuntu5.14) ...
(Reading database ... 306803 files and directories currently installed.)
Preparing to unpack .../imagemagick_8%3a6.9.7.4+dfsg-16ubuntu6.7_amd64.deb ...
Unpacking imagemagick (8:6.9.7.4+dfsg-16ubuntu6.7) over (8:6.8.9.9-7ubuntu5.14) ...
Preparing to unpack .../imagemagick-6.q16_8%3a6.9.7.4+dfsg-16ubuntu6.7_amd64.deb ...
Unpacking imagemagick-6.q16 (8:6.9.7.4+dfsg-16ubuntu6.7) over (8:6.8.9.9-7ubuntu5.14) ...
(Reading database ... 306786 files and directories currently installed.)
Removing libmagickwand-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.14) ...
Removing libmagickcore-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.14) ...
Removing imagemagick-common (8:6.8.9.9-7ubuntu5.14) ...
Removing libnetcdf13:amd64 (1:4.6.0-2build1) ...
Removing libhdf5-100:amd64 (1.10.0-patch1+docs-4) ...
Removing libsz2:amd64 (0.3.2-2) ...
Removing libaec0:amd64 (0.3.2-2) ...
Removing libarmadillo8 (1:8.400.0+dfsg-2) ...
Removing libarpack2:amd64 (3.5.0+real-2) ...
Removing libopenvdb3.1 (3.1.0-2) ...
Removing libblosc1 (1.14.2+ds1-1) ...
Removing libboost-iostreams1.58.0:amd64 (1.58.0+dfsg-5ubuntu3.1) ...
Removing libboost-locale1.58.0:amd64 (1.58.0+dfsg-5ubuntu3.1) ...
Removing libboost-thread1.58.0:amd64 (1.58.0+dfsg-5ubuntu3.1) ...
Removing libboost-system1.58.0:amd64 (1.58.0+dfsg-5ubuntu3.1) ...
Removing libboost-wave1.65.1:amd64 (1.65.1+dfsg-0ubuntu5) ...
Removing libgdcm2.8:amd64 (2.8.4-1build2) ...
Removing libcharls1:amd64 (1.1.0+dfsg-2) ...
Removing libdapclient6v5:amd64 (3.19.1-2build1) ...
Removing libdap25:amd64 (3.19.1-2build1) ...
Removing libepsilon1:amd64 (0.9.2+dfsg-2) ...
Removing libspatialite7:amd64 (4.3.0a-5build1) ...
Removing libfreexl1:amd64 (1.0.5-1) ...
Removing libfyba0:amd64 (4.1.1-3) ...
Removing libgeos-c1v5:amd64 (3.6.2-1build2) ...
Removing libgeos-3.6.2:amd64 (3.6.2-1build2) ...
Removing libgeotiff2:amd64 (1.4.2-2build1) ...
Removing libopensubdiv (3.3.3-0thomas~xenial1) ...
Removing libglew1.13:amd64 (1.13.0-2) ...
Removing libhdf4-0-alt (4.2.13-2) ...
Removing libjemalloc1 (3.6.0-11) ...
Removing libkmlengine1:amd64 (1.3.0-5) ...
Removing libkmldom1:amd64 (1.3.0-5) ...
Removing libkmlbase1:amd64 (1.3.0-5) ...
Removing libllvm4.0:amd64 (1:4.0.1-10) ...
Removing liblog4cplus-1.1-9 (1.1.2-3.2) ...
Selecting previously unselected package imagemagick-6-common.
(Reading database ... 306287 files and directories currently installed.)
Preparing to unpack .../imagemagick-6-common_8%3a6.9.7.4+dfsg-16ubuntu6.7_all.deb ...
Unpacking imagemagick-6-common (8:6.9.7.4+dfsg-16ubuntu6.7) ...
Selecting previously unselected package libmagickcore-6.q16-3:amd64.
Preparing to unpack .../libmagickcore-6.q16-3_8%3a6.9.7.4+dfsg-16ubuntu6.7_amd64.deb ...
Unpacking libmagickcore-6.q16-3:amd64 (8:6.9.7.4+dfsg-16ubuntu6.7) ...
Selecting previously unselected package libmagickwand-6.q16-3:amd64.
Preparing to unpack .../libmagickwand-6.q16-3_8%3a6.9.7.4+dfsg-16ubuntu6.7_amd64.deb ...
Unpacking libmagickwand-6.q16-3:amd64 (8:6.9.7.4+dfsg-16ubuntu6.7) ...
(Reading database ... 306553 files and directories currently installed.)
Removing libminizip1:amd64 (1.1-8build1) ...
Removing libmysqlclient20:amd64 (5.7.27-0ubuntu0.18.04.1) ...
Removing libogdi3.2 (3.2.0+ds-2) ...
Removing libopencolorio1v5 (1.1.0~dfsg0-1) ...
Removing libopencv-imgproc3.2:amd64 (3.2.0+dfsg-4ubuntu0.1) ...
Removing libopencv-core3.2:amd64 (3.2.0+dfsg-4ubuntu0.1) ...
Removing libpq5:amd64 (10.10-0ubuntu0.18.04.1) ...
Removing proj-bin (4.9.3-2) ...
Removing libproj12:amd64 (4.9.3-2) ...
Removing libqhull7:amd64 (2015.2-4) ...
Removing libsocket++1:amd64 (1.12.13-9) ...
Removing libspnav0 (0.2.3-1) ...
Removing libsuperlu5:amd64 (5.2.1+dfsg1-3) ...
Removing libtinyxml2.6.2v5:amd64 (2.6.2-4) ...
Removing liburiparser1:amd64 (0.8.4-1) ...
Removing libxerces-c3.2:amd64 (3.2.0+debian-2) ...
Removing libyaml-cpp0.5v5:amd64 (0.5.2-4ubuntu1) ...
Removing proj-data (4.9.3-2) ...
Removing python3-numpy (1:1.13.3-2ubuntu1) ...
Selecting previously unselected package libmagickcore-6.q16-3-extra:amd64.
(Reading database ... 306016 files and directories currently installed.)
Preparing to unpack .../libmagickcore-6.q16-3-extra_8%3a6.9.7.4+dfsg-16ubuntu6.7_amd64.deb ...
Unpacking libmagickcore-6.q16-3-extra:amd64 (8:6.9.7.4+dfsg-16ubuntu6.7) ...
Setting up imagemagick-6-common (8:6.9.7.4+dfsg-16ubuntu6.7) ...
Installing new version of config file /etc/ImageMagick-6/delegates.xml ...
Installing new version of config file /etc/ImageMagick-6/policy.xml ...
Setting up libmagickcore-6.q16-3:amd64 (8:6.9.7.4+dfsg-16ubuntu6.7) ...
Setting up libmagickwand-6.q16-3:amd64 (8:6.9.7.4+dfsg-16ubuntu6.7) ...
Setting up imagemagick-6.q16 (8:6.9.7.4+dfsg-16ubuntu6.7) ...
update-alternatives: warning: alternative /usr/bin/compare-im6 (part of link group compare) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/compare is dangling; it will be updated with best choice
update-alternatives: using /usr/bin/compare-im6.q16 to provide /usr/bin/compare (compare) in auto mode
update-alternatives: using /usr/bin/compare-im6.q16 to provide /usr/bin/compare-im6 (compare-im6) in auto mode
update-alternatives: warning: alternative /usr/bin/animate-im6 (part of link group animate) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/animate is dangling; it will be updated with best choice
update-alternatives: using /usr/bin/animate-im6.q16 to provide /usr/bin/animate (animate) in auto mode
update-alternatives: using /usr/bin/animate-im6.q16 to provide /usr/bin/animate-im6 (animate-im6) in auto mode
update-alternatives: warning: alternative /usr/bin/convert-im6 (part of link group convert) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/convert is dangling; it will be updated with best choice
update-alternatives: using /usr/bin/convert-im6.q16 to provide /usr/bin/convert (convert) in auto mode
update-alternatives: using /usr/bin/convert-im6.q16 to provide /usr/bin/convert-im6 (convert-im6) in auto mode
update-alternatives: warning: alternative /usr/bin/composite-im6 (part of link group composite) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/composite is dangling; it will be updated with best choice
update-alternatives: using /usr/bin/composite-im6.q16 to provide /usr/bin/composite (composite) in auto mode
update-alternatives: using /usr/bin/composite-im6.q16 to provide /usr/bin/composite-im6 (composite-im6) in auto mode
update-alternatives: warning: alternative /usr/bin/conjure-im6 (part of link group conjure) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/conjure is dangling; it will be updated with best choice
update-alternatives: using /usr/bin/conjure-im6.q16 to provide /usr/bin/conjure (conjure) in auto mode
update-alternatives: using /usr/bin/conjure-im6.q16 to provide /usr/bin/conjure-im6 (conjure-im6) in auto mode
update-alternatives: warning: alternative /usr/bin/import-im6 (part of link group import) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/import is dangling; it will be updated with best choice
update-alternatives: using /usr/bin/import-im6.q16 to provide /usr/bin/import (import) in auto mode
update-alternatives: using /usr/bin/import-im6.q16 to provide /usr/bin/import-im6 (import-im6) in auto mode
update-alternatives: warning: alternative /usr/bin/identify-im6 (part of link group identify) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/identify is dangling; it will be updated with best choice
update-alternatives: using /usr/bin/identify-im6.q16 to provide /usr/bin/identify (identify) in auto mode
update-alternatives: using /usr/bin/identify-im6.q16 to provide /usr/bin/identify-im6 (identify-im6) in auto mode
update-alternatives: warning: alternative /usr/bin/stream-im6 (part of link group stream) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/stream is dangling; it will be updated with best choice
update-alternatives: using /usr/bin/stream-im6.q16 to provide /usr/bin/stream (stream) in auto mode
update-alternatives: using /usr/bin/stream-im6.q16 to provide /usr/bin/stream-im6 (stream-im6) in auto mode
update-alternatives: warning: alternative /usr/bin/display-im6 (part of link group display) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/display is dangling; it will be updated with best choice
update-alternatives: using /usr/bin/display-im6.q16 to provide /usr/bin/display (display) in auto mode
update-alternatives: using /usr/bin/display-im6.q16 to provide /usr/bin/display-im6 (display-im6) in auto mode
update-alternatives: warning: alternative /usr/bin/montage-im6 (part of link group montage) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/montage is dangling; it will be updated with best choice
update-alternatives: using /usr/bin/montage-im6.q16 to provide /usr/bin/montage (montage) in auto mode
update-alternatives: using /usr/bin/montage-im6.q16 to provide /usr/bin/montage-im6 (montage-im6) in auto mode
update-alternatives: warning: alternative /usr/bin/mogrify-im6 (part of link group mogrify) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/mogrify is dangling; it will be updated with best choice
update-alternatives: using /usr/bin/mogrify-im6.q16 to provide /usr/bin/mogrify (mogrify) in auto mode
update-alternatives: using /usr/bin/mogrify-im6.q16 to provide /usr/bin/mogrify-im6 (mogrify-im6) in auto mode
Setting up libmagickcore-6.q16-3-extra:amd64 (8:6.9.7.4+dfsg-16ubuntu6.7) ...
Setting up imagemagick (8:6.9.7.4+dfsg-16ubuntu6.7) ...
Processing triggers for shared-mime-info (1.9-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for menu (2.1.47ubuntu2) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
                                         
Current status: 0 (-3) upgradable, 5442 (-47) new.


```

So, using aptitude - ran update, then dist-upgrade. That did the trick with the "higher-level" aptitude program. I used dist-upgrade rather than install to allow for aptitude to properly configure and "do its thing"!

Thanks to all, and to all concerned ... Hope this helps!!!

---

### Post by #&amp;thj^% on 2019-09-22
Very Nice! Glad it's sorted now.
The main differences between aptitude and apt-get are: 
[list]
[*]aptitude adds explicit per-package flags, indicating whether a package was automatically installed to satisfy a dependency: you can manipulate those flags (aptitude markauto or aptitude unmarkauto) to change the way aptitude treats the package.

[*]apt-get keeps track of the same information, but will not show it explicitly. apt-mark can be used for manipulating the flags though.
[*]aptitude will offer to remove unused packages each time you remove an installed package, whereas apt-get will only do that if explicitly asked to with apt-get autoremove or specify --auto-remove.
[*]aptitude acts as a single command-line front-end to most of the functionalities in both apt-get and apt-cache. Note: As of 16.04, there is an apt command that includes the most commonly used commands from apt-get and apt-cache and a few extra features.
[*]contrast to apt-cache's "search", aptitude's "search" output also shows the installed/removed/purged status of a package (plus aptitude's own status flags). Also, the "install" output marks which packages are being installed to satisfy a dependency, and which are being removed because unused.
[*]aptitude has a (text-only) interactive UI.[/list]
I still use "apt" a little especially giving advice or suggestions in the forum but,  I usually end up resolving any problems with aptitude, which never seems to encounter the "apt-get's" numerous problems.

---

