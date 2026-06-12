---
title: "Error during 8.04 upgrade"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by ncumming on 2008-05-04
This morning I decided to updgrade from 7.10 (ubuntu studio version) to 8.04 using the update manager.  Partway through the upgrade, i got several error messages - one saying nautilus crashed and had to close, another saying the upgrade failed and the system may be in an "unstable" state.   I tried restarting and updating again.  Now, the update manager says that it can only do a partial update due to a previous update failing, and when try to run the partial update it crashes again.

Everything else seems to be working OK (I'm posting from the machine right now), but I seem to be stuck somewhere between 7.10 and 8.04.  Any suggestions?

---

### Post by red_smeg on 2008-05-04
I tried the same upgrade and I now get HAL! error which won't allow me to see the network anymore.

What can I do to recover my system..

---

### Post by ncumming on 2008-05-04
update....i tried downloading the alt install cd and upgrading that way and same results.  also tried using apt-get...no luck there either...

---

### Post by ncumming on 2008-05-04
ok...making some progress now.  definately past the point of no return.  i tried upgrading in safe mode.  ran apt-get update then apt-get upgrade.  Upgrade ran for several minutes, then hung up trying to install the desktop theme.  I was able to exit out to the desktop...which seems to be more or less functional (internet connection and many apps including firefox work) but the desktop is completely white (no background) and most icons are missing.  upgrade manager does not work.  running sudo apt-get upgrade from the terminal i get:

The following packages will be upgraded:
  human-theme
1 upgraded, 0 newly installed, 0 to remove and 423 not upgraded.
621 not fully installed or removed.
Need to get 0B/33.7kB of archives.
After unpacking 111kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 135400 files and directories currently installed.)
Preparing to replace human-theme 0.9 (using .../human-theme_0.18_all.deb) ...
Unpacking replacement human-theme ...
dpkg: error processing /var/cache/apt/archives/human-theme_0.18_all.deb (--unpack):
 trying to overwrite `/usr/share/applications/screensavers/ubuntu_theme.desktop', which is also in package gnome-screensaver
Errors were encountered while processing:
 /var/cache/apt/archives/human-theme_0.18_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
nick@officemachine:~$

---

### Post by red_smeg on 2008-05-08
Here's what I did to sort out the mess.

1. opened up my apple and downloaded / burn't the CD.
2. ran the live CD
3. Repartitioned the hard disk to create a new instance. (kept the old one)
4. Ran the install of 8.04
5. Ran RPM to get mysql, php and apache back
6. Copied my webserver content over from the original partition.
7. Copied my sites-available config file over to get my vhosts back
8. downloaded mysql administrator and restored the back-up

Results.

1. system working but now cannot access the hard drive without running sudo terminal
2. phpbb still not working I think needs re-install due to mysql permissions failure
3. all other webcontent (html) working ok.

Opinion.

It sucks that this sort of upgrade should cause such issues for something so trivial as a LAMP installation and that the only way I could get my system back was to effectively start again.

Question.

Does anyone know a short cut to getting my phpbb running again ?

---

