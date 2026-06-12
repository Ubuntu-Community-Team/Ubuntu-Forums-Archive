---
title: "gnome-system-tools unavailable? bad upgrade?"
date: 2008-05-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by KIAaze on 2008-05-16
Is it normal that gnome-system-tools can currently not be installed on intrepid?

[http://packages.ubuntu.com/intrepid/gnome-system-tools](http://packages.ubuntu.com/intrepid/gnome-system-tools)

I tried to follow the dependencies and get this:
gnome-system-tools->liboobs-1-4->system-tools-backends->libnet-dbus-perl->perlapi-5.8.8->Package not available

Here's my current sources.lst:
```
# deb cdrom:[Ubuntu 7.10 _Hardy Heron_ - Release i386 (20071016)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://fr.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties
# Line commented out by installer because it failed to verify:

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://fr.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://fr.archive.ubuntu.com/ubuntu/ intrepid universe
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb http://fr.archive.ubuntu.com/ubuntu/ intrepid-updates universe
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://fr.archive.ubuntu.com/ubuntu/ intrepid multiverse
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb http://fr.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
# Line commented out by installer because it failed to verify:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://fr.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
#deb-src http://fr.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security restricted main multiverse universe #Added by software-properties
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:

## for code::blocks
## KEY GPG : wget -q http://lgp203.free.fr/public.key -O- | sudo apt-key add -
# deb http://lgp203.free.fr/ubuntu/ intrepid universe
## for wxwidgets
## KEY wget -q http://apt.wxwidgets.org/key.asc -O- | sudo apt-key add -
# deb http://apt.wxwidgets.org/ intrepid-wx main
# deb http://archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse #Added by software-properties
# deb http://blognux.free.fr/debian unstable main

```

Maybe I did something wrong when upgrading to intrepid.
I used:
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get upgrade

And later made some manual upgrades in Synaptic, which removed some packages.

---

### Post by caryb on 2008-05-16
Theres a pile of upgrades ATM for Gnome panel etc, might fix your problem!'


Cary

---

### Post by KIAaze on 2008-05-17
No, gnome-panel is up to date for me:
```
ii  gnome-panel                                1:2.22.1.2-0ubuntu3                                launcher and docking facility for GNOME
ii  gnome-panel-data                           1:2.22.1.2-0ubuntu3                                common files for the GNOME Panel

```

However, I noticed that another one of my problems is linked to perlapi being unavailable:
gnome-applets got uninstalled during one manual upgrade I made in Synaptic (which removes packages unlike "apt-get upgrade").
And I can't reinstall/it got removed because it also depends on liboobs-1-4, which as previously is linked to perlapi... :(

I guess I shouldn't have upgraded through Synaptic manually.

My problem without gnome-applets is that some applets can't load anymore obviously:
-mixer applet
-system monitor applet
-trash applet

I do have a log of the bad upgrade because I _did notice_ that lots of stuff was going to be removed:
```
abiword will be removed
acidrip will be removed
atlas3-base will be removed
atlas3-headers will be removed
bibtex2html will be removed
dhelp will be removed
digikam will be removed
fast-user-switch-applet will be removed
foomatic-db-hpijs will be removed
g++-3.4 will be removed
g77 will be removed
g77-3.4 will be removed
gaim will be removed
gcc-4.2 will be removed
gcj-4.2 will be removed
gfortran-4.2 will be removed
git-core will be removed
gitk will be removed
gnome-applets will be removed
gnome-system-tools will be removed
hpijs will be removed
hplip will be removed
hplip-gui will be removed
kdebase-kio-plugins will be removed
kmail will be removed
kmailcvt will be removed
konq-kim will be removed
konq-plugins will be removed
konq-toutf8 will be removed
konqueror will be removed
konqueror-nsplugins will be removed
kontact will be removed
lapack3 will be removed
lapack3-dev will be removed
libcairo-perl will be removed
libclamav3 will be removed
libclanlib-dev will be removed
libdbd-mysql-perl will be removed
libdbi-perl will be removed
libdigest-sha1-perl will be removed
libg2c0 will be removed
libg2c0-dev will be removed
libgcj8-dev will be removed
libglib-perl will be removed
libgnome2-canvas-perl will be removed
libgnome2-perl will be removed
libgnome2-vfs-perl will be removed
libgtk2-perl will be removed
libmodule-signature-perl will be removed
libnet-dbus-perl will be removed
liboobs-1-4 will be removed
libperl5.8 will be removed
libpurple0 will be removed
libqt-perl will be removed
libsnmp15 will be removed
libstdc++6-dev will be removed
libsuitesparse will be removed
libtemplate-perl will be removed
libtext-bibtex-perl will be removed
linux-kernel-devel will be removed
mysql-client-5.0 will be removed
mysql-server-5.0 will be removed
pidgin will be removed
pidgin-otr will be removed
refblas3-dev will be removed
system-tools-backends will be removed
ubuntu-desktop will be removed
vim-full will be removed
vim-gnome will be removed
vim-gtk will be removed
vim-python will be removed
xchat will be removed
xchat-gnome will be removed
clamav (version 0.92.1~dfsg2-1.1) will be upgraded to version 0.93~dfsg-1
clamav-freshclam (version 0.92.1~dfsg2-1.1) will be upgraded to version 0.93~dfsg-1
cpp-3.4 (version 3.4.6-6ubuntu3) will be upgraded to version 3.4.6-7ubuntu2
dansguardian (version 2.8.0.6-antivirus-6.4.4.1-4build1) will be upgraded to version 2.9.9.4-1
gcc-3.4 (version 3.4.6-6ubuntu3) will be upgraded to version 3.4.6-7ubuntu2
gcc-3.4-base (version 3.4.6-6ubuntu3) will be upgraded to version 3.4.6-7ubuntu2
gnome-games-extra-data (version 2.20.0-1) will be upgraded to version 2.22.0-1
k3b (version 1.0.4-2ubuntu4) will be upgraded to version 1.0.4-8ubuntu2
kdelibs (version 4:3.5.9-0ubuntu7) will be upgraded to version 4:3.5.9.dfsg.1-4ubuntu3
kdelibs4c2a (version 4:3.5.9-0ubuntu7) will be upgraded to version 4:3.5.9.dfsg.1-4ubuntu3
libcegui-mk2-1 (version 0.5.0-2) will be upgraded to version 0.5.0-3
libcegui-mk2-dev (version 0.5.0-2) will be upgraded to version 0.5.0-3
libcegui-mk2-doc (version 0.5.0-2) will be upgraded to version 0.5.0-3
libceguiogre-dev (version 1.4.5-3build1) will be upgraded to version 1.4.6.dfsg1-1
libcommandline-ruby1.8 (version 0.7.10-9) will be upgraded to version 0.7.10-10
libcrypt-ssleay-perl (version 0.55-1) will be upgraded to version 0.57-1
libdigest-sha-perl (version 5.45-1) will be upgraded to version 5.47-1
libfinance-quote-perl (version 1.13-1) will be upgraded to version 1.13-2
libgettext-ruby1.8 (version 1.9.0-1) will be upgraded to version 1.90.0-2
libglpk0 (version 4.25-1) will be upgraded to version 4.28-3
libhtml-parser-perl (version 3.56-1) will be upgraded to version 3.56-1build1
liblocale-gettext-perl (version 1.05-2ubuntu1) will be upgraded to version 1.05-4
libmono-zeroconf1.0-cil (version 0.7.3-1) will be upgraded to version 0.7.6-1
libmysql++-dev (version 2.3.2-1) will be upgraded to version 3.0.0-1
libogre-dev (version 1.4.5-3build1) will be upgraded to version 1.4.6.dfsg1-1
libqimageblitz4 (version 0.0.706674-2build1) will be upgraded to version 1:0.0.4-3
libqt4-core (version 4.3.4-0ubuntu3) will be upgraded to version 4.4.0-1ubuntu3
libqt4-dev (version 4.3.4-0ubuntu3) will be upgraded to version 4.4.0-1ubuntu3
libqt4-gui (version 4.3.4-0ubuntu3) will be upgraded to version 4.4.0-1ubuntu3
libqt4-qt3support (version 4.3.4-0ubuntu3) will be upgraded to version 4.4.0-1ubuntu3
libqt4-sql (version 4.3.4-0ubuntu3) will be upgraded to version 4.4.0-1ubuntu3
libsdl-perl (version 1.20.3dfsg-2.1) will be upgraded to version 1.20.3dfsg-3
libsoprano4 (version 2.0.0-1) will be upgraded to version 2.0.98-1
libstrigiqtdbusclient0 (version 0.5.7-2) will be upgraded to version 0.5.9-1
libtaglib2.0-cil (version 2.0.3.0-1) will be upgraded to version 2.0.3.0-2
libterm-readkey-perl (version 2.30-3ubuntu1) will be upgraded to version 2.30-3ubuntu2
libtext-charwidth-perl (version 0.04-4build1) will be upgraded to version 0.04-5build1
libtext-iconv-perl (version 1.4-3) will be upgraded to version 1.7-1build1
libtolua-dev (version 4.0a-3) will be upgraded to version 5.1b-3
libxml-parser-perl (version 2.34-4.3) will be upgraded to version 2.36-1.1build1
mailx (version 1:8.1.2-0.20071017cvs-2) will be upgraded to version 1:20071201-3
ocaml-base-nox (version 3.10.0-8) will be upgraded to version 3.10.1-1
pciutils (version 1:2.2.4-1.1ubuntu3) will be upgraded to version 1:3.0.0-3
perl (version 5.8.8-12) will be upgraded to version 5.10.0-10
perl-base (version 5.8.8-12) will be upgraded to version 5.10.0-10
perl-modules (version 5.8.8-12) will be upgraded to version 5.10.0-10
perl-suid (version 5.8.8-12) will be upgraded to version 5.10.0-10
perl-tk (version 1:804.027-8) will be upgraded to version 1:804.028-1
python-cerealizer (version 0.6-1) will be upgraded to version 0.6-2
python-soya-doc (version 0.13~rc1-1) will be upgraded to version 0.14~rc1-1
qt4-designer (version 4.3.4-0ubuntu3) will be upgraded to version 4.4.0-1ubuntu3
qt4-dev-tools (version 4.3.4-0ubuntu3) will be upgraded to version 4.4.0-1ubuntu3
system-config-printer-common (version 0.9.90+svn2385-0ubuntu1) will be upgraded to version 0.9.90+svn2385-0ubuntu2
system-config-printer-gnome (version 0.9.90+svn2385-0ubuntu1) will be upgraded to version 0.9.90+svn2385-0ubuntu2
ttf-thai-tlwg (version 1:0.4.8-1) will be upgraded to version 1:0.4.9-1
vbetool (version 1.0-1.1) will be upgraded to version 1.0-3
xserver-xorg-video-amd (version 2.8.0-7) will be upgraded to version 2.9.0-1
xserver-xorg-video-geode (version 2.8.0-7) will be upgraded to version 2.9.0-1
xserver-xorg-video-intel (version 2:2.2.1-1ubuntu12) will be upgraded to version 2:2.2.1-2ubuntu1
bsd-mailx (version 8.1.2-0.20071201cvs-3) will be installed
esound-clients (version 0.2.38-0ubuntu9) will be installed
gnucash (version 2.2.4-1ubuntu1) will be installed
gnucash-docs (version 2.2.0-3) will be installed
irb1.8 (version 1.8.6.111-2ubuntu1) will be installed
k3b-data (version 1.0.4-8ubuntu2) will be installed
libceguiogrerenderer-1.4.6 (version 1.4.6.dfsg1-1) will be installed
libclamav4 (version 0.93~dfsg-1) will be installed
libggi-target-x (version 1:2.2.1-5ubuntu1) will be installed
libmysql++3 (version 3.0.0-1) will be installed
libogremain-1.4.6 (version 1.4.6.dfsg1-1) will be installed
libopen4-ruby1.8 (version 0.9.6-2) will be installed
libpci3 (version 1:3.0.0-3) will be installed
libperl5.10 (version 5.10.0-10) will be installed
libqt4-assistant (version 4.4.0-1ubuntu3) will be installed
libqt4-dbus (version 4.4.0-1ubuntu3) will be installed
libqt4-designer (version 4.4.0-1ubuntu3) will be installed
libqt4-help (version 4.4.0-1ubuntu3) will be installed
libqt4-network (version 4.4.0-1ubuntu3) will be installed
libqt4-opengl (version 4.4.0-1ubuntu3) will be installed
libqt4-opengl-dev (version 4.4.0-1ubuntu3) will be installed
libqt4-script (version 4.4.0-1ubuntu3) will be installed
libqt4-sql-mysql (version 4.4.0-1ubuntu3) will be installed
libqt4-sql-sqlite (version 4.4.0-1ubuntu3) will be installed
libqt4-svg (version 4.4.0-1ubuntu3) will be installed
libqt4-test (version 4.4.0-1ubuntu3) will be installed
libqt4-webkit (version 4.4.0-1ubuntu3) will be installed
libqt4-xml (version 4.4.0-1ubuntu3) will be installed
libqt4-xmlpatterns (version 4.4.0-1ubuntu3) will be installed
libqtcore4 (version 4.4.0-1ubuntu3) will be installed
libqtgui4 (version 4.4.0-1ubuntu3) will be installed
libreadline-ruby1.8 (version 1.8.6.111-2ubuntu1) will be installed
linux-image-2.6.24-16-386 (version 2.6.24-16.30) will be installed
orbit (version 0.5.17-11.1ubuntu4) will be installed
perl-doc (version 5.10.0-10) will be installed
qt4-qtconfig (version 4.4.0-1ubuntu3) will be installed
virtualbox-ose-modules-2.6.24-16-386 (version 24) will be installed

```

Should I reinstall some packages using the -f option to get around this?

---

