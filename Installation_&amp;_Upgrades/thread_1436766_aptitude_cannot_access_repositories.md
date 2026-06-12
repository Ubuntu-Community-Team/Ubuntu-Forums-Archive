---
title: "aptitude cannot access repositories"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by st0nes on 2010-03-23
Hi,

I have internet access, but cannot run updates or upgrades--I get the following error when I run sudo apt-get update:-
```
Err http://www.geekconnection.org karmic/ Release.gpg
  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out
Err http://www.geekconnection.org karmic/ Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://www.geekconnection.org ubuntu/ Release.gpg
  Unable to connect to 196.5.234.34 3142:
Err http://www.geekconnection.org ubuntu/ Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ppa.launchpad.net karmic Release.gpg
  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out
Err http://ppa.launchpad.net karmic/main Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic Release.gpg
  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out
Err http://ubuntu.mirror.ac.za karmic/main Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic/universe Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic/restricted Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic/multiverse Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic-security Release.gpg
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic-security/main Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic-security/universe Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic-security/restricted Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic-security/multiverse Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic-updates Release.gpg
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic-updates/main Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic-updates/universe Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic-updates/restricted Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ubuntu.mirror.ac.za karmic-updates/multiverse Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://download.virtualbox.org karmic Release.gpg
  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out
Err http://ftp.saix.net karmic Release.gpg
  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out
Err http://download.virtualbox.org karmic/non-free Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic/main Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic/universe Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic/restricted Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic/multiverse Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-security Release.gpg
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-security/main Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-security/universe Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-security/restricted Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-security/multiverse Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-updates Release.gpg
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-updates/main Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-updates/universe Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-updates/restricted Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.leg.uct.ac.za karmic Release.gpg
  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out
Err http://ftp.leg.uct.ac.za karmic/free Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.leg.uct.ac.za karmic/non-free Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.leg.uct.ac.za karmic Release.gpg
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.leg.uct.ac.za karmic/partner Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-updates/multiverse Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-backports Release.gpg
  Unable to connect to 196.5.234.34 3142:
Err http://packages.medibuntu.org karmic Release.gpg
  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out
Err http://packages.medibuntu.org karmic/free Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://packages.medibuntu.org karmic/non-free Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-backports/main Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-backports/universe Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-backports/restricted Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-backports/multiverse Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-proposed Release.gpg
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-proposed/main Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-proposed/universe Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-proposed/restricted Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Err http://ftp.saix.net karmic-proposed/multiverse Translation-en_ZA
  Unable to connect to 196.5.234.34 3142:
Reading package lists...
W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-security/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-security/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-security/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-updates/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-updates/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-security/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-security/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-security/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-security/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-security/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-updates/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-updates/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-updates/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-updates/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-updates/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-backports/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-backports/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-proposed/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-proposed/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-proposed/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-proposed/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-proposed/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.leg.uct.ac.za/medibuntu/dists/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://ftp.leg.uct.ac.za/medibuntu/dists/karmic/free/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.leg.uct.ac.za/medibuntu/dists/karmic/non-free/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.leg.uct.ac.za/canonical-partner/dists/karmic/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.leg.uct.ac.za/canonical-partner/dists/karmic/partner/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ppa.launchpad.net/kbuel/ppa/ubuntu/dists/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://ppa.launchpad.net/kbuel/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://www.geekconnection.org/remastersys/repository/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://www.geekconnection.org/remastersys/repository/karmic/en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://www.geekconnection.org/remastersys/repository/ubuntu/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://www.geekconnection.org/remastersys/repository/ubuntu/en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/karmic/non-free/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Some index files failed to download, they have been ignored, or old ones used instead.
mark@addy-laptop:~$ 
mark@addy-laptop:~$ sudo apt-get update > $HOME/apt.out
W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-security/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-security/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-security/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-updates/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-updates/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-security/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-security/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-security/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-security/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-security/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-updates/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-updates/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-updates/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-updates/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ubuntu.mirror.ac.za/ubuntu-archive/dists/karmic-updates/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-backports/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-backports/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-proposed/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-proposed/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-proposed/universe/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-proposed/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.saix.net/linux/distributions/ubuntu/dists/karmic-proposed/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.leg.uct.ac.za/medibuntu/dists/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://ftp.leg.uct.ac.za/medibuntu/dists/karmic/free/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.leg.uct.ac.za/medibuntu/dists/karmic/non-free/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.leg.uct.ac.za/canonical-partner/dists/karmic/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ftp.leg.uct.ac.za/canonical-partner/dists/karmic/partner/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://ppa.launchpad.net/kbuel/ppa/ubuntu/dists/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://ppa.launchpad.net/kbuel/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://www.geekconnection.org/remastersys/repository/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://www.geekconnection.org/remastersys/repository/karmic/en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://www.geekconnection.org/remastersys/repository/ubuntu/Release.gpg  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://www.geekconnection.org/remastersys/repository/ubuntu/en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release.gpg  Could not connect to 196.5.234.34:3142 (196.5.234.34), connection timed out

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/karmic/non-free/i18n/Translation-en_ZA.bz2  Unable to connect to 196.5.234.34 3142:

W: Some index files failed to download, they have been ignored, or old ones used instead.
```
I have no idea what this 196.5.234.34 address is--I have searched for any file containing that string and the only one was /var/cache/debconf/config.dat which contained the lines:-```
Name: msttcorefonts/http_proxy
Template: msttcorefonts/http_proxy
Value: http://amciver:5CataClysm@196.5.234.34:3128/
Owners: ttf-mscorefonts-installer
```
Any ideas please?

