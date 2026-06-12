---
title: "Upgrade 13.04 -&gt; 13.10 hangs at &quot;Installed cups-common&quot;"
date: 2013-11-11
forum: Installation &amp; Upgrades
---

### Post by tiggerntatie on 2013-11-11
I have been performing distribution upgrades twice a year for the past 8 years with few issues, but this upgrade (-> 13.10) has failed in exactly the same way on all three machines that I have running 13.04 (First on a Macbook Pro, then on an dual core Intel desktop, and now on an Atom desktop).

The upgrade tool is on the "Installing the upgrades" section, when it becomes unresponsive (gray). At the time this happens, the status line reads: "Installed cups-common". 

On the last two upgrades I killed the tool and attempted a reboot, which failed (can't recall the exact problem, but at that point I just did a clean install).

Today, my third upgrade is failing in the exact same way and I simply don't have the desire to do yet another install of 13.10 from scratch. Is there some way to recover from this hanged condition that will not necessitate a complete reinstall from scratch?

---

### Post by bapoumba on 2013-11-11
Please post your sources.list and the results to :
```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by tiggerntatie on 2013-11-11
I could get the sources.list, but I could not run apt-get while the upgrade tool was running (lock file). I killed that (perhaps a mistake) but still can't run apt-get. And the desktop has gotten wonky (launcher icons disappearing, alt-tab list not appearing, etc.). 

Tried to rm the lock file and run again, but was informed to use dpkg --configure -a before continuing.

Did that.. then it stopped after a long time with "too many errors to continue".

At this point working on the machine has become more challenging since my VNC connection has broken and can't be restored (the machine is a print server in a closet).

Anyway.. sources.list:

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ saucy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy universe
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu saucy-security main restricted
deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
deb http://security.ubuntu.com/ubuntu saucy-security universe
deb-src http://security.ubuntu.com/ubuntu saucy-security universe
deb http://security.ubuntu.com/ubuntu saucy-security multiverse
deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu saucy main
deb-src http://extras.ubuntu.com/ubuntu saucy main
```

---

### Post by bapoumba on 2013-11-11
Okay, please do not shut down or reboot. If the upgrade was interrupted, it needs to be finished or fixed.

Run the upgrade and paste the output here, even if it is very long.

---

### Post by tiggerntatie on 2013-11-11
```
Ign http://us.archive.ubuntu.com saucy InRelease
Ign http://security.ubuntu.com saucy-security InRelease
Ign http://extras.ubuntu.com saucy InRelease
Ign http://us.archive.ubuntu.com saucy-updates InRelease
Hit http://security.ubuntu.com saucy-security Release.gpg
Hit http://extras.ubuntu.com saucy Release.gpg
Ign http://us.archive.ubuntu.com saucy-backports InRelease
Hit http://security.ubuntu.com saucy-security Release
Hit http://extras.ubuntu.com saucy Release
Hit http://us.archive.ubuntu.com saucy Release.gpg
Hit http://security.ubuntu.com saucy-security/main Sources
Hit http://us.archive.ubuntu.com saucy-updates Release.gpg
Hit http://extras.ubuntu.com saucy/main Sources
Hit http://security.ubuntu.com saucy-security/restricted Sources
Hit http://security.ubuntu.com saucy-security/universe Sources
Hit http://extras.ubuntu.com saucy/main i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports Release.gpg
Hit http://security.ubuntu.com saucy-security/multiverse Sources
Hit http://us.archive.ubuntu.com saucy Release
Hit http://security.ubuntu.com saucy-security/main i386 Packages
Hit http://us.archive.ubuntu.com saucy-updates Release
Hit http://security.ubuntu.com saucy-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports Release
Hit http://security.ubuntu.com saucy-security/universe i386 Packages
Hit http://us.archive.ubuntu.com saucy/main Sources
Hit http://security.ubuntu.com saucy-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com saucy/restricted Sources
Hit http://us.archive.ubuntu.com saucy/universe Sources
Hit http://security.ubuntu.com saucy-security/main Translation-en
Hit http://us.archive.ubuntu.com saucy/multiverse Sources
Hit http://us.archive.ubuntu.com saucy/main i386 Packages
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com saucy/restricted i386 Packages
Ign http://extras.ubuntu.com saucy/main Translation-en_US
Hit http://us.archive.ubuntu.com saucy/universe i386 Packages
Hit http://us.archive.ubuntu.com saucy/multiverse i386 Packages
Ign http://extras.ubuntu.com saucy/main Translation-en
Hit http://security.ubuntu.com saucy-security/restricted Translation-en
Hit http://us.archive.ubuntu.com saucy/main Translation-en
Hit http://security.ubuntu.com saucy-security/universe Translation-en
Hit http://us.archive.ubuntu.com saucy/multiverse Translation-en
Hit http://us.archive.ubuntu.com saucy/restricted Translation-en
Hit http://us.archive.ubuntu.com saucy/universe Translation-en
Hit http://us.archive.ubuntu.com saucy-updates/main Sources
Hit http://us.archive.ubuntu.com saucy-updates/restricted Sources
Hit http://us.archive.ubuntu.com saucy-updates/universe Sources
Hit http://us.archive.ubuntu.com saucy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com saucy-updates/main i386 Packages
Ign http://security.ubuntu.com saucy-security/main Translation-en_US
Hit http://us.archive.ubuntu.com saucy-updates/restricted i386 Packages
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com saucy-updates/universe i386 Packages
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com saucy-updates/multiverse i386 Packages
Ign http://security.ubuntu.com saucy-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com saucy-updates/main Translation-en
Hit http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com saucy-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com saucy-updates/universe Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/main Sources
Hit http://us.archive.ubuntu.com saucy-backports/restricted Sources
Hit http://us.archive.ubuntu.com saucy-backports/universe Sources
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Sources
Hit http://us.archive.ubuntu.com saucy-backports/main i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/main Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/universe Translation-en
Ign http://us.archive.ubuntu.com saucy/main Translation-en_US
Ign http://us.archive.ubuntu.com saucy/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com saucy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com saucy/universe Translation-en_US
Ign http://us.archive.ubuntu.com saucy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com saucy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com saucy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/universe Translation-en_US
Reading package lists...
```

and..

```
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
91 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Setting up libpam-systemd:i386 (204-0ubuntu19) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libpam-systemd:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.6.5-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ntfs-3g (1:2013.1.13AR.1-2ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ntfs-3g (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up popularity-contest (1.57ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing popularity-contest (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libavutil-extra-51:i386 (6:0.8.9ubuntu0.13.10.1) ...
Setting up libavcodec-extra-53:i386 (6:0.8.9ubuntu0.13.10.1) ...
Setting up libavformat53:i386 (6:0.8.9-0ubuntu0.13.10.1) ...
Setting up libpam-gnome-keyring:i386 (3.8.2-0ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libpam-gnome-keyring:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libpostproc52:i386 (6:0.8.9-0ubuntu0.13.10.1) ...
Setting up libswscale2:i386 (6:0.8.9-0ubuntu0.13.10.1) ...
Setting up lightdm (1.8.4-0ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing lightdm (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up isc-dhcp-client (4.2.4-7ubuntu8) ...
^[OAdebconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing isc-dhcp-client (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of policykit-1:
 policykit-1 depends on libpam-systemd; however:
  Package libpam-systemd:i386 is not configured yet.

dpkg: error processing policykit-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on isc-dhcp-client (>= 4.1.1-P1-4); however:
  Package isc-dhcp-client is not configured yet.
 network-manager depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (2:3.6.18-1ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.

dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
Setting up unattended-upgrades (0.79.3ubuntu8) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing unattended-upgrades (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on unattended-upgrades; however:
  Package unattended-upgrades is not configured yet.

dpkg: error processing python3-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3-software-properties (= 0.92.28); however:
  Package python3-software-properties is not configured yet.

dpkg: error processing software-properties-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3-software-properties (= 0.92.28); however:
  Package python3-software-properties is not configured yet.
 software-properties-gtk depends on software-properties-common; however:
  Package software-properties-common is not configured yet.

dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.

dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on samba-common (>= 3.0.27a); however:
  Package samba-common is not configured yet.
 nautilus-share depends on samba-common-bin | samba-common (<< 2:3.4.0~pre2-1~0); however:
  Package samba-common-bin is not configured yet.
  Version of samba-common on system is 2:3.6.18-1ubuntu3.
 nautilus-share depends on apturl; however:
  Package apturl is not configured yet.

dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.6.18-1ubuntu3); however:
  Package samba-common is not configured yet.

dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Setting up less (458-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing less (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up rsyslog (5.8.11-2ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on isc-dhcp-client; however:
  Package isc-dhcp-client is not configured yet.
 ubuntu-minimal depends on less; however:
  Package less is not configured yet.
 ubuntu-minimal depends on rsyslog; however:
  Package rsyslog is not configured yet.

dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Setting up apparmor (2.8.0-0ubuntu31) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing apparmor (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up irqbalance (1.0.6-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing irqbalance (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up memtest86+ (4.20-1.1ubuntu5) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on man-db; however:
  Package man-db is not configured yet.
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
 ubuntu-standard depends on popularity-contest; however:
  Package popularity-contest is not configured yet.

dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up ufw (0.33-0ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ufw (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of checkbox:
 checkbox depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing checkbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox-qt:
 checkbox-qt depends on checkbox (>= 0.16.7); however:
  Package checkbox is not configured yet.

dpkg: error processing checkbox-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of colord:
 colord depends on policykit-1 (>= 0.103); however:
  Package policykit-1 is not configured yet.

dpkg: error processing colord (--configure):
 dependency problems - leaving unconfigured
Setting up cups (1.7.0~rc1-0ubuntu5) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of printer-driver-hpcups:
 printer-driver-hpcups depends on cups (>= 1.4.0) | cupsddk; however:
  Package cups is not configured yet.
  Package cupsddk is not installed.
 printer-driver-hpcups depends on cups; however:
  Package cups is not configured yet.

dpkg: error processing printer-driver-hpcups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on printer-driver-hpcups (= 3.13.9-1); however:
  Package printer-driver-hpcups is not configured yet.
 hplip depends on cups (>= 1.1.20); however:
  Package cups is not configured yet.
 hplip depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on hplip (>= 3.13.9-1); however:
  Package hplip is not configured yet.

dpkg: error processing printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
Setting up dictionaries-common (1.20.2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up flashplugin-installer (11.2.202.310ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-system-log:
 gnome-system-log depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing gnome-system-log (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on man-db (>= 2.5.1-1); however:
  Package man-db is not configured yet.

dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on yelp (>= 3); however:
  Package yelp is not configured yet.

dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (2.00-19ubuntu2.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hyphen-en-us:
 hyphen-en-us depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.

dpkg: error processing hyphen-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-common:
 jockey-common depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing jockey-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.

dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of landscape-client-ui-install:
 landscape-client-ui-install depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing landscape-client-ui-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-gnome:
 language-selector-gnome depends on aptdaemon (>= 0.40+bzr527); however:
  Package aptdaemon is not configured yet.

dpkg: error processing language-selector-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lintian:
 lintian depends on man-db; however:
  Package man-db is not configured yet.

dpkg: error processing lintian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of myspell-en-au:
 myspell-en-au depends on dictionaries-common (>= 1.0); however:
  Package dictionaries-common is not configured yet.

dpkg: error processing myspell-en-au (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.9.8); however:
  Package network-manager is not configured yet.

dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-hyphenation:
 openoffice.org-hyphenation depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.

dpkg: error processing openoffice.org-hyphenation (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-gutenprint:
 printer-driver-gutenprint depends on cups (>= 1.3.0); however:
  Package cups is not configured yet.

dpkg: error processing printer-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio:
 pulseaudio depends on libpam-systemd; however:
  Package libpam-systemd:i386 is not configured yet.

dpkg: error processing pulseaudio (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic

Processing triggers for libc-bin ...
Errors were encountered while processing:
 libpam-systemd:i386
 man-db
 ntfs-3g
 popularity-contest
 libpam-gnome-keyring:i386
 lightdm
 isc-dhcp-client
 policykit-1
 network-manager
 samba-common
 samba-common-bin
 unattended-upgrades
 python3-software-properties
 software-properties-common
 software-properties-gtk
 apturl
 nautilus-share
 smbclient
 less
 rsyslog
 ubuntu-minimal
 apparmor
 irqbalance
 memtest86+
 ubuntu-standard
 ufw
 checkbox
 checkbox-qt
 colord
 cups
 printer-driver-hpcups
 hplip
 printer-driver-postscript-hp
 dictionaries-common
 flashplugin-installer
 gnome-system-log
 yelp
 gnome-user-guide
 grub-pc
 hyphen-en-us
 jockey-common
 jockey-gtk
 landscape-client-ui-install
 aptdaemon
 language-selector-gnome
 lintian
 myspell-en-au
 network-manager-gnome
 openoffice.org-hyphenation
 printer-driver-gutenprint
 pulseaudio
Processing was halted because there were too many errors.
```

---

### Post by bapoumba on 2013-11-11
Do you have some ppa enabled ? If so, please disable/purge them for now.

Then try :
```
sudo apt-get update
sudo apt-get -f install
```

Edit : sorry, does not seem you have any active ppa. Please run the above commands.

---

### Post by tiggerntatie on 2013-11-11
```
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  g++-4.7 libaccounts-qt1 libcamel-1.2-40 libcolumbus0-0 libcolumbus0-0-common
  libdns95 libgc1c3 libgnome-desktop-3-4 libgweather-3-1 libisc92 libllvm3.2
  libmenu-cache2 libobrender27 libobt0 libqjson0 libsignon-qt1
  libstdc++6-4.7-dev linux-headers-3.8.0-25 linux-headers-3.8.0-25-generic
  linux-image-3.8.0-25-generic linux-image-extra-3.8.0-25-generic
  python3-virtkey ttf-dejavu-extra
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
86 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up libpam-systemd:i386 (204-0ubuntu19) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libpam-systemd:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.6.5-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ntfs-3g (1:2013.1.13AR.1-2ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ntfs-3g (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up popularity-contest (1.57ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing popularity-contest (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libpam-gnome-keyring:i386 (3.8.2-0ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libpam-gnome-keyring:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lightdm (1.8.4-0ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing lightdm (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up isc-dhcp-client (4.2.4-7ubuntu8) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing isc-dhcp-client (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of policykit-1:
 policykit-1 depends on libpam-systemd; however:
  Package libpam-systemd:i386 is not configured yet.

dpkg: error processing policykit-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on isc-dhcp-client (>= 4.1.1-P1-4); however:
  Package isc-dhcp-client is not configured yet.
 network-manager depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (2:3.6.18-1ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.

dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
Setting up unattended-upgrades (0.79.3ubuntu8) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing unattended-upgrades (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on unattended-upgrades; however:
  Package unattended-upgrades is not configured yet.

dpkg: error processing python3-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3-software-properties (= 0.92.28); however:
  Package python3-software-properties is not configured yet.

dpkg: error processing software-properties-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3-software-properties (= 0.92.28); however:
  Package python3-software-properties is not configured yet.
 software-properties-gtk depends on software-properties-common; however:
  Package software-properties-common is not configured yet.

dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.

dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on samba-common (>= 3.0.27a); however:
  Package samba-common is not configured yet.
 nautilus-share depends on samba-common-bin | samba-common (<< 2:3.4.0~pre2-1~0); however:
  Package samba-common-bin is not configured yet.
  Version of samba-common on system is 2:3.6.18-1ubuntu3.
 nautilus-share depends on apturl; however:
  Package apturl is not configured yet.

dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.6.18-1ubuntu3); however:
  Package samba-common is not configured yet.

dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Setting up less (458-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing less (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up rsyslog (5.8.11-2ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on isc-dhcp-client; however:
  Package isc-dhcp-client is not configured yet.
 ubuntu-minimal depends on less; however:
  Package less is not configured yet.
 ubuntu-minimal depends on rsyslog; however:
  Package rsyslog is not configured yet.

dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Setting up apparmor (2.8.0-0ubuntu31) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing apparmor (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up irqbalance (1.0.6-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing irqbalance (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up memtest86+ (4.20-1.1ubuntu5) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on man-db; however:
  Package man-db is not configured yet.
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
 ubuntu-standard depends on popularity-contest; however:
  Package popularity-contest is not configured yet.

dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up ufw (0.33-0ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ufw (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of checkbox:
 checkbox depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing checkbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox-qt:
 checkbox-qt depends on checkbox (>= 0.16.7); however:
  Package checkbox is not configured yet.

dpkg: error processing checkbox-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of colord:
 colord depends on policykit-1 (>= 0.103); however:
  Package policykit-1 is not configured yet.

dpkg: error processing colord (--configure):
 dependency problems - leaving unconfigured
Setting up cups (1.7.0~rc1-0ubuntu5) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of printer-driver-hpcups:
 printer-driver-hpcups depends on cups (>= 1.4.0) | cupsddk; however:
  Package cups is not configured yet.
  Package cupsddk is not installed.
 printer-driver-hpcups depends on cups; however:
  Package cups is not configured yet.

dpkg: error processing printer-driver-hpcups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on printer-driver-hpcups (= 3.13.9-1); however:
  Package printer-driver-hpcups is not configured yet.
 hplip depends on cups (>= 1.1.20); however:
  Package cups is not configured yet.
 hplip depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on hplip (>= 3.13.9-1); however:
  Package hplip is not configured yet.

dpkg: error processing printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
Setting up dictionaries-common (1.20.2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up flashplugin-installer (11.2.202.310ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-system-log:
 gnome-system-log depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing gnome-system-log (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on man-db (>= 2.5.1-1); however:
  Package man-db is not configured yet.

dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on yelp (>= 3); however:
  Package yelp is not configured yet.

dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (2.00-19ubuntu2.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hyphen-en-us:
 hyphen-en-us depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.

dpkg: error processing hyphen-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-common:
 jockey-common depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing jockey-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.

dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of landscape-client-ui-install:
 landscape-client-ui-install depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing landscape-client-ui-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-gnome:
 language-selector-gnome depends on aptdaemon (>= 0.40+bzr527); however:
  Package aptdaemon is not configured yet.

dpkg: error processing language-selector-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lintian:
 lintian depends on man-db; however:
  Package man-db is not configured yet.

dpkg: error processing lintian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of myspell-en-au:
 myspell-en-au depends on dictionaries-common (>= 1.0); however:
  Package dictionaries-common is not configured yet.

dpkg: error processing myspell-en-au (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.9.8); however:
  Package network-manager is not configured yet.

dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-hyphenation:
 openoffice.org-hyphenation depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.

dpkg: error processing openoffice.org-hyphenation (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-gutenprint:
 printer-driver-gutenprint depends on cups (>= 1.3.0); however:
  Package cups is not configured yet.

dpkg: error processing printer-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio:
 pulseaudio depends on libpam-systemd; however:
  Package libpam-systemd:i386 is not configured yet.

dpkg: error processing pulseaudio (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic
Errors were encountered while processing:
 libpam-systemd:i386
 man-db
 ntfs-3g
 popularity-contest
 libpam-gnome-keyring:i386
 lightdm
 isc-dhcp-client
 policykit-1
 network-manager
 samba-common
 samba-common-bin
 unattended-upgrades
 python3-software-properties
 software-properties-common
 software-properties-gtk
 apturl
 nautilus-share
 smbclient
 less
 rsyslog
 ubuntu-minimal
 apparmor
 irqbalance
 memtest86+
 ubuntu-standard
 ufw
 checkbox
 checkbox-qt
 colord
 cups
 printer-driver-hpcups
 hplip
 printer-driver-postscript-hp
 dictionaries-common
 flashplugin-installer
 gnome-system-log
 yelp
 gnome-user-guide
 grub-pc
 hyphen-en-us
 jockey-common
 jockey-gtk
 landscape-client-ui-install
 aptdaemon
 language-selector-gnome
 lintian
 myspell-en-au
 network-manager-gnome
 openoffice.org-hyphenation
 printer-driver-gutenprint
 pulseaudio
Processing was halted because there were too many errors.
```

---

### Post by bapoumba on 2013-11-12
Hmm, please try
```
sudo dpkg --configure -a
```

---

### Post by tiggerntatie on 2013-11-13
```
Setting up sane-utils (1.0.23-0ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing sane-utils (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up memtest86+ (4.20-1.1ubuntu5) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.6.5-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on man-db; however:
  Package man-db is not configured yet.
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.

dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up ntfs-3g (1:2013.1.13AR.1-2ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ntfs-3g (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libpam-systemd:i386 (204-0ubuntu19) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libpam-systemd:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libpam-gnome-keyring:i386 (3.8.2-0ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libpam-gnome-keyring:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up dictionaries-common (1.20.2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up flashplugin-installer (11.2.202.310ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lintian:
 lintian depends on man-db; however:
  Package man-db is not configured yet.

dpkg: error processing lintian (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (2:3.6.18-1ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up unattended-upgrades (0.79.3ubuntu8) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing unattended-upgrades (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.6.18-1ubuntu3); however:
  Package samba-common is not configured yet.

dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on man-db (>= 2.5.1-1); however:
  Package man-db is not configured yet.

dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
Setting up ufw (0.33-0ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ufw (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of unity-scope-manpages:
 unity-scope-manpages depends on man-db; however:
  Package man-db is not configured yet.

dpkg: error processing unity-scope-manpages (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (2.00-19ubuntu2.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on libpam-systemd; however:
  Package libpam-systemd:i386 is not configured yet.
 ubuntu-desktop depends on yelp; however:
  Package yelp is not configured yet.

dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-hyphenation:
 openoffice.org-hyphenation depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.

dpkg: error processing openoffice.org-hyphenation (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.

dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
Setting up irqbalance (1.0.6-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing irqbalance (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lightdm (1.8.4-0ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing lightdm (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on yelp; however:
  Package yelp is not configured yet.

dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on unattended-upgrades; however:
  Package unattended-upgrades is not configured yet.

dpkg: error processing python3-software-properties (--configure):
 dependency problems - leaving unconfigured
Setting up popularity-contest (1.57ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing popularity-contest (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up apparmor (2.8.0-0ubuntu31) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing apparmor (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up rsyslog (5.8.11-2ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of pulseaudio:
 pulseaudio depends on libpam-systemd; however:
  Package libpam-systemd:i386 is not configured yet.

dpkg: error processing pulseaudio (--configure):
 dependency problems - leaving unconfigured
Setting up isc-dhcp-client (4.2.4-7ubuntu8) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing isc-dhcp-client (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up less (458-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing less (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of policykit-1:
 policykit-1 depends on libpam-systemd; however:
  Package libpam-systemd:i386 is not configured yet.

dpkg: error processing policykit-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3-software-properties (= 0.92.28); however:
  Package python3-software-properties is not configured yet.

dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up cups (1.7.0~rc1-0ubuntu5) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of pulseaudio-module-bluetooth:
 pulseaudio-module-bluetooth depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing pulseaudio-module-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-module-x11:
 pulseaudio-module-x11 depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing pulseaudio-module-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on yelp (>= 3); however:
  Package yelp is not configured yet.

dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of myspell-en-au:
 myspell-en-au depends on dictionaries-common (>= 1.0); however:
  Package dictionaries-common is not configured yet.

dpkg: error processing myspell-en-au (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.

dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on samba-common (>= 3.0.27a); however:
  Package samba-common is not configured yet.
 nautilus-share depends on samba-common-bin | samba-common (<< 2:3.4.0~pre2-1~0); however:
  Package samba-common-bin is not configured yet.
  Version of samba-common on system is 2:3.6.18-1ubuntu3.
 nautilus-share depends on apturl; however:
  Package apturl is not configured yet.

dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of colord:
 colord depends on policykit-1 (>= 0.103); however:
  Package policykit-1 is not configured yet.

dpkg: error processing colord (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-common:
 jockey-common depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing jockey-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-log:
 gnome-system-log depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing gnome-system-log (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-hpcups:
 printer-driver-hpcups depends on cups (>= 1.4.0) | cupsddk; however:
  Package cups is not configured yet.
  Package cupsddk is not installed.
 printer-driver-hpcups depends on cups; however:
  Package cups is not configured yet.

dpkg: error processing printer-driver-hpcups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-software-properties:
 python-software-properties depends on unattended-upgrades; however:
  Package unattended-upgrades is not configured yet.

dpkg: error processing python-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hyphen-en-us:
 hyphen-en-us depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.

dpkg: error processing hyphen-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-module-gconf:
 pulseaudio-module-gconf depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing pulseaudio-module-gconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of landscape-client-ui-install:
 landscape-client-ui-install depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing landscape-client-ui-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox:
 checkbox depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing checkbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-sound:
 indicator-sound depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing indicator-sound (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on policykit-1; however:
  Package policykit-1 is not configured yet.

dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic
Errors were encountered while processing:
 sane-utils
 memtest86+
 man-db
 ubuntu-standard
 ntfs-3g
 libpam-systemd:i386
 libpam-gnome-keyring:i386
 dictionaries-common
 flashplugin-installer
 lintian
 samba-common
 unattended-upgrades
 smbclient
 yelp
 ufw
 unity-scope-manpages
 grub-pc
 ubuntu-desktop
 openoffice.org-hyphenation
 samba-common-bin
 irqbalance
 lightdm
 ubuntu-docs
 python3-software-properties
 popularity-contest
 apparmor
 rsyslog
 pulseaudio
 isc-dhcp-client
 less
 policykit-1
 software-properties-gtk
 cups
 pulseaudio-module-bluetooth
 pulseaudio-module-x11
 gnome-user-guide
 myspell-en-au
 apturl
 nautilus-share
 colord
 jockey-common
 gnome-system-log
 printer-driver-hpcups
 python-software-properties
 hyphen-en-us
 pulseaudio-module-gconf
 software-center
 landscape-client-ui-install
 checkbox
 indicator-sound
 update-notifier
Processing was halted because there were too many errors.
```

Followed this with
```
lsof /var/cache/debconf/config.dat
```

then...

```
sudo killall frontend
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

```

Reboot and everything fine again.

---

