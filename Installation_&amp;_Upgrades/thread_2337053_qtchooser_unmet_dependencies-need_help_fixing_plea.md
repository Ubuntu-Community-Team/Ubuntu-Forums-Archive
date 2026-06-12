---
title: "qtchooser unmet dependencies-need help fixing please"
date: 2016-09-14
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2016-09-14
OK. . .well. . .I never have stated that I am smart. . .so now I need the brilliance of you brilliant Forum Members. . .

I mistakenly attempted an install of the latest qt5-default version (the 16.10 build) on Lubuntu 16.04. Bad move.

As soon as I installed the dependency qtchooser. . .I got unmet dependencies. . . if I run apt get -f install or any variant thereof. . .it messes up my entire installation. . .basically wanting to uninstall programs that has qt5 as a dependency, including all of qt4 and the installed qt5-default. . .I cannot uninstall qtchooser at all without messing up my entire installation either. . .just the installation of that one file has messed up everything. . .libqt5core5a and libqtcore4 won't install. . .or uninstall either. . . without taking everything else with it. . .it's a mess. . .

Is there any way out of this without having to do a complete reinstall? Why did the installation of that one file create such havoc? And why can't I uninstall qtchooser without taking 60MB of important Files and Programs with it?

The following packages have unmet dependencies:
 qtchooser : Breaks: libqt5core5a (< 5.5.1+dfsg-17~) but 5.5.1+dfsg-16ubuntu7.1 is to be installed
             Breaks: libqtcore4 (< 4:4.8.7+dfsg-7~) but 4:4.8.7+dfsg-5ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by mc4man on 2016-09-14
If you only tried installing that one package (qtchooser) then try downloading the 16.04 package & using dpkg on, 
sudo dpkg -i /path/to/the.deb
[https://launchpad.net/ubuntu/+source/qtchooser/52-gae5eeef-2build1~gcc5.2](https://launchpad.net/ubuntu/+source/qtchooser/52-gae5eeef-2build1~gcc5.2)
(- pick your arch from Builds section

---

### Post by roler2 on 2016-09-15
Thank you for your suggestion. Unfortunately, the only way out was to do exactly what apt install -f directed me to do. Once that was completed, then I just reinstalled all of the humongous amount of files that were uninstalled. In turn, that uninstalled the offending qtchooser file. A lot of work over one file.

---

