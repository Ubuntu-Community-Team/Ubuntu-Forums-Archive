---
title: "Reverse dist-upgrade"
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by jaywhy13 on 2006-10-01
I think I did summin stupid... ](*,)  I changed my sources.list file to this elongated one that has many repos for debian and a whole lot a whole lot a different stuff... Forgettin that I had changed it. I did a dist-upgrade.

Am running grub and I get a kernel-panic error for the newest kernel 2.6.15-26-386, also loading restricted-drivers now fails.

Any suggestions on whether what I did was really stupid and if I need to reverse it and if it can be done or so? 

PLease help 

Sources.list file
```
      # Based on source-o-matic (http://www.ubuntulinux.nl/source-o-matic) list
       # Added extra repository
       #
       # If you get errors about missing keys, lookup the key in this file
       # and run these commands (replace KEY with the key number)
       #
       # gpg –keyserver subkeys.pgp.net –recv KEY
       # gpg –export –armor KEY | sudo apt-key add -                 # Ubuntu supported packages (packages, GPG key: 437D05B5)
       deb http://archive.ubuntu.com/ubuntu dapper main restricted
       deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
       deb http://security.ubuntu.com/ubuntu dapper-security main restricted
          # Ubuntu supported packages (sources, GPG key: 437D05B5)
       deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
       deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
       deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
          # Ubuntu community supported packages (packages, GPG key: 437D05B5)
       deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
       deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
       deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
          # Ubuntu community supported packages (sources, GPG key: 437D05B5)
       deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
       deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
       deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
          # Ubuntu backports project (packages, GPG key: 437D05B5)
       deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
          # Ubuntu backports project (sources, GPG key: 437D05B5)
       deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
# CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
# RealPlayer10, Opera and more to come.)
deb http://archive.canonical.com/ubuntu dapper-commercial main    # Seveas’ packages (packages, GPG key: 1135D466)
       deb http://mirror.ubuntulinux.nl dapper-seveas all
          # Seveas’ packages (sources, GPG key: 1135D466)
       deb-src http://mirror3.ubuntulinux.nl dapper-seveas all
          # Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
       deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
          # Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
       deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main
          # kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
       deb http://kubuntu.org/packages/kde-latest dapper main
          # kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
       deb-src http://kubuntu.org/packages/kde-latest dapper main
deb http://kubuntu.org/packages/kde-354 dapper main
          # kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
       deb http://kubuntu.org/packages/koffice-latest dapper main
          # kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
       deb-src http://kubuntu.org/packages/koffice-latest dapper main
          # kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
       deb http://kubuntu.org/packages/amarok-latest dapper main
          # kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
       deb-src http://kubuntu.org/packages/amarok-latest dapper main
          # Bleeding edge wine packages (packages)
       deb http://wine.budgetdedicated.com/apt dapper main
          # Bleeding edge wine packages (sources)
       deb-src http://wine.budgetdedicated.com/apt dapper main
          # The Opera browser (packages)
       deb http://deb.opera.com/opera etch non-free
          # Penguin Liberation Front (packages)
       #deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free
       deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
          # Penguin Liberation Front (sources)
       #deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free
       deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
          ## archive.kubuntu.de / archive.czessi.net
       # The repository from Kubuntu Germany
       # wget http://archive.czessi.net/ubuntu/kczessi.gpg
       # sudo apt-key add kczessi.gpg
       deb http://archive.czessi.net/ubuntu dapper main restricted universe multiverse preview
       deb-src http://archive.czessi.net/ubuntu dapper main restricted universe multiverse preview
          # Amarok 1.4 Packages
       deb http://kubuntu.org/packages/amarok-14 dapper main
          # KDE 3.5.3 Packages
       deb http://kubuntu.org/packages/kde-353 dapper main
          # KOffice 1.5.1 Packages
  deb http://kubuntu.org/packages/koffice-151 dapper main
          ## Doomsday games
       #deb http://eyagi.bpa.nu/~jamie/ubuntu dapper main restricted universe multiverse
       #deb-src http://eyagi.bpa.nu/~jamie/ubuntu dapper main restricted universe multiverse
             # Dev not-public (Breezy Packages)
       deb http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/ breezy free non-free
       deb-src http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/ breezy free non-free
          # Achim’s Unofficial ‘dapper’ Kubuntu packages
       deb http://www.mpe.mpg.de/~ach/kubuntu/dapper ./
       deb-src http://www.mpe.mpg.de/~ach/kubuntu/dapper ./
          # Ubuntu Taiwan ubuntu extra repository
       deb http://apt.ubuntu.org.tw ubtw/
       deb http://apt.ubuntu.org.tw ubtw-testing/
          # Ubuntu dapper University Klagenfurt packages
       # $ wget http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub
       # $ sudo apt-key add uniklu-debuild.pub
       #   uniklu:         backports and new packages
       #   uniklu-desktop: packages for uniklu desktop
       #   uniklu-intern:  not freely redistributable (jvm), or modified packages
       #   uniklu-nfsv4:   nfsv4 kernel and packages
       #   uniklu-vserver: vserver kernel
       #   uniklu-testing: packages not ready for general use !
       deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu
       deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu-desktop
       deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu-intern
       deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu-nfsv4
       deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu-vserver
       deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu-testing
       deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu
       deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu-desktop
       deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu-intern
       deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu-nfsv4
       deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu-vserver
       deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu-testing
          # Ekiga and Debian pkg-voip
       deb http://pkg-voip.buildserver.net/ubuntu dapper main
          # VLC nightlies
       deb http://nightlies.videolan.org/build/dapper-i386 /
          # # MaXeR (KDE Apps)
       # # deb http://repos.knio.it/ sarge main contrib non-free
       # # deb-src http://repos.knio.it/ sarge main contrib non-free
       # deb http://repos.knio.it/ breezy main contrib non-free
       # deb-src http://repos.knio.it/ breezy main contrib non-free
                     # Quinn’s Compiz Packages - http://xgl.compiz.info/
       deb http://www.beerorkid.com/compiz dapper main
       deb http://xgl.compiz.info/ dapper main
       deb-src http://xgl.compiz.info/ dapper main
          # CompizTool package
       deb http://compiztools.free.fr/debian unstable main
          # Wormux - Worm Clone packages
       deb http://download.gna.org/wormux/debs dapper/
          # Skype packages
       deb http://download.skype.com/linux/repos/debian/ stable non-free
          # Easycam packages
       deb http://blognux.free.fr/debian unstable main
          # Audacious
       deb http://vdlinux.sourceforge.jp/ experimental audacious
       deb-src http://vdlinux.sourceforge.jp/ experimental audacious
          # Listen
       deb http://theli.free.fr/packages/dapper/    ./
          # BMPx
       deb http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/ dapper/
          # Freevo
       # wget http://www.geole.de/fileadmin/data/misc/geole-apt-key.gpg
       # sudo apt-key add geole-apt-key.gpg
       deb http://ubuntu.geole.de/ dapper universe multiverse
          # Samba
       deb http://www.linux2go.dk/ubuntu dapper main
          # GCompris, Televidilo, Kdocker,…
       deb http://thomas.enix.org/pub/debian/packages/ dapper main
          # Asher256’s Repository
       deb http://asher256-repository.tuxfamily.org breezy main dupdate french
       deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french
          # Gauvain Repository
       deb http://gauvain.tuxfamily.org/repos dapper contrib
       deb-src http://gauvain.tuxfamily.org/repos dapper contrib
          # Tvfreeplayer Packages
       deb http://www.tvfreeplayer.com/linux/ubuntu/dapper/ unstable main
          # gnomemeeting (ekiga)
       deb http://snapshots.gnomemeeting.net/ubuntu/ dapper main
       deb-src http://snapshots.gnomemeeting.net/ubuntu/ dapper main
       deb http://snapshots.voxgratia.org/ubuntu/ dapper main
       deb-src http://snapshots.voxgratia.org/ubuntu/ dapper main
          # seb128 repository (gaim - rhythmbox)
       deb http://people.ubuntu.com/~seb128/deb ./
          ## lprod packages: many audio/video apps: avidemux, cinelerra… (breezy partly working on dapper)
       # deb http://lprod.org/deb/breezy/ ./
          # Mjpegtools and Cinelerra packages (choose your arch)
  deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
  deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./
  # deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./
  # deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./
        # LiVes dapper package
deb http://people.ubuntubrasil.org/~rclbelem/lives/dapper/ ./binary/
          # A little too quiet
       deb http://apt.alittletooquiet.net/staging dapper main
          # MythTV 0.19
  deb http://home.eng.iastate.edu/~superm1 dapper main
  deb-src http://home.eng.iastate.edu/~superm1 dapper main
          # Debuntu Ubuntu dapper packages
deb http://repository.debuntu.org/ dapper multiverse
deb-src http://repository.debuntu.org/ dapper multiverse        # BMPx Dapper Repository
# GPG key-file: http://files.beep-media-player.org/packages/bmp-packages.pubkey
deb http://files.beep-media-player.org/packages/ubuntu dapper main universe
deb-src http://files.beep-media-player.org/packages/ubuntu dapper main universe
        # Treviño’s Ubuntu Dapper Repository (GPG key: 81836EBF)
# Many “random” software: aMule, amsn, gnash, google-earth, stellarium, moto4lin…
# Further informations: http://3v1n0.tuxfamily.org
deb http://3v1n0.tuxfamily.org dapper 3v1n0

# KDE-Bluetooth
deb http://fred.hexbox.de/debian ./

```

---

