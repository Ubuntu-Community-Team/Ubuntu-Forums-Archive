---
title: "Error in upgrading from 7.10 to 8.04"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by v_mallikarjun on 2008-04-25
I was upgrading ubuntu from 7.10 to 8.04 using alternate cd, system restarted due to some power problems 
then there was error so i had to fix it typed "sudo apt-get install -f"

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gappletviewer-4.2 apache2-utils libsigc++-2.0-dev x11proto-xext-dev
  x11proto-kb-dev x11proto-xinerama-dev x11proto-render-dev python-wxglade
  libsqlite0 libxdmcp-dev libdvbpsi4 libxosd2 x11proto-composite-dev
  xtrans-dev libvlc0 x11proto-core-dev apache2.2-common vlc-nox libept0
  x11proto-randr-dev gjdoc x11proto-damage-dev libdbus-1-dev libwxbase2.6-0
  libxapian15 x11proto-input-dev libqt4-sql x11proto-fixes-dev libxau-dev
  python-wxversion libtar python-wxgtk2.8 libebml0 php5-common libmatroska0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  human-theme ubuntu-gdm-themes ubuntu-wallpapers
The following packages will be REMOVED:
  feisty-gdm-themes gutsy-wallpapers
The following NEW packages will be installed:
  ubuntu-gdm-themes ubuntu-wallpapers
The following packages will be upgraded:
  human-theme
1 upgraded, 2 newly installed, 2 to remove and 725 not upgraded.
1 not fully installed or removed.
Need to get 0B/6741kB of archives.
After unpacking 3146kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 203944 files and directories currently installed.)
Preparing to replace human-theme 0.9 (using .../human-theme_0.18_all.deb) ...
Unpacking replacement human-theme ...
dpkg: error processing /var/cache/apt/archives/human-theme_0.18_all.deb (--unpack):
 trying to overwrite `/usr/share/applications/screensavers/ubuntu_theme.desktop', which is also in package gnome-screensaver
Errors were encountered while processing:
 /var/cache/apt/archives/human-theme_0.18_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

please help need to see ubuntu hardy
thanks in advance

---

### Post by aum11 on 2008-04-25
I have had exactly the same error on 2 different machines,

Am waiting on some advice in another thread.

---

### Post by Pumalite on 2008-04-25
You have broken packages. Lets try to fix them. Run:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by aum11 on 2008-04-25
Thanks Pumalite.  I have the same problem.  Can You give me some help please?

This is what I get: 

~$ sudo dpkg --configure -a
[sudo] password for ari:
dpkg: dependency problems prevent configuration of ubuntu-artwork:
 ubuntu-artwork depends on human-theme (>= 0.10); however:
  Version of human-theme on system is 0.9.
 ubuntu-artwork depends on ubuntu-gdm-themes; however:
  Package ubuntu-gdm-themes is not installed.
 ubuntu-artwork depends on ubuntu-wallpapers; however:
  Package ubuntu-wallpapers is not installed.
dpkg: error processing ubuntu-artwork (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-artwork

---

### Post by Pumalite on 2008-04-25
Run the same commands from:
sudo apt-get -f install

---

### Post by aum11 on 2008-04-25
~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  bittornado librte1 libdvbpsi4 libxosd2 libvlc0 vlc-nox libwxbase2.6-0
  libdvdnav4 libiso9660-4 python-wxversion libtar libvcdinfo0 libebml0
  libmatroska0 libsdl-image1.2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  human-theme ubuntu-gdm-themes ubuntu-wallpapers
The following packages will be REMOVED:
  feisty-gdm-themes gutsy-wallpapers
The following NEW packages will be installed:
  ubuntu-gdm-themes ubuntu-wallpapers
The following packages will be upgraded:
  human-theme
1 upgraded, 2 newly installed, 2 to remove and 673 not upgraded.
1 not fully installed or removed.
Need to get 0B/6741kB of archives.
After unpacking 3146kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)'
in the drive '/cdrom/' and press enter


It appears that it will not accept the alt cd, which is what I have downloaded and am using,  Suggestions please?

---

### Post by v_mallikarjun on 2008-04-26
I tried all four
 
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

but no use getting some errors

---

### Post by aum11 on 2008-04-26
I eventually gave up on trying to do the update with the alt cd.  Downloaded the install cd and did a fresh install...perfect...no problems.  However this is largely due to me having a separate Home partition so that no data and settings are lost.

All the best with it.

---

### Post by lenu on 2008-05-06
> **aum11 said:**
> I eventually gave up on trying to do the update with the alt cd.  Downloaded the install cd and did a fresh install...perfect...no problems.  However this is largely due to me having a separate Home partition so that no data and settings are lost.

All the best with it.

i'm in the same situation, except home is not its own partition, so doing a clean install seems a bit risky. any ideas?

---

### Post by Pumalite on 2008-05-06
You can install on top of the old Ubuntu. Don't worry about /swap. Go Manual and pick all the old partitions. You pick /home, but DO NOT FOMAT.

---

### Post by mondomunchies on 2008-05-27
I had the same problem.

Used:

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

But kept getting same errors.

Then ran:

sudo apt-get remove ubuntu-desktop ubuntu-artwork human-theme

(don't worry, removing ubuntu-desktop is okay)
Removed the three packages without trouble.  Then run:

sudo apt-get install ubuntu-desktop ubuntu-artwork human-theme

It should also install a few more packages.  I had 26 upgraded, 61 new install, 6 removed, and 332 not upgraded.

Then try running the four commands:

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

That worked for me.

Good luck.

---

