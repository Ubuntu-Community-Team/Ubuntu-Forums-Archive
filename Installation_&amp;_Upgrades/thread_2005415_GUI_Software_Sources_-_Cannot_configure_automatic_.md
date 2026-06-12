---
title: "GUI Software Sources - Cannot configure automatic installation of security updates"
date: 2012-06-17
forum: Installation &amp; Upgrades
---

### Post by damienz on 2012-06-17
Hello,

OS: Ubuntu 12.04 x86_64

In the Update Manager software, when I click on the Settings... button to open the software sources window, I cannot select an option for "When there are security updates" in the Updates tab. In fact the combobox is disabled.

As someone an idea of the problem ?

thanks in advance

Damien

---

### Post by romis on 2012-06-23
I am having the same problem. And the checkbox below it, was blank as well, the one where you set an option of how often to notify when there's a regular update.

I think we're missing a/some packages, but I just cannot figure out which.

---

### Post by damienz on 2012-06-25
Yes, I think the problem is related with a package which is not installed.

I have two Ubuntu 12.04 systems, the first one was installed using the GUI livecd installer and the second one was installed using the text only installer. Only the second system has the problem, I guess, using the text installer, some packages are not installed.

Maybe I can do a comparison between my both systems in order to discover the differences in term of installed packages.

---

### Post by romis on 2012-06-25
> **damienz said:**
> Yes, I think the problem is related with a package which is not installed.

I have two Ubuntu 12.04 systems, the first one was installed using the GUI livecd installer and the second one was installed using the text only installer. Only the second system has the problem, I guess, using the text installer, some packages are not installed.

Maybe I can do a comparison between my both systems in order to discover the differences in term of installed packages.

You absolutely should be able to. You can run a command like **dpkg --get-selections** in a terminal and that will give you a list of installed packages. You can also do it like **dpkg --get-selections > my-installed-packages.txt** and it will send the output to a text file. Run it on both machines.

There's a program called "diff" you can use to compare files, but I'm not too sure how to use it, but a manual comparison may not be too difficult?

---

### Post by tekdo on 2012-06-25
I am having the same problem across a number of desktops,  all running Xubuntu 11.10 (Oneiric).

---

### Post by damienz on 2012-06-26
> **romis said:**
> You absolutely should be able to. You can run a command like **dpkg --get-selections** in a terminal and that will give you a list of installed packages. You can also do it like **dpkg --get-selections > my-installed-packages.txt** and it will send the output to a text file. Run it on both machines.

There's a program called "diff" you can use to compare files, but I'm not too sure how to use it, but a manual comparison may not be too difficult?

Yes, I tried your solution (dpkg + diff), I saw some difference but I cannot found a package which has an influence on that problem.
Maybe, it's a configuration problem...

---

### Post by dino99 on 2012-06-26
synaptic is a better/easier choice

sudo apt-get install synaptic
sudo synpatic

---

### Post by tekdo on 2012-06-27
> **damienz said:**
> Yes, I tried your solution (dpkg + diff), I saw some difference but I cannot found a package which has an influence on that problem.
Maybe, it's a configuration problem...

I found the same thing. I compared "dpkg --get-selections" against different machines. There was no significant differences in installed packages.

I thought it might be an apparmor issue, so I uninstalled apparmor and even rebooted, but still remains.

Its not an arch issue, because I see this on both 32bit and 64bit.

Some more ideas:
- maybe it is something in /etc/apt/apt.conf.d
- something to do with polkit

---

### Post by tekdo on 2012-06-27
Solution: just uninstall unattended-upgrades

Unfortunately, I can't do that, because it brings in all these dependencies that I don't want:
```
The following extra packages will be installed:
  docbook-xsl kate-data katepart kde-runtime kde-runtime-data kdebase-runtime kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdoctools libattica0 libclucene0ldbl libdbusmenu-qt2 libdlrestrictions1 libiodbc2
  libkatepartinterfaces4 libkcmutils4 libkde3support4 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5
  libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4 libkjsembed4
  libkmediaplayer4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4
  libktexteditor4 libmysqlclient16 libnepomuk4 libnepomukquery4a libnepomukutils4 libntrack-qt4-1
  libntrack0 libphonon4 libplasma3 libpolkit-qt-1-1 libqt4-qt3support libqt4-sql-mysql libsolid4
  libsoprano4 libstreamanalyzer0 libstreams0 libthreadweaver4 mysql-common ntrack-module-libnl-0 phonon
  phonon-backend-gstreamer plasma-scriptengine-javascript shared-desktop-ontologies soprano-daemon
Suggested packages:
  docbook-xsl-doc-html docbook-xsl-doc-pdf docbook-xsl-doc-text docbook-xsl-doc libsaxon-java
  docbook-xsl-saxon fop xalan dbtoepub djvulibre-bin hspell libqt4-dev phonon-backend-vlc
  phonon-backend-xine phonon-backend-mplayer
Recommended packages:
  virtuoso-minimal kubuntu-debug-installer icoutils libcanberra-pulse libcanberra-gstreamer
The following packages will be REMOVED
  aptdaemon* apturl* language-selector-gnome* python-aptdaemon* python-aptdaemon-gtk*
  python-aptdaemon.gtk3widgets* python-aptdaemon.gtkwidgets* python-software-properties*
  sessioninstaller* software-center* software-properties-gtk* unattended-upgrades* xubuntu-desktop*
  xul-ext-ubufox* y-ppa-manager*
The following NEW packages will be installed
  docbook-xsl kate-data katepart kde-runtime kde-runtime-data kdebase-runtime kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdoctools libattica0 libclucene0ldbl libdbusmenu-qt2 libdlrestrictions1 libiodbc2
  libkatepartinterfaces4 libkcmutils4 libkde3support4 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5
  libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4 libkjsembed4
  libkmediaplayer4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4
  libktexteditor4 libmysqlclient16 libnepomuk4 libnepomukquery4a libnepomukutils4 libntrack-qt4-1
  libntrack0 libphonon4 libplasma3 libpolkit-qt-1-1 libqt4-qt3support libqt4-sql-mysql libsolid4
  libsoprano4 libstreamanalyzer0 libstreams0 libthreadweaver4 mysql-common ntrack-module-libnl-0 phonon
  phonon-backend-gstreamer plasma-scriptengine-javascript shared-desktop-ontologies soprano-daemon
0 upgraded, 61 newly installed, 15 to remove and 0 not upgraded.
Need to get 26.8 MB of archives.
After this operation, 116 MB of additional disk space will be used.

```Does anyone know how to uninstall it without bringing in all these dependencies?

