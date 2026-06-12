---
title: "Firefox has disappeared"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by Nolwandle on 2010-05-04
Hi

I managed to upgrade from Karmic to Lucid, but then a serious operator error seems to have occured.

It seems that I have uninstalled Firefox but cannot reinstall it. Below is what I get when I try to reinstall.

All assistance greatfully received.

Nolwandle, Cape Town, South Africa


max@max-laptop:~$ firefox -safe-mode
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox
max@max-laptop:~$ sudo apt-get install firefox
[sudo] password for max: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdns46 libgtk1.2-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox-branding
Suggested packages:
  firefox-gnome-support kmozillahelper latex-xft-fonts
The following packages will be REMOVED:
  firefox-mozilla-build
The following NEW packages will be installed:
  firefox firefox-branding
0 upgraded, 2 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/11.1MB of archives.
After this operation, 29.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 216500 files and directories currently installed.)
Removing firefox-mozilla-build ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
  found `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg: error processing firefox-mozilla-build (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 firefox-mozilla-build
E: Sub-process /usr/bin/dpkg returned an error code (1)
max@max-laptop:

---

### Post by Nolwandle on 2010-05-07
To those that have the same problem, I managed to sort it out by running the python script at [Ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_Installer_Script").

Follow the instructions further down on this page:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

"Old ubuntuzilla installer script users note: before installing these packages, run "ubuntuzilla.py -a remove -p packagename". Otherwise installation may fail due to the existence of a local diversion of /usr/bin/ links, placed there by the old ubuntuzilla script."

Good luck, I needed it!

---

