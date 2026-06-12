---
title: "Best methods for package installation/removal"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by Arla on 2010-05-16
Was thinking about this, and wondering how others deal with this.

For testing a program, how do you deal with the uninstallation of the packages that something installed, you install, say DigiKam, it installs a ton of extra stuff because it's KDE vs Gnome, later you decide you don't really like DigiKam (or prefer something else) how do you uninstall both DigiKam and all the extra stuff that was installed with it?

Second, for actual testing of development (and this MAY be more suited to the Maverick forum) how do you install all the programs that you normally use quickly and easily? Clone your current install and start fresh? Personally I want to see all the changes to the default install, so I like doing a fresh install, but then how to make sure you also install all the programs that you actually use on a normal basis, or do you just spend the hours to go through all the installs?

---

### Post by mistichu on 2010-05-16
apt-get remove nameofprogramhere
apt-get install nameofprogramhere
apt-cache search programyouwanttofind
apt-get update
apt-get autoremove -removes unused (undependent packages)
only five commands you need
hope that helps

just write a script for it its not hard
btw only programs that you really absolutely need at the beginning of a fresh install (in case of breaks or lockouts)
nano or vi (personally nano is easier) aircrack-ng(in case you lose your routers password)

nano and vi provide a way to read and edit text(conf files in case of break) from the terminal in case you screw up and accidentally delete xorg.conf or put in a bad conf file in its place .

aircrack-ng is good if you lock yourself out of your router constantly(i have short term memory loss so unless i make a hook(something that you say or think to help remember something) then i forget it easily)

---