In the meantime, there is a workaround: edit this file **/etc/apt/apt.conf.d/20auto-upgrades** and comment out its contents. It should look like this after you are done:
```
//APT::Periodic::Update-Package-Lists "1";
//APT::Periodic::Download-Upgradeable-Packages "0";
//APT::Periodic::AutocleanInterval "0";
//APT::Periodic::Unattended-Upgrade "1";
```

You can follow bug report here:
[https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1018367](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1018367)

---

### Post by damienz on 2012-07-02
> **dino99 said:**
> synaptic is a better/easier choice

sudo apt-get install synaptic
sudo synpatic

I totally agree with you. But this doesn't fix the problem.

---

### Post by damienz on 2012-07-02
> **tekdo said:**
> Solution: just uninstall unattended-upgrades

Unfortunately, I can't do that, because it brings in all these dependencies that I don't want:
```
The following extra packages will be installed:
  docbook-xsl kate-data katepart kde-runtime kde-runtime-data kdebase-runtime kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdoctools libattica0 libclucene0ldbl libdbusmenu-qt2 libdlrestrictions1 libiodbc2
  libkatepartinterfaces4 libkcmutils4 libkde3support4 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5
  libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4 libkjsembed4
  libkmediaplayer4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4
  libktexteditor4 libmysqlclient16 libnepomuk4 libnepomukquery4a libnepomukutils4 libntrack-qt4-1
  libntrack0 libphonon4 libplasma3 libpolkit-qt-1-1 libqt4-qt3support libqt4-sql-mysql libsolid4
  libsoprano4 libstreamanalyzer0 libstreams0 libthreadweaver4 mysql-common ntrack-module-libnl-0 phonon
  phonon-backend-gstreamer plasma-scriptengine-javascript shared-desktop-ontologies soprano-daemon
Suggested packages:
  docbook-xsl-doc-html docbook-xsl-doc-pdf docbook-xsl-doc-text docbook-xsl-doc libsaxon-java
  docbook-xsl-saxon fop xalan dbtoepub djvulibre-bin hspell libqt4-dev phonon-backend-vlc
  phonon-backend-xine phonon-backend-mplayer
Recommended packages:
  virtuoso-minimal kubuntu-debug-installer icoutils libcanberra-pulse libcanberra-gstreamer
The following packages will be REMOVED
  aptdaemon* apturl* language-selector-gnome* python-aptdaemon* python-aptdaemon-gtk*
  python-aptdaemon.gtk3widgets* python-aptdaemon.gtkwidgets* python-software-properties*
  sessioninstaller* software-center* software-properties-gtk* unattended-upgrades* xubuntu-desktop*
  xul-ext-ubufox* y-ppa-manager*
The following NEW packages will be installed
  docbook-xsl kate-data katepart kde-runtime kde-runtime-data kdebase-runtime kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdoctools libattica0 libclucene0ldbl libdbusmenu-qt2 libdlrestrictions1 libiodbc2
  libkatepartinterfaces4 libkcmutils4 libkde3support4 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5
  libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4 libkjsembed4
  libkmediaplayer4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4
  libktexteditor4 libmysqlclient16 libnepomuk4 libnepomukquery4a libnepomukutils4 libntrack-qt4-1
  libntrack0 libphonon4 libplasma3 libpolkit-qt-1-1 libqt4-qt3support libqt4-sql-mysql libsolid4
  libsoprano4 libstreamanalyzer0 libstreams0 libthreadweaver4 mysql-common ntrack-module-libnl-0 phonon
  phonon-backend-gstreamer plasma-scriptengine-javascript shared-desktop-ontologies soprano-daemon
0 upgraded, 61 newly installed, 15 to remove and 0 not upgraded.
Need to get 26.8 MB of archives.
After this operation, 116 MB of additional disk space will be used.

```Does anyone know how to uninstall it without bringing in all these dependencies?

In the meantime, there is a workaround: edit this file **/etc/apt/apt.conf.d/20auto-upgrades** and comment out its contents. It should look like this after you are done:
```
//APT::Periodic::Update-Package-Lists "1";
//APT::Periodic::Download-Upgradeable-Packages "0";
//APT::Periodic::AutocleanInterval "0";
//APT::Periodic::Unattended-Upgrade "1";
```

You can follow bug report here:
[https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1018367](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1018367)

Thanks for your solution. By reading your post and by reading the bug report on launchpad, I understand the problem...

In my case (maybe you have the same situation), in Ubuntu installation where I have the problem, I noticed an additional file (20auto-upgrades) in /etc/apt/apt.conf.d, however in Ubuntu installation where I don't have the problem, this specific file doesn't exist. To fix the problem, I just had to remove this file. I discover that this file is present only if you install the system in text mode.

---