---

### Post by stlsaint on 2010-03-23
Probably means server is down.

---

### Post by amrypma on 2010-03-23
All the repositories aptitude uses are listed in /etc/apt/sources.list and sometimes additional repositories are listed in separate files in /etc/apt/sources.list.d/

there should be at least one line with 196.5.234.34 in there or a hostname that resolves to that ip address.

This here is my sources.list if you want something to compare yours to.
```
deb http://nl.archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse

deb http://nl.archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse

deb http://nl.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu karmic-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted universe multiverse

#The Onion Router
deb http://deb.torproject.org/torproject.org karmic main

#codecs
deb http://www.debian-multimedia.org stable main

#electric sheep
#deb http://ppa.launchpad.net/flam3/ppa/ubuntu intrepid main
#deb-src http://ppa.launchpad.net/flam3/ppa/ubuntu intrepid main

#arduino programming
deb http://ppa.launchpad.net/arduino-ubuntu-team/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/arduino-ubuntu-team/ppa/ubuntu karmic main

```

---

### Post by st0nes on 2010-03-24
> **amrypma said:**
> All the repositories aptitude uses are listed in /etc/apt/sources.list and sometimes additional repositories are listed in separate files in /etc/apt/sources.list.d/

there should be at least one line with 196.5.234.34 in there or a hostname that resolves to that ip address.
Thanks for your reply, but that isn't it.  None of the URLs in sources.list resolve to that IP. I replaced my sources list with yours and get identical errors, with the same IP.

This is something I can't find in apt setup; how do I fix it?

---

### Post by mkvnmtr on 2010-03-24
You probably need to change the mirror you are using or just wait for your mirror to be back up. It should be a rather straight foward change in software sources.


I just noticed tor in your sources. You are not trying to update with tor enabled are you ?

---

### Post by tkOne on 2010-12-17
I had a similar problem with synaptic. I needed to set up synaptic with the correct proxy settings.
When I checked aptitude, I had the same problem you're having.
I fixed it by following the instructions from this thread:
[http://ubuntuforums.org/showthread.php?t=177926](http://ubuntuforums.org/showthread.php?t=177926)

Hope this helps

---

