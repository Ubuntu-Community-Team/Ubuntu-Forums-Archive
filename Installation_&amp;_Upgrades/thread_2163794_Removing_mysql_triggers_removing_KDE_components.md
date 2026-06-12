---
title: "Removing mysql triggers removing KDE components"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by dwlamb on 2013-07-19
I want to remove mysql from system to start over.  If I enter ```


sudo apt-get remove --purge mysql-server mysql-client mysql-common
``` in terminal, I get the following: ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-client is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libterm-readkey-perl php5-gd libmcrypt4 libt1-5 php5-mcrypt dbconfig-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  accountsservice language-selector-common libaccountsservice0 libqt4-dbus libqt4-declarative libqt4-declarative-gestures libqt4-designer
  libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-test
  libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 python-apport qdbus
Suggested packages:
  gnome-control-center libqt4-declarative-folderlistmodel libqt4-declarative-particles libqt4-declarative-shaders qt4-qmlviewer libqt4-dev
  qt4-qtconfig
The following packages will be REMOVED:
  akonadi-backend-mysql* akonadi-server* akregator* amarok* apport-kde* apturl-kde* jockey-kde* kaddressbook* kde-config-touchpad* kde-workspace*
  kde-workspace-bin* kdepim-kresources* kdepim-runtime* kdepim-strigi-plugins* kmail* knotes* kontact* kopete* kopete-message-indicator*
  korganizer* ktimetracker* kubuntu-desktop* language-selector-kde* libcalendarsupport4* libdbd-mysql-perl* libeventviews4* libincidenceeditorsng4*
  libkdepim4* libkdepimdbusinterfaces4* libkopete4* libksieveui4* libmailcommon4* libmessagecomposer4* libmessagecore4* libmessagelist4*
  libmessageviewer4* libmuonprivate1* libmysqlclient18* libqt4-sql-mysql* libtemplateparser4* muon* muon-installer* muon-notifier* muon-updater*
  mysql-client-5.5* mysql-common* mysql-server* mysql-server-5.5* php5-mysql* phpmyadmin* plasma-dataengines-workspace* plasma-desktop*
  plasma-netbook* plasma-scriptengine-python* plasma-widget-facebook* plasma-widgets-addons* plasma-widgets-workspace* printer-applet* python-kde4*
  software-properties-kde* system-config-printer-kde* update-manager-kde* usb-creator-kde* userconfig*
The following NEW packages will be installed:
  libqt4-declarative-gestures
The following packages will be upgraded:
  accountsservice language-selector-common libaccountsservice0 libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network
  libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtgui4 python-apport qdbus
22 upgraded, 1 newly installed, 64 to remove and 179 not upgraded.
Need to get 15.9 MB/16.3 MB of archives.
After this operation, 224 MB disk space will be freed.
Do you want to continue [Y/n]?
```

There is a lot of items in there I don't think should go as they are important to KDE and the plasma desktop.  Is there a better and less wide sweep of the broom method?

---

### Post by dwlamb on 2013-08-01
Nudge.  Does anyone have a response?

---

