---
title: "Sources problem"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by QwUo173Hy on 2007-06-28
I recently installed the 3v1n0-sources-list package and was informed that updated were available. However, I can't install many of them now.

When I run the update manager, I get the error;

```
Not all updates can be installed

Run a partial upgrade, to install as many updates as possible.
```

This error dialog actually has a button on it to run a "Partial Upgrade", but when I choose this, I get the message;

```
Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.
```

Anyone know how I can fix this besides just putting back my old sources.list?

---

### Post by bapoumba on 2007-06-28
Hello,
what package were you willing to install?
Could you post the specific lines from your sources.list for this repo (or the whole file)?

---

### Post by QwUo173Hy on 2007-06-28
Hi bapoumba,

The packages are;

```
gaim
libtotem-plparser
pidgin
pidgin-data
totem
totem-mozilla
totem-xine
```

I've attached my sources.list because I don't know which lines are relevant.

---

### Post by bapoumba on 2007-06-28
All the packages you've specified are in the ubuntu repos. Do you need different versions from the standard ones?
Please paste the sources.list in here (in [code] tags, the # symbol when you answer a post), I do not see the attached file (or I may be already too sleepy).

Someone may take over this, as it is quite late in here. I'll see your answers tomorrow.

---

### Post by QwUo173Hy on 2007-06-28
Hi Bapoumba,

You're right, I didn't attach the file that time - sorry. It's quite late here too :)

thanks,
Jarlath

```

# Treviño's Ubuntu Feisty Fawn Sources list
# http://3v1n0.tuxfamily.org/blog/?page_id=13
#
# Repository List based on standard feisty with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
#  gpg --keyserver subkeys.pgp.net --recv KEY
#  gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
#  wget URL --quiet -O - | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
#  sudo apt-key add FILE
#
# In the repository list page there's also a script that can do this
# work automatically, this is suggested only if you know what you're doing

# Ubuntu supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://archive.ubuntu.com/ubuntu feisty-security main restricted
deb http://archive.ubuntu.com/ubuntu feisty-proposed main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-proposed main restricted

# Ubuntu community supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-security universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-proposed universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-security universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-proposed universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)
deb http://mi.mirror.garr.it/ubuntu feisty-backports main restricted universe multiverse
deb-src http://mi.mirror.garr.it/ubuntu feisty-backports main restricted universe multiverse

# CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
# RealPlayer10, Opera, VmWare Server and more to come.)
deb http://archive.canonical.com/ubuntu feisty-commercial main

# UbuntuStudio Repository (GPG key: B6A4EB33)
# GPG key-file: http://archive.ubuntustudio.org/ubuntustudio.gpg
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb-src http://archive.ubuntustudio.org/ubuntustudio feisty main

## kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-357 feisty main
deb-src http://kubuntu.org/packages/kde-357 feisty main
#deb http://kubuntu.org/packages/kde-latest feisty main
#deb-src http://kubuntu.org/packages/kde-latest feisty main

## kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
#deb http://kubuntu.org/packages/koffice-latest feisty main
#deb-src http://kubuntu.org/packages/koffice-latest feisty main

## kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
#deb http://kubuntu.org/packages/amarok-latest feisty main
#deb-src http://kubuntu.org/packages/amarok-latest feisty main

# kubuntu.org packages for KDE4 alpha-1 (GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde4-3.90.1 feisty main
deb-src http://kubuntu.org/packages/kde4-3.90.1 feisty main

# Bleeding edge wine packages (GPG key: 387EE263)
# GPG key-file: http://wine.budgetdedicated.com/apt/387EE263.gpg
deb http://wine.budgetdedicated.com/apt feisty main
deb-src http://wine.budgetdedicated.com/apt feisty main

# Seveas' packages (GPG key: 1135D466)
# GPG key-file: http://mirror.ubuntulinux.nl/1135D466.gpg
deb http://mirror.ubuntulinux.nl feisty-seveas all
deb-src http://mirror.ubuntulinux.nl feisty-seveas all

# The Opera browser (packages) (GPG key: 6A423791)
deb http://deb.opera.com/opera etch non-free

# Google picasa packages (GPG key: 7FAC5991)
deb http://dl.google.com/linux/deb/ stable non-free

# Medibuntu (Multimedia, Entertainment & Distraction In Ubuntu - ex Penguin Liberation Front)
# GPG key-file: http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

# The repository from Kubuntu Germany
# GPG key-file: http://archive.czessi.net/ubuntu/kczessi.gpg
deb http://archive.czessi.net/ubuntu feisty main restricted universe multiverse preview
deb-src http://archive.czessi.net/ubuntu feisty main restricted universe multiverse preview

# Achim's Unofficial 'feisty' Kubuntu packages
# GPG key-file: http://www.mpe.mpg.de/~ach/ach-gpg.asc
deb http://www.mpe.mpg.de/~ach/kubuntu/feisty ./
deb-src http://www.mpe.mpg.de/~ach/kubuntu/feisty ./

# Ubuntu feisty University Klagenfurt packages
# GPG key-file: http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub
# $ sudo apt-key add uniklu-debuild.pub 
#   uniklu:         backports and new packages
#   uniklu-intern:  not freely redistributable (jvm), or modified packages
#   uniklu-testing: packages not ready for general use
deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu
deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu-intern
deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu-testing
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu-intern
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu-testing

# MEPIS improvements, overrides and updates (distro based on kubuntu)
#deb http://apt.mepis.org/mepis32-6.5/ mepis main
#deb http://apt.mepis.org/simply32-6.0/ mepis main

# Ekiga and Debian pkg-voip
deb http://pkg-voip.buildserver.net/ubuntu feisty main

# MythTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
deb http://home.eng.iastate.edu/~superm1 feisty all
deb-src http://home.eng.iastate.edu/~superm1 feisty all

# Official Beryl Ubuntu Packages (GPG key: 1609B551)
# GPG key-file: http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main

# Ubuntu repository for Screenlets (GPG key: F854AFD7)
# GPG key-file: http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
deb-src http://hendrik.kaju.pri.ee/ubuntu feisty screenlets

# Subpixel Font rendering packages (GPG key: 937215FF)
# Improved fonts on LCDs - WARNING: May violate some patents
# GPG key-file: http://www.telemail.fi/mlind/ubuntu/937215FF.gpg
deb http://www.telemail.fi/mlind/ubuntu feisty fonts main
deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts main

## Others mlind experimental misc Packages (GPG key: 937215FF)
## GPG key-file: http://www.telemail.fi/mlind/ubuntu/937215FF.gpg
#deb http://www.telemail.fi/mlind/ubuntu feisty experimental
#deb-src http://www.telemail.fi/mlind/ubuntu feisty experimental

# Skype packages
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Geole's Ubuntu Repository
# GPG key-file: http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg
deb http://ubuntu.geole.info/ feisty universe multiverse
deb-src http://ubuntu.geole.info/ feisty universe multiverse
deb http://ubuntu.geole.info/ feisty-backports main universe multiverse restricted
deb-src http://ubuntu.geole.info/ feisty-backports main universe multiverse restricted

# Linux2Go Ubuntu Packages (GPG key: E8BDA4E3)
deb http://www.linux2go.dk/ubuntu feisty main
deb-src http://www.linux2go.dk/ubuntu feisty main

# Asher256's Repository
deb http://asher256-repository.tuxfamily.org edgy main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

# Tvfreeplayer Packages (GPG key: )
# GPG key-file: http://www.tvfreeplayer.com/linux/falcon/tvfreeplayer.gpg
deb http://www.tvfreeplayer.com/linux/falcon feisty all
deb-src http://www.tvfreeplayer.com/linux/falcon feisty all

# gnomemeeting - ekiga (GPG key: 52ABFCB1)
deb http://snapshots.ekiga.net/ubuntu/ feisty main
deb-src http://snapshots.ekiga.net/ubuntu/ feisty main

## lprod packages: many audio/video apps: avidemux, cinelerra...
#deb http://lprod.org/deb/feisty/ ./
#deb-src http://lprod.org/deb/feisty/ ./

# Cinelerra Feisty packages
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/ ./

## Spring Packages (RTS game)
#deb ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /
#deb-src ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /

# Cafuego's feisty Stuff: Broadcom firmware, google-earth, secondlife (GPG key: 969F3F57)...
deb http://au.ubuntu.cafuego.net feisty-cafuego all
deb-src http://au.ubuntu.cafuego.net feisty-cafuego all

# Debuntu Ubuntu feisty packages
# GPG Key: http://repository.debuntu.org/GPG-Key-chantra.txt
deb http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse

## BMPx feisty Repository
## GPG key-file: http://files.beep-media-player.org/packages/bmp-packages.pubkey
#deb http://files.beep-media-player.org/packages/ubuntu feisty main testing
#deb-src http://files.beep-media-player.org/packages/ubuntu feisty main testing

# Morgoth Repository (GPG key: 7E2E4741)
# Provides Monkey's Audio, xmms pugins, vlc plugins, gqview, audacius, audacity...
# GPG key-file: http://morgoth.free.fr/files/morgoth-signkey.gpg.asc
deb http://morgoth.free.fr/ubuntu feisty-backports main
deb-src http://morgoth.free.fr/ubuntu feisty-backports main

## ATi & nVidia drivers Ubuntu packages
## GPG key: http://albertomilone.com/drivers/tseliot.asc
#deb http://www.albertomilone.com/drivers/feisty/latest/32bit binary/

# Automatix repository (GPG key: E23C5FC3)
deb http://www.getautomatix.com/apt feisty main

# edevelop - e17 (Enlightenment DR 17)
# GPG key: http://lut1n.ifrance.com/repo_key.asc
deb http://edevelop.org/pkg-e/ubuntu feisty e17
deb-src http://edevelop.org/pkg-e/ubuntu feisty e17
#deb http://e17.dunnewind.net/ubuntu feisty e17
#deb-src http://e17.dunnewind.net/ubuntu feisty e17

# Musicbrainz Repository
# GPG key-file: http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/public.key
deb http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu feisty musicbrainz
deb-src http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu feisty musicbrainz

## Imbrandons software repository (GPG key: 887D9FD2)
## GPG key-file: http://www.imbrandon.com/packages/887D9FD2.gpg
#deb http://www.imbrandon.com/packages feisty all
#deb-src http://www.imbrandon.com/packages feisty all

## Candyz's Ubuntu Packages
## GPG key-file: http://cle.linux.org.tw/candyz/Ubuntu/candyz.key
#deb http://cle.linux.org.tw/candyz/Ubuntu/feisty i386/

# The Ubuntu NLP Repository (GPG key: 8ABD1965)
# GPG key-file: http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg
deb http://cl.naist.jp/~eric-n/ubuntu-nlp feisty all
deb-src http://cl.naist.jp/~eric-n/ubuntu-nlp feisty all

# Ubuntu System Administrator packages (GPG key: 2F306651)
# GPG key-file: http://ubuntu.moshen.de/2F306651.gpg
deb http://ubuntu.moshen.de feisty multimedia misc
deb-src http://ubuntu.moshen.de feisty multimedia misc

## Michael Biebl Tracker Repository (GPG key: BD058554)
## GPG Key-file: http://www.teco.edu/~biebl/biebl.asc
#deb http://debs.michaelbiebl.de/ feisty main
#deb-src http://debs.michaelbiebl.de/ feisty main

# The Consciousness Repository (GPG key: DD385D79)
# GPG key-file: http://debs.peadrop.com/DD385D79.gpg
deb http://debs.peadrop.com feisty all
deb-src http://debs.peadrop.com feisty all

## Tolero Ubuntu Repository
#deb http://ubuntu.tolero.org/ feisty main
#deb-src http://ubuntu.tolero.org/ feisty main

# IVTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
# GPG key-file: http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg
deb http://dl.ivtvdriver.org/ubuntu feisty all
deb-src http://dl.ivtvdriver.org/ubuntu feisty all

# syzygy42 repository: avant-window-navigator, exaile, closure... (GPG key: 8434D43A)
# GPG key-file: http://download.tuxfamily.org/syzygy42/8434D43A.gpg
deb http://download.tuxfamily.org/syzygy42/ feisty all
deb-src http://download.tuxfamily.org/syzygy42/ feisty all

## Firefox 3.0 alpha builds for feisty (unstable)
#deb http://gnomefreak.youmortals.com/mozilla-testing feisty main
#deb-src http://gnomefreak.youmortals.com/mozilla-testing feisty main

## Swiftfox (enhanced Firefox for linux) packages
deb http://getswiftfox.com/builds/debian unstable non-free

# Sonnes repository (aMule AdunanZa, Audacious)
deb http://adurepo.altervista.org/ubuntu feisty all
deb-src http://adurepo.altervista.org/ubuntu feisty all

# darkmagez repository: rhythmbox and newer gtk (GPG key: A3012FB3)
# GPG key-file: http://mirror.randumb.org/darkmagez/repo/A3012FB3.gpg
deb http://mirror.randumb.org/darkmagez/repo feisty-darkmagez multimedia-experimental #core-experimental
deb-src http://mirror.randumb.org/darkmagez/repo feisty-darkmagez multimedia-experimental #core-experimental

## Raof Repository: newer versions of Compiz, beagle, mono, scribus... (GPG key: 2F306651)
## GPG key-file: http://raof.dyndns.org/falcon/2F306651.gpg
##deb http://raof.dyndns.org/falcon feisty all
#deb-src http://raof.dyndns.org/falcon feisty all

# FoLKeN 'Repozytorium' (GPG key: 6FB65A0F)
#deb http://deb.svx.pl/ feisty main universe bleeding
#deb-src http://deb.svx.pl/ feisty main universe bleeding

# Le dépomaniak repository (GPG key: 1D59E694)
# GPG key-file: http://ubuntu.davromaniak.eu/1D59E694.gpg
deb http://ubuntu.davromaniak.eu feisty-depomaniak all
deb-src http://ubuntu.davromaniak.eu feisty-depomaniak all

# Mez's Repository (GPG key: 6AAAA569)
# GPG key-file: http://apt.sourceguru.net/6AAAA569.gpg
deb http://apt.sourceguru.net feisty all
deb-src http://apt.sourceguru.net feisty all

# Ryan Kavanagh's packages (GPG key: 02544D0E)
# GPG key-file: http://packages.ryanak.ca/02544D0E.gpg
deb http://packages.ryanak.ca ryan-feisty all
deb-src http://packages.ryanak.ca ryan-feisty all

# OpenedHand Debian/Ubuntu Packages
deb http://debian.o-hand.com feisty/
deb-src http://debian.o-hand.com feisty/

# OpenSync svn ubuntu repository (GPG key: B029CB84)
deb http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main
deb-src http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main

# Iuculano's debian packages (GPG key: AE3BE9AA)
# GPG key-file: http://ubuntu.iuculano.it/AE3BE9AA.gpg
deb http://ubuntu.iuculano.it feisty amsn thunderbird #ck-kernel #all
deb-src http://ubuntu.iuculano.it feisty amsn thunderbird #ck-kernel #all

# Elisa Debian Packages
deb http://elisa.fluendo.com/packages feisty main

# PollyCooke, il repository :)
deb http://download.tuxfamily.org/pollyrepo feisty/

# Treviño's Ubuntu Feisty Fawn Repository (GPG key: 81836EBF - DD800CD9)
# Many "random" bleeding edge software: aMule, aMSN, Mercury, flash...
# Further informations and complete packages list: http://3v1n0.tuxfamily.org
deb http://download.tuxfamily.org/3v1deb feisty 3v1n0
deb-src http://download.tuxfamily.org/3v1deb feisty 3v1n0

# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, compiz and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs...
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

## Treviño's Ubuntu Suspend2 patched kernels Repository (GPG key: 81836EBF - DD800CD9)
## Ubuntu kernels patched with Suspend2 plus other related tools www.suspend2.net
## Warning: they will replace standard ubuntu kernel related packages
#deb http://download.tuxfamily.org/3v1deb feisty suspend2
#deb-src http://download.tuxfamily.org/3v1deb feisty suspend2
```

---

### Post by bapoumba on 2007-06-28
Thats an extensive source.list ;)
If you do not mind, I'll look into it tomorrow, or someone else will do it in the mean time.

