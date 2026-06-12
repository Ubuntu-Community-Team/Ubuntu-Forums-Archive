---
title: "Broken release upgrade 20.04 to 22.04 has not resolveable unanttended upgrades"
date: 2022-11-11
forum: Installation &amp; Upgrades
---

### Post by franknfurter2 on 2022-11-11
Hello, 

some days ago I did do-release-upgrade on a rock pi running a little  nextcloud server for me. I started the upgrade while I was logged in at  the hardware itself, not over network. While the upgrade was fetching and unzipping the packages, the monitor  went black and there was no way to open the screen again.
 I was still  able to get via ssh into the server and found out, that the console was  waiting for the user to enter "OK". As you will now, there was no way to  do so.


 So I killed the upgrade process and started again. I had to fix some  problems (don't ask me what it was) and started the upgrade again. It  worked and after a while it seems, that it's on 22.04 now. lsb_release  tells so.
 
But since then there is a list of 53 updates, that will not be installed. Here they are:

 Die folgenden Pakete sind zurückgehalten worden: bogofilter bogofilter-bdb bogofilter-common fwupd gcc-10-base  guile-2.2-libs inkscape libfwupd2 libfwupdplugin5 libgslcblas0  libqt5concurrent5 libqt5core5a libqt5dbus5 libqt5designer5 libqt5designercomponents5 libqt5gui5 libqt5help5 libqt5network5  libqt5opengl5 libqt5opengl5-dev libqt5positioning5 libqt5printsupport5  libqt5qml5 libqt5quick5 libqt5quickparticles5 libqt5quickshapes5 libqt5quicktest5 libqt5quickwidgets5 libqt5sensors5 libqt5sql5  libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5webchannel5 libqt5webkit5  libqt5widgets5 libqt5xml5 mariadb-server python-six python3-chardet qdoc-qt5 qhelpgenerator-qt5 qt5-assistant qt5-gtk-platformtheme  qt5-qmake qt5-qmake-bin qt5-qmltooling-plugins qtattributionsscanner-qt5  qtbase5-dev qtbase5-dev-tools qtdeclarative5-dev qtdeclarative5-dev-tools qttools5-dev-tools 0 aktualisiert, 0 neu installiert, 0 zu entfernen und 53 nicht  aktualisiert.


 /var/log/unattended-upgrades/unattended-upgrades.log tells on all  packages something like that: 2022-11-11 06:36:18,009 INFO Paket qttools5-dev-tools wird  zurückgehalten, weil ein verwandtes Paket zurückgehalten wird oder  aufgrund lokaler apt_preferences(5).


 At the beginning the log says: 2022-11-11 06:33:35,048 INFO Erlaubte Ursprünge sind: o=Ubuntu,a=jammy,  o=Ubuntu,a=jammy-security, o=UbuntuESMApps,a=jammy-apps-security,  o=UbuntuESM,a=jammy-infra-se curity
 Problem is, that nextcloud wont run. Within its log it shows problems  in connecting the database (mariadb) and because mariadb-server is  unattended, I guess that this is the problem.

sudo apt install -f or sudo dpkg --configure -a dows not do anything.



 Hot do I have to fix this?


 Regards

---

