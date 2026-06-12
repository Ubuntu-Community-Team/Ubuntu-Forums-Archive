---
title: "[SOLVED] Issues with Upgrade from 7.04 to 7.10"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by ajay_g_m on 2008-03-07
I ran the following command (with the Ubuntu 7.10 i386 alternate CD)...
$ gksu "sh /cdrom/cdromupgrade"

I get the following message...
[I]--------------------------------------------------------------
Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
--------------------------------------------------------------
[/I]

After this the distribution upgrade just rolls back.

Have attached the files that were requested.

Please help.

---

### Post by taurus on 2008-03-07
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by ajay_g_m on 2008-03-07
$ cat /etc/apt/sources.list

-----------------------------------------------------------------------------

[I]# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted universe multiverse






deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main universe multiverse
[/I]

-----------------------------------------------------------------------------

---

### Post by ajay_g_m on 2008-03-07
$ cat /etc/apt/sources.list

-----------------------------------------------------------------------------

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted universe multiverse






deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main universe multiverse


-----------------------------------------------------------------------------

---

### Post by ajay_g_m on 2008-03-07
Your /etc/apt/sources.list doesn't look complete and you have both Feisty and Gutsy in there.

So, I would make a copy of it first in case you need to recall it later

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
and edit it.

```
gksudo gedit /etc/apt/sources.list
```
Now, delete everything in there and add these new lines for Feisty.

```

deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

#deb http://archive.canonical.com/ubuntu feisty-commercial main

```
Save it and close down gedit editing window.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```
Now, see if you can upgrade from Feisty to Gutsy again.[/QUOTE]

---

### Post by ajay_g_m on 2008-03-07
The following is the result....

```
**$ sudo apt-get upgrade**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  emacs gnupg hal rhythmbox
The following packages will be upgraded:
  apache2 apache2-doc apache2-mpm-worker apache2-utils apache2.2-common app-install-data app-install-data-commercial apport apport-gtk bind9-host bsdutils capplets-data cdrecord
  cupsys cupsys-bsd cupsys-client cupsys-common dbus dbus-1-utils dnsutils e2fslibs e2fsprogs emacs21 emacs21-bin-common emacs21-common evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-plugins file firefox firefox-gnome-support foo2zjs genisoimage gimp gimp-data gimp-python gnome-app-install
  gnome-btdownload gnome-control-center gnome-media gnome-media-common gnome-panel gnome-panel-data gnome-system-tools gpgv hal-device-manager hpijs hplip hplip-data iptables
  kdelibs-data kdelibs4c2a khelpcenter language-pack-en language-pack-gnome-en language-pack-gnome-gu language-pack-gnome-hi language-pack-gu language-pack-hi lftp libbind9-0
  libblkid1 libcairo2 libcamel1.2-10 libcdio6 libcomerr2 libcupsimage2 libcupsys2 libcurl3 libdbus-1-3 libdns22 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 libexif12 libflac7 libfreetype6 libgimp2.0 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa
  libgnome-media0 libgnome-window-settings1 libhal-storage1 libhal1 libisc11 libisccc0 libisccfg1 libjasper-1.701-1 libkpathsea4 libkrb53 liblwres9 libmagic1 libmagick9
  libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libnspr4 libnss3 libopal-2.2.0 libpanel-applet2-0
  libpcre3 libperl5.8 libpng12-0 libpoppler1 libpoppler1-glib libpq5 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqt3-mt libslab0 libsmbclient
  libsndfile1 libsnmp-base libsnmp9 libss2 libssl0.9.8 libsvn1 libuuid1 libvorbis0a libvorbisenc2 libvorbisfile3 libwrap0 libxfont1 libxml2 libxml2-utils mesa-utils metacity
  metacity-common mkisofs mono-common mono-gac mono-jit mono-runtime mount openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-math openoffice.org-style-human openoffice.org-writer openssl perl perl-base perl-modules poppler-utils python python-apport python-gdbm python-launchpad-bugs
  python-libxml2 python-minimal python-problem-report python-uno rdesktop rsync samba-common smbclient ssh-askpass-gnome subversion tar tcpdump tomboy ttf-opensymbol tzdata
  util-linux util-linux-locales vim-common vim-tiny wodim xscreensaver-data xscreensaver-gl xserver-xorg-core
202 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 257MB of archives.
After unpacking 16.5MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

The download size is too big for the internet connection I have. 
That was the main reason why I had gone for the alternate cd v/s the upgrade via internet.

Can someone suggest some method to get the upgrade working without downloading those 257MB?

---

### Post by zvacet on 2008-03-07
I belive if you are doing distro upgrade from alternate CD you have choise to upgrade with or without updates.So in your case choose second one.You can install updates from another comp with fast(er) connection with [nonetdebs.](http://nonetdebs.homeip.net/)

---

### Post by ajay_g_m on 2008-03-08
Hi All,

I got this resolved using 'Synaptic Package Manager' with the following steps:
[LIST=1] 
[*]Settings -> Repositories. 
[LIST=a] 
[*]'Ubuntu Software' tab -> Uncheck all options
[*]'Third-Party Software' tab -> Uncheck all options
[*]'Third-Party Software' tab -> Using 'Add CD-ROM' register the alternate CD.
[/LIST]
[*]Edit -> Reload Package Information. 
[*]Selected all packages listed in Status -> Installed (upgradable) 
[*]Package -> Mark for Upgrade.
[/LIST]

Now I'm not sure if this would have broken anything. But at first look, seems like it has resolved my issue.

So the general conclusion with this seems...
Instead of using 'Update Manager' to update which seems to give all the above issues, this one does not give these issues.

Again, I'm not sure if I have really screwed up my system or what. Will come to know in a few days.

Will keep updated if there are any side effects that I notice.

---

