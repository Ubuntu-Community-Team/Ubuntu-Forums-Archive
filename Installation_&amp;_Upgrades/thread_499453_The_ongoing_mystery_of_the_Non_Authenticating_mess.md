---
title: "The ongoing mystery of the Non Authenticating message"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by Protagonistics on 2007-07-12
I know this has been brought up in previous posts but I have not found an appropriate answer yet. Some of us are experiencing partial upgrade problems. When I start my lappy up, I get the "updates available" message at the top right. I click it, and a window atop the Update manager WIndow says: 

"Not all updates can be installed

Run a partial upgrade, to install as many updates as possible.

This can be caused by:
-A previous upgrade which didn't complete
- Unofficial software packages not provided by Ubuntu
- Normal Changes of a pre-release version of Ubuntu"



There are two buttons: Partial Upgrade and Close. Partial Upgrade fails, and returns this message:


"Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

compiz
compiz-core
compiz-gnome
compiz-plugins
gaim
libtotem-plparser7
pidgin
pidgin-data
rhythmbox
totem
totem-gstreamer
totem-mozilla"



NOW. Assuming that I do not meet any of those three conditions in the first window (1: Although a previous upgrade did NOT complete, however, the failed packages were THESE packages mixed in with many succesful packages. 2: I don't know if I qualify for condition two because the packages like Pidgin ARE supported by Ubuntu but I AM using Trevino's suggested repositories (which shouldn't matter, right?). 3: Normal Changes of a pre-release? I don't think so.... I did a clean install of Feisty four days ago.), then I'm at a loss to see what is going on. I have tried all other suggestions in the other posts but with no success. Quite a few of us, it seems, could benefit from a good answer or at least further deduction. Has anyone solved this?

Thank you for your time.

Adam L.

---

### Post by bapoumba on 2007-07-12
[http://ubuntuforums.org/showpost.php?p=2999771&postcount=9]("http://ubuntuforums.org/showpost.php?p=2999771&postcount=9")
Please check this thread.

---

### Post by Protagonistics on 2007-07-12
the post linked to in the previous post here links to the thread which is discussing a problem about installing the same packages over and over again. However, I am not even installing them. THey just show up every day so of course they appear as normal updates which have simply failed the previous time- is this the same problem? sounds different to me.

---

### Post by bapoumba on 2007-07-12
Okay, sorry.
Could you post your sources.list ?
```
cat /etc/apt/sources.list
```

---

### Post by Protagonistics on 2007-07-12
Yes, here is my sources.list. Also, I deleted the two "bleeding edge" repos but to no avail. Still same old problem.

I did a manual "Check" button push in Update manager and got the VERY verbose response of all failed gpg keys (I forget what those are and I'll look them up straight away.) Sorry it's so long....

SOurces:

    # Treviño’s Ubuntu Feisty Fawn Sources list
    # [http://3v1n0.tuxfamily.org/blog/?page_id=13](http://3v1n0.tuxfamily.org/blog/?page_id=13)
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
    # In the repository list page there’s also a script that can do this
    # work automatically, this is suggested only if you know what you’re doing

    # Ubuntu supported packages (GPG key: 437D05B5)
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed main restricted
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed main restricted

    # Ubuntu community supported packages (GPG key: 437D05B5)
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security universe multiverse
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed universe multiverse

    # Ubuntu backports project (GPG key: 437D05B5)
    deb [http://mi.mirror.garr.it/ubuntu](http://mi.mirror.garr.it/ubuntu) feisty-backports main restricted universe multiverse
    deb-src [http://mi.mirror.garr.it/ubuntu](http://mi.mirror.garr.it/ubuntu) feisty-backports main restricted universe multiverse

    # CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
    # RealPlayer10, Opera, VmWare Server and more to come.)
    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

    # UbuntuStudio Repository (GPG key: B6A4EB33)
    deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
    deb-src [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

    ## kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
    #deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) feisty main
    #deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) feisty main

    ## kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
    #deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) feisty main
    #deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) feisty main

    ## kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
    #deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) feisty main
    #deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) feisty main

    # kubuntu.org packages for KDE4 alpha-1 (GPG key: DD4D5088)
    deb [http://kubuntu.org/packages/kde4-3.90.1](http://kubuntu.org/packages/kde4-3.90.1) feisty main
    deb-src [http://kubuntu.org/packages/kde4-3.90.1](http://kubuntu.org/packages/kde4-3.90.1) feisty main

    # Bleeding edge wine packages
    deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
    deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

    # Seveas’ packages (GPG key: 1135D466)
    # GPG key-file: [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg)
    deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas all
    deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas all

    # The Opera browser (packages) (GPG key: 6A423791)
    deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

    ## Google picasa packages (GPG key: 7FAC5991 - missing)
    #deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

    # Medibuntu (Multimedia, Entertainment & Distraction In Ubuntu - ex Penguin Liberation Front)
    # GPG key-file: [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg)
    deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
    deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

    # The repository from Kubuntu Germany
    # GPG key-file: [http://archive.czessi.net/ubuntu/kczessi.gpg](http://archive.czessi.net/ubuntu/kczessi.gpg)
    deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) feisty main restricted universe multiverse preview
    deb-src [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) feisty main restricted universe multiverse preview

    # Achim’s Unofficial ‘feisty’ Kubuntu packages
    # GPG key-file: [http://www.mpe.mpg.de/~ach/ach-gpg.asc](http://www.mpe.mpg.de/~ach/ach-gpg.asc)
    deb [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./
    deb-src [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./

    # Ubuntu feisty University Klagenfurt packages
    # GPG key-file: [http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub](http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub)
    # $ sudo apt-key add uniklu-debuild.pub
    #   uniklu:         backports and new packages
    #   uniklu-intern:  not freely redistributable (jvm), or modified packages
    #   uniklu-testing: packages not ready for general use
    deb     [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  feisty  uniklu
    deb     [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  feisty  uniklu-intern
    deb     [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  feisty  uniklu-testing
    deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  feisty  uniklu
    deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  feisty  uniklu-intern
    deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  feisty  uniklu-testing

    # MEPIS improvements, overrides and updates (distro based on kubuntu)
    #deb [http://apt.mepis.org/mepis32-6.5/](http://apt.mepis.org/mepis32-6.5/) mepis main
    #deb [http://apt.mepis.org/simply32-6.0/](http://apt.mepis.org/simply32-6.0/) mepis main

    # Ekiga and Debian pkg-voip
    deb [http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) feisty main

    # MythTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
    deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) feisty all
    deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) feisty all

    # Official Beryl Ubuntu Packages (GPG key: 1609B551)
    # GPG key-file: [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)
    deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
    deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

    # Ubuntu repository for Screenlets (GPG key: F854AFD7)
    # GPG key-file: [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg)
    deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets
    deb-src [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

    # Subpixel Font rendering packages (GPG key: 937215FF)
    # Improved fonts on LCDs - WARNING: May violate some patents
    # GPG key-file: [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg)
    deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts main
    deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts main

    ## Others mlind experimental misc Packages (GPG key: 937215FF)
    ## GPG key-file: [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg)
    #deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty experimental
    #deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty experimental

    # Skype packages
    deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

    # Geole’s Ubuntu Repository
    # GPG key-file: [http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg](http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg)
    deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) feisty universe multiverse
    deb-src [http://ubuntu.geole.info/](http://ubuntu.geole.info/) feisty universe multiverse
    deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) feisty-backports main universe multiverse restricted
    deb-src [http://ubuntu.geole.info/](http://ubuntu.geole.info/) feisty-backports main universe multiverse restricted

    # Linux2Go Ubuntu Packages (GPG key: E8BDA4E3)
    deb [http://www.linux2go.dk/ubuntu](http://www.linux2go.dk/ubuntu) feisty main
    deb-src [http://www.linux2go.dk/ubuntu](http://www.linux2go.dk/ubuntu) feisty main

    # Asher256’s Repository
    deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy main dupdate french
    deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french

    # Tvfreeplayer Packages (GPG key: )
    # GPG key-file: [http://www.tvfreeplayer.com/linux/falcon/tvfreeplayer.gpg](http://www.tvfreeplayer.com/linux/falcon/tvfreeplayer.gpg)
    deb [http://www.tvfreeplayer.com/linux/falcon](http://www.tvfreeplayer.com/linux/falcon) feisty all
    deb-src [http://www.tvfreeplayer.com/linux/falcon](http://www.tvfreeplayer.com/linux/falcon) feisty all

    # gnomemeeting - ekiga (GPG key: 52ABFCB1)
    deb [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) feisty main
    deb-src [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) feisty main

    ## lprod packages: many audio/video apps: avidemux, cinelerra…
    #deb [http://lprod.org/deb/feisty/](http://lprod.org/deb/feisty/) ./
    #deb-src [http://lprod.org/deb/feisty/](http://lprod.org/deb/feisty/) ./

    # Cinelerra Feisty packages
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./

    ## Spring Packages (RTS game)
    #deb [ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/](ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/) /
    #deb-src [ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/](ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/) /

    # Cafuego’s feisty Stuff: Broadcom firmware, google-earth, secondlife (GPG key: 969F3F57)…
    deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego all
    deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego all

    # Debuntu Ubuntu feisty packages
    # GPG Key: [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt)
    deb [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse
    deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse

    ## BMPx feisty Repository
    ## GPG key-file: [http://files.beep-media-player.org/packages/bmp-packages.pubkey](http://files.beep-media-player.org/packages/bmp-packages.pubkey)
    #deb [http://files.beep-media-player.org/packages/ubuntu](http://files.beep-media-player.org/packages/ubuntu) feisty main testing
    #deb-src [http://files.beep-media-player.org/packages/ubuntu](http://files.beep-media-player.org/packages/ubuntu) feisty main testing

    # Morgoth Repository (GPG key: 7E2E4741)
    # Provides Monkey’s Audio, xmms pugins, vlc plugins, gqview, audacius, audacity…
    # GPG key-file: [http://morgoth.free.fr/files/morgoth-signkey.gpg.asc](http://morgoth.free.fr/files/morgoth-signkey.gpg.asc)
    deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main
    deb-src [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main

    ## ATi & nVidia drivers Ubuntu packages
    ## GPG key: [http://albertomilone.com/drivers/tseliot.asc](http://albertomilone.com/drivers/tseliot.asc)
    #deb [http://www.albertomilone.com/drivers/feisty/latest/32bit](http://www.albertomilone.com/drivers/feisty/latest/32bit) binary/

    # Automatix repository (GPG key: E23C5FC3)
    deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

    # edevelop - e17 (Enlightenment DR 17)
    # GPG key: [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc)
    deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
    deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
    #deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) feisty e17
    #deb-src [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) feisty e17

    # Musicbrainz Repository
    # GPG key-file: [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/public.key](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/public.key)
    deb [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu) feisty musicbrainz
    deb-src [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu) feisty musicbrainz

    ## Imbrandons software repository (GPG key: 887D9FD2)
    ## GPG key-file: [http://www.imbrandon.com/packages/887D9FD2.gpg](http://www.imbrandon.com/packages/887D9FD2.gpg)
    #deb [http://www.imbrandon.com/packages](http://www.imbrandon.com/packages) feisty all
    #deb-src [http://www.imbrandon.com/packages](http://www.imbrandon.com/packages) feisty all

    ## Candyz’s Ubuntu Packages
    ## GPG key-file: [http://cle.linux.org.tw/candyz/Ubuntu/candyz.key](http://cle.linux.org.tw/candyz/Ubuntu/candyz.key)
    #deb [http://cle.linux.org.tw/candyz/Ubuntu/feisty](http://cle.linux.org.tw/candyz/Ubuntu/feisty) i386/

    # The Ubuntu NLP Repository (GPG key: 8ABD1965)
    # GPG key-file: [http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg](http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg)
    deb [http://cl.naist.jp/~eric-n/ubuntu-nlp](http://cl.naist.jp/~eric-n/ubuntu-nlp) feisty all
    deb-src [http://cl.naist.jp/~eric-n/ubuntu-nlp](http://cl.naist.jp/~eric-n/ubuntu-nlp) feisty all

    # Ubuntu System Administrator packages (GPG key: 2F306651)
    # GPG key-file: [http://ubuntu.moshen.de/2F306651.gpg](http://ubuntu.moshen.de/2F306651.gpg)
    deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty multimedia misc
    deb-src [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty multimedia misc

    ## Michael Biebl Tracker Repository (GPG key: BD058554)
    ## GPG Key-file: [http://www.teco.edu/~biebl/biebl.asc](http://www.teco.edu/~biebl/biebl.asc)
    #deb [http://debs.michaelbiebl.de/](http://debs.michaelbiebl.de/) feisty main
    #deb-src [http://debs.michaelbiebl.de/](http://debs.michaelbiebl.de/) feisty main

    # The Consciousness Repository (GPG key: DD385D79)
    # GPG key-file: [http://debs.peadrop.com/DD385D79.gpg](http://debs.peadrop.com/DD385D79.gpg)
    deb [http://debs.peadrop.com](http://debs.peadrop.com) feisty all
    deb-src [http://debs.peadrop.com](http://debs.peadrop.com) feisty all

    ## Tolero Ubuntu Repository
    #deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) feisty main
    #deb-src [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) feisty main

    # IVTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
    # GPG key-file: [http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg](http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg)
    deb [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) feisty all
    deb-src [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) feisty all

    # syzygy42 repository: avant-window-navigator, exaile, closure… (GPG key: 8434D43A)
    # GPG key-file: [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg)
    deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty all
    deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty all

    ## Firefox 3.0 alpha builds for feisty (unstable)
    #deb [http://gnomefreak.youmortals.com/mozilla-testing](http://gnomefreak.youmortals.com/mozilla-testing) feisty main
    #deb-src [http://gnomefreak.youmortals.com/mozilla-testing](http://gnomefreak.youmortals.com/mozilla-testing) feisty main

    ## Swiftfox (enhanced Firefox for linux) packages
    deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

    # Sonnes repository (aMule AdunanZa, Audacious)
    deb [http://adurepo.altervista.org/ubuntu](http://adurepo.altervista.org/ubuntu) feisty all
    deb-src [http://adurepo.altervista.org/ubuntu](http://adurepo.altervista.org/ubuntu) feisty all

    # darkmagez repository: rhythmbox and newer gtk (GPG key: A3012FB3)
    # GPG key-file: [http://mirror.randumb.org/darkmagez/repo/A3012FB3.gpg](http://mirror.randumb.org/darkmagez/repo/A3012FB3.gpg)
    deb [http://mirror.randumb.org/darkmagez/repo](http://mirror.randumb.org/darkmagez/repo) feisty-darkmagez multimedia-experimental #core-experimental
    deb-src [http://mirror.randumb.org/darkmagez/repo](http://mirror.randumb.org/darkmagez/repo) feisty-darkmagez multimedia-experimental #core-experimental

    ## Raof Repository: newer versions of Compiz, beagle, mono, scribus… (GPG key: 2F306651)
    ## GPG key-file: [http://raof.dyndns.org/falcon/2F306651.gpg](http://raof.dyndns.org/falcon/2F306651.gpg)
    #deb [http://raof.dyndns.org/falcon](http://raof.dyndns.org/falcon) feisty all
    #deb-src [http://raof.dyndns.org/falcon](http://raof.dyndns.org/falcon) feisty all

    # FoLKeN ‘Repozytorium’ (GPG key: 6FB65A0F)
    deb [http://deb.svx.pl/](http://deb.svx.pl/) feisty main universe bleeding
    deb-src [http://deb.svx.pl/](http://deb.svx.pl/) feisty main universe bleeding

    # Le dépomaniak repository (GPG key: 1D59E694)
    # GPG key-file: [http://ubuntu.davromaniak.eu/1D59E694.gpg](http://ubuntu.davromaniak.eu/1D59E694.gpg)
    deb [http://ubuntu.davromaniak.eu](http://ubuntu.davromaniak.eu) feisty-depomaniak all
    deb-src [http://ubuntu.davromaniak.eu](http://ubuntu.davromaniak.eu) feisty-depomaniak all

    # Mez’s Repository (GPG key: 6AAAA569)
    # GPG key-file: [http://apt.sourceguru.net/6AAAA569.gpg](http://apt.sourceguru.net/6AAAA569.gpg)
    deb [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty all
    deb-src [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty all

    # Ryan Kavanagh’s packages (GPG key: 02544D0E)
    # GPG key-file: [http://packages.ryanak.ca/02544D0E.gpg](http://packages.ryanak.ca/02544D0E.gpg)
    deb [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty all
    deb-src [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty all

    # OpenedHand Debian/Ubuntu Packages
    deb [http://debian.o-hand.com](http://debian.o-hand.com) feisty/
    deb-src [http://debian.o-hand.com](http://debian.o-hand.com) feisty/

    # OpenSync svn ubuntu repository (GPG key: B029CB84)
    deb [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/) feisty main
    deb-src [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/) feisty main
    # deb [http://www.in.fh-merseburg.de/~jahn/opensync-svn/](http://www.in.fh-merseburg.de/~jahn/opensync-svn/) feisty main
    # deb-src [http://www.in.fh-merseburg.de/~jahn/opensync-svn/](http://www.in.fh-merseburg.de/~jahn/opensync-svn/) feisty main

    # Iuculano’s debian packages (GPG key: AE3BE9AA)
    # GPG key-file: [http://ubuntu.iuculano.it/AE3BE9AA.gpg](http://ubuntu.iuculano.it/AE3BE9AA.gpg)
    deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty amsn thunderbird #ck-kernel #all
    deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty amsn thunderbird #ck-kernel #all

    # Elisa Debian Packages
    deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) feisty main

    # PollyCooke, il repository :)
    deb [http://download.tuxfamily.org/pollyrepo](http://download.tuxfamily.org/pollyrepo) feisty/

    # Treviño’s Ubuntu Feisty Fawn Repository (GPG key: 81836EBF - DD800CD9)
    # Many "random" bleeding edge software: aMule, aMSN, Mercury, flash…
    # Further informations and complete packages list: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)
    deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0
    deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0

    ## Treviño’s Ubuntu Suspend2 patched kernels Repository (GPG key: 81836EBF - DD800CD9)
    ## Ubuntu kernels patched with Suspend2 plus other related tools [www.suspend2.net](www.suspend2.net)
    ## Warning: they will replace standard ubuntu kernel related packages
    #deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty suspend2
    #deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty suspend2

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
#AUTOMATIX REPOS END



------------------------

And the GPG error...

W: GPG error: [http://snapshots.ekiga.net](http://snapshots.ekiga.net) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A5E3A5A52ABFCB1
W: GPG error: [http://pkg-voip.buildserver.net](http://pkg-voip.buildserver.net) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A5E3A5A52ABFCB1
W: GPG error: [http://ftp.musicbrainz.org](http://ftp.musicbrainz.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3A39A02A92132F7B
W: GPG error: [http://www.linux2go.dk](http://www.linux2go.dk) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A278DF5EE8BDA4E3
W: GPG error: [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 80E5E56B02544D0E
W: GPG error: [http://debs.peadrop.com](http://debs.peadrop.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 02D40794DD385D79
W: GPG error: [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 580E2519969F3F57
W: GPG error: [http://mirror.randumb.org](http://mirror.randumb.org) feisty-darkmagez Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB5D6B0AA3012FB3
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0A1CC62F306651
W: GPG error: [http://www.tvfreeplayer.com](http://www.tvfreeplayer.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9CFD7AEA3C6489CB
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 576856718434D43A
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [http://home.eng.iastate.edu](http://home.eng.iastate.edu) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4C8BC4C880DF6D58
W: GPG error: [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 371A69E3AE3BE9AA
W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: GPG error: [http://ubuntu.geole.info](http://ubuntu.geole.info) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BC40ED2499419355
W: GPG error: [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 84F27CD6A2BF7BCB
W: GPG error: [http://www.in.fh-merseburg.de](http://www.in.fh-merseburg.de) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB210090B029CB84
W: GPG error: [http://archive.czessi.net](http://archive.czessi.net) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A714EB87D1B1F415
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: GPG error: [http://dl.ivtvdriver.org](http://dl.ivtvdriver.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4C8BC4C880DF6D58
W: GPG error: [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2404ED3A6AAAA569
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://ubuntu.geole.info](http://ubuntu.geole.info) feisty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BC40ED2499419355
W: GPG error: [http://deb.svx.pl](http://deb.svx.pl) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C12ADDB16FB65A0F
W: GPG error: [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8CC68B397E2E4741
W: GPG error: [http://repository.debuntu.org](http://repository.debuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E466170BCF1FC29
W: GPG error: [http://edevelop.org](http://edevelop.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 223020C2A7C6F0DF
W: GPG error: [http://www.telemail.fi](http://www.telemail.fi) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: GPG error: [http://cl.naist.jp](http://cl.naist.jp) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B8F0E6C98ABD1965
W: GPG error: [http://ubuntu.davromaniak.eu](http://ubuntu.davromaniak.eu) feisty-depomaniak Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8BB73F9E1D59E694
W: GPG error: [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A361B38AB6A4EB33


Thanks.

---

### Post by bapoumba on 2007-07-12
That's quite a sources.list...
You have edgy, mepis and debian repos in there. I would comment them out.

And in addition, would you consider keeping only the official ubuntu repos without the -proposed repositories (for testing packages that will make it to the official repos if no bugs are reported) and the -backports ?
```
# Ubuntu supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu feisty main restricted 
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://archive.ubuntu.com/ubuntu feisty-security main restricted

deb-src http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted


```

And run:
```
sudo aptitude update
```
(you could add universe and multiverse to the above ones).

---

### Post by Protagonistics on 2007-07-12
Yeah... I just added whatever Trevino had in there as I was using what I thought was the same list before I reinstalled. I'll remove the debian and mepis repos and see what helps.

---

### Post by bapoumba on 2007-07-12
> **Protagonistics said:**
>  I'll remove the debian and mepis repos and see what helps.
and the edgy ones.
They may cause the partial upgrade.

---

### Post by Protagonistics on 2007-07-12
that's not working either. I'm guessing to resolve this I should return to the most "normal" repos possible-- but the problem with that is that I have been repeatedly dissapointed with the lack of software that I occasionally want to get-- I have spent hours trying to figure out the repos for commonly discussed apps. SO, I just decided to get all the repos and just not worry any more. This is a weakness in ubuntu, in my book. but not a major one.

What qualifies as "normal?" I guess that's really subjective and I would have to say that I'm not and never will be a developer or beta tester. I just want good, stable supported software. Should I just use the automatically generated repos that I can get off the ubuntu wiki?

---

### Post by bapoumba on 2007-07-12
```
~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Alpha i386 (20070228.1)]/ feisty main restricted

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

## Major bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse

## Security updates
deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse

## Backports.
# deb http://fr.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

## Medibuntu
# deb http://packages.medibuntu.org/ feisty free non-free
```
[Medibuntu]("https://help.ubuntu.com/community/Medibuntu") info. I do not enable the backports and medibuntu on a daily basis. I just look from time to time if there is anything new.

You can start from there, get a clean system, and then add other third party repos one by one, but at your on risk ;)

---

### Post by Protagonistics on 2007-07-12
Wow, that was fun (seriously). Everything is fixed now... though I worry about all those programs I'll want. Is there anything I might not know about that allows better visibility of a lot/most/all repositories in existance so that new users can get a better idea of what repos are needed to get some software?

---

### Post by bapoumba on 2007-07-12
I might not be hanging around for too long (getting late over here). Make your list, I (and other members too) will look into it. You probably also want to search over the forums, and see how people do regarding the packages you're interested into.

---