My first question remains: do you need specific versions of these packages that are not in standard ubuntu repos?

My guess is that you updated with the repos enabled, and if some packages are at different versions form ubuntu, its giving you errors.
If everything was fine before you add the Treviño's repos, try to comment them out. I also see edgy repos for Asher and the mepis ones, I'll have to look into. I know mepis is based on ubuntu, but it also can give you errors.

Good night :)

---

### Post by QwUo173Hy on 2007-06-28
Bapoumba, tomorrow is fine - thank you so much for your time.

The only applications I needed was the newer GIMP 2.3, Beryl, and Skype 1.4. I didn't realize my OS was being mongrelized :)

Talk tomorrow.
Jarlath

---

### Post by bapoumba on 2007-06-29
You're welcome.

Gimp2.3 is in the gutsy repos, not the feisty ones. Did not look from which repos you tried to install it from. So which one is it? Do you need that Gimp version for some particular reason?
Skype and Beryl have their own repo.

You should for sure comment out the Asher repos that are for edgy.
Looks I cannot browse the debian repos for swiftfox.
The feisty-proposed repos are designed to test out pakages before they make it to the official repos.

What I would do, to start, is comment everything but feisty main restricted universe multiverse (including backports and proposed) and run 
```
sudo aptitude update
```
to see what errors are there.

To comment the repos, add a # at the beginning of the line.
First make a copy of the file, just in case:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak
```
Then edit the file
```
sudo nano /etc/apt/sources.list
```
nano is a small text editor working from the command line.
CTRL-O to save the file, CTRL-X to exit nano. Run the update after you comment the repos.

---

### Post by QwUo173Hy on 2007-06-29
Thanks - I did as you said and ran the command. There were no errors and the prompt asking me to upgrade no longer appears.

Thanks for your help bapoumba. I don't think I'll blindly add repos to my sources again :)

---

### Post by bapoumba on 2007-06-29
You're wecome :)
My sources.list is : main restricted universe multiverse, and I got a couple codecs from medibuntu, but I commented the repos after. I check from time to time if there are new packages there.

---

