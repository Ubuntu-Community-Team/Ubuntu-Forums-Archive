---
title: "unable to down load updates"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by keefy49 on 2012-12-01
Using 12.04 with no problem but updates now not downloading!
Can anyone help

Keefy

---

### Post by ibjsb4 on 2012-12-01
Hi keefty49, welcome to the forum  :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

And please post the output.

---

### Post by The_Cougar_Kid on 2012-12-02
I am having exactly the same problem on my wife's PC (Ubuntu 12.04).  Update manager says there are 20 updates to install but when we try to install them it fails with this message:

installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0: 
 field name `../libindicator-messages-status-provider1/changelog.Debian.gz' must be followed by colon 
localepurge: Disk space freed in /usr/share/locale: 0 KiB 
localepurge: Disk space freed in /usr/share/man: 0 KiB 
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB 
localepurge: Disk space freed in /usr/share/omf: 0 KiB 
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB 
 
Total disk space freed by localepurge: 0 KiB 
 
localepurge: Disk space freed in /usr/share/locale: 0 KiB 
localepurge: Disk space freed in /usr/share/man: 0 KiB 
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB 
localepurge: Disk space freed in /usr/share/omf: 0 KiB 
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB 
 
Total disk space freed by localepurge: 0 KiB 
 
localepurge: Disk space freed in /usr/share/locale: 0 KiB 
localepurge: Disk space freed in /usr/share/man: 0 KiB 
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB 
localepurge: Disk space freed in /usr/share/omf: 0 KiB 
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB 
 
Total disk space freed by localepurge: 0 KiB 
 
localepurge: Disk space freed in /usr/share/locale: 0 KiB 
localepurge: Disk space freed in /usr/share/man: 0 KiB 
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB 
localepurge: Disk space freed in /usr/share/omf: 0 KiB 
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB 
 
Total disk space freed by localepurge: 0 KiB

I ran the command you suggested to keefty49 and this was the output:

[sudo] password for dorothy: 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security InRelease
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe Translation-en
Reading package lists... Done




Any ideas please?

---

