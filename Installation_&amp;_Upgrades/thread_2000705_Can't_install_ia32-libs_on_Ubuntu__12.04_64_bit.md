---
title: "Can't install ia32-libs on Ubuntu  12.04 64 bit"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by Tiefschnee on 2012-06-10
Hey there,

I'm trying to install ia32-libs, when I run sudo apt-get install ia32-libs I get the following output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.

```and when I run sudo apt-get install ia32-libs-multiarch:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: libcurl3:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```Basically I'm trying to get sopcast to get working, which depends on ia32-libs.

I also tried to install the teamviewer packet, which makes ubuntu software center return "Cannot install 'ia32-libs'".

Anybody any idea what I'm doing wrong? Any thoughts and help are greatly  appreciated!

-Peter

---

### Post by dino99 on 2012-06-10
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/879091](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/879091)

[http://ubuntuforums.org/showthread.php?t=1880965](http://ubuntuforums.org/showthread.php?t=1880965)

---

### Post by Tiefschnee on 2012-06-12
Thank you very much for the reply.

I had a look at the threads, but there doesn't seem to be a solution.

Strange thing is, on a different computer, with a clean install of 12.04 64bit, it works just fine.

---

### Post by raja.genupula on 2012-06-12
what you got after doing 
```
sudo apt-get install -f
```

---

### Post by Tiefschnee on 2012-06-12
unfortunately the same thing:

```
$ sudo apt-get install -f


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


$ sudo apt-get install ia32-libs-multiarch

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: libcurl3:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Is it possible to "reinstall" ubuntu? (without losing the currently installed programs and settings)

-Peter

---

### Post by Tiefschnee on 2012-06-12
Here [http://goo.gl/cyodc](http://goo.gl/cyodc) someone had a similar issue and it was recommend to run sudo apt-get install librtmp0 librtmp0:i386, which produces the following output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
librtmp0 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 librtmp0 : Conflicts: librtmp0:i386 but 2.4~git20120222.60218d3-ppa2~precise is to be installed
 librtmp0:i386 : Conflicts: librtmp0 but 2.4~git20120222.60218d3-ppa2~precise is to be installed
E: Unable to correct problems, you have held broken packages.
```As I understand, librtmp0 is used for streaming, the only things that I can think of in my system that could have something to do with that, are Kaffeine, VLC, TVheadend and Flash - and it seems to be associated with tvheadend

If I try to install, or better reinstall this [http://goo.gl/5VKXZ]("https://launchpad.net/%7Ealexandr-surkov/+archive/xbmc-pvr/+build/3231485") tells me that it basically has to uninstall my entire system.

Any hint is greatly appreciated.

---

### Post by Tiefschnee on 2012-06-12
OK, went through the dependencies:

```
$ sudo apt-get install ia32-libs-multiarch

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: libcurl3:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
``````
$ sudo apt-get install libcurl3:i386

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcurl3:i386 : Depends: librtmp0:i386 (>= 2.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
``````
$ sudo apt-get install librtmp0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  virtuoso-minimal libqca2 python-bluez libgraphicsmagick3 libhal-storage1
  libqt4-qt3support libpolkit-qt-1-1 libxine1-x libqapt-runtime libvirtodbc0
  python-compizconfig libilmbase6 libmicrohttpd5 odbcinst1debian2
  libqt4-designer libsdl-mixer1.2 libthreadweaver4 phonon libkrosscore4
  python-lxml odbcinst virtuoso-opensource-6.1-bin libxine1-plugins libsolid4
  libpcrecpp0 virtuoso-opensource-6.1-common kde-runtime-data libclucene0ldbl
  libqapt1 shared-desktop-ontologies libhal1 libmikmod2 libgif4
  gir1.2-unique-3.0 libopenexr6 icoutils libxine1-console libntrack0
  libphonon4 libkntlm4 libxine1-misc-plugins phonon-backend-gstreamer
  ntrack-module-libnl-0 libvdpau1 libkjsembed4 libkjsapi4 libstreams0
  libntrack-qt4-1 libva-glx1 libqtwebkit4 libxine1-bin libxine1-ffmpeg
  landscape-common libstreamanalyzer0 libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc-4.6-base:i386 libc6:i386 libgcc1:i386 libgcrypt11:i386 libgnutls26:i386
  libgpg-error0:i386 libp11-kit0:i386 libtasn1-3:i386 python3 python3-minimal
  python3.2 python3.2-minimal zlib1g:i386
Suggested packages:
  glibc-doc:i386 locales:i386 rng-tools:i386 gnutls-bin:i386 python3-doc
  python3-tk python3.2-doc binfmt-support
The following packages will be REMOVED:
  apt-transport-https aptdaemon apturl brasero-cdrkit evolution-data-server
  flashplugin-installer gir1.2-rb-3.0 gir1.2-totem-1.0
  gir1.2-totem-plparser-1.0 gir1.2-ubuntuoneui-3.0 gnome-contacts
  gstreamer0.10-plugins-bad jockey-common jockey-gtk kaffeine katepart
  kde-runtime kdelibs-bin kdelibs5-plugins kdoctools kerneloops-daemon
  kubuntu-debug-installer landscape-client landscape-client-ui
  landscape-client-ui-install language-selector-gnome libbrasero-media3-1
  libcmis-0.2-0 libcurl3 libcurl3-gnutls libcurl3-nss libfolks-eds25
  libgdata13 libkatepartinterfaces4 libkde3support4 libkdewebkit5
  libkemoticons4 libkfile4 libkhtml5 libkio5 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkparts4 libktexteditor4 libnepomuk4
  libnepomukdatamanagement4 libnepomukquery4a libnepomuksync4 libnepomukutils4
  liboauth0 libplasma3 libquvi7 libraptor2-0 librasqal3 librdf0
  libreoffice-base-core libreoffice-common libreoffice-core
  libreoffice-emailmerge libreoffice-gnome libreoffice-gtk
  libreoffice-style-human libreoffice-style-tango librhythmbox-core5 librtmp0
  libslv2-9 libsoprano4 libtotem-plparser17 libtotem0 libubuntuoneui-3.0-1
  mythes-en-us nautilus-share plasma-scriptengine-javascript python-aptdaemon
  python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat python-cupshelpers
  python-pycurl python-software-properties python-uno qapt-batch
  sessioninstaller software-center software-properties-gtk soprano-daemon
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev ubuntu-tweak whoopsie xbmc xbmc-bin
  xul-ext-ubufox
The following NEW packages will be installed:
  gcc-4.6-base:i386 libc6:i386 libgcc1:i386 libgcrypt11:i386 libgnutls26:i386
  libgpg-error0:i386 libp11-kit0:i386 librtmp0:i386 libtasn1-3:i386 python3
  python3-minimal python3.2 python3.2-minimal zlib1g:i386
0 upgraded, 14 newly installed, 94 to remove and 0 not upgraded.
Need to get 9,137 kB of archives.
After this operation, 328 MB disk space will be freed.
Do you want to continue [Y/n]?
```That seems to be an awful lot to be removed. 

So my question is, if I answer here with yes, will that break my system?

-peter

---

### Post by sandy8925 on 2012-06-16
well, it's removing a lot of stuff including xbmc, libreoffice and many kde libraries. most likely will break your system. if you have some other DE installed, this might be a good idea to do. then. reinstall whatever was removed. hopefully, the problem will be fixed then.

---

### Post by LeeJunFan on 2012-06-18
Having the same problem. Might be resolving it at this moment.

Check to see where your librtmp0 is from. I'm guessing from a dnjl ppa

apt-cache policy librtmp0

---

### Post by LeeJunFan on 2012-06-18
Yeah, mine's working now.

dpkg -r --force-all librtmp0
apt-get install librtmp0
apt-get install ia32-libs

---

### Post by slegrand on 2012-06-23
> **LeeJunFan said:**
> Yeah, mine's working now.

dpkg -r --force-all librtmp0
apt-get install librtmp0
apt-get install ia32-libs
That did not work for me. :(
```
strykekyte@strykekyte-desktop:~$ sudo dpkg -r --force-all librtmp0
dpkg: librtmp0: dependency problems, but removing anyway as you requested:
 libavformat-extra-53 depends on librtmp0 (>= 2.3).
 libcurl3 depends on librtmp0 (>= 2.3).
 gstreamer0.10-plugins-bad depends on librtmp0 (>= 2.3).
 rtmpdump depends on librtmp0 (>= 2.3).
 librtmp-dev depends on librtmp0 (= 2.4~20110711.gitc28f1bab-1).
 libcurl3-gnutls depends on librtmp0 (>= 2.3).
(Reading database ... 744970 files and directories currently installed.)
Removing librtmp0 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
strykekyte@strykekyte-desktop:~$ sudo apt-get install librtmp0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kthesaurus calligrastage calligrasheets calligraplan calligrawords create-resources qhull-bin geomview
  calligraflow-data libgeomview-1.9.4 calligraflow calligrawords-data kexi
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  librtmp0
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 57.1 kB of archives.
After this operation, 146 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ precise/main librtmp0 amd64 2.4~20110711.gitc28f1bab-1 [57.1 kB]
Fetched 57.1 kB in 0s (103 kB/s)  
Selecting previously unselected package librtmp0.
(Reading database ... 744973 files and directories currently installed.)
Unpacking librtmp0 (from .../librtmp0_2.4~20110711.gitc28f1bab-1_amd64.deb) ...
Setting up librtmp0 (2.4~20110711.gitc28f1bab-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
strykekyte@strykekyte-desktop:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.
strykekyte@strykekyte-desktop:~$ sudo apt-get install ia32-libs-multiarch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 ia32-libs-multiarch:i386 : Depends: bluez-alsa:i386 but it is not going to be installed
                            Depends: gvfs:i386 but it is not going to be installed
                            Depends: libcanberra-gtk-module:i386 but it is not going to be installed
                            Depends: libgconf-2-4:i386 but it is not going to be installed
                            Depends: libgphoto2-2:i386 but it is not going to be installed
                            Depends: libsane:i386 but it is not going to be installed
                            Suggests: libpam-ldap:i386
                            Suggests: libpam-winbind:i386 but it is not going to be installed
                            Suggests: libnss-ldap:i386
E: Unable to correct problems, you have held broken packages.

```

This is getting really frustrating. It seems that this should be listed as a notable know issue with a big warning. Wine is used by many people for a lot of different reasons and I would not be surprised if it was one of the most installed packages on Ubuntu. Breaking it with a new realease is a little wreckless. I should've held upgrading. I always upgrade and always regret it. I'm a slow learner it seems.

---

### Post by who_da_fly on 2012-08-08
The ia32libs package is no longer needed, we're now using multiarch. Just install the i386 version of the package you require.

sudo apt-get install package:i386

---

### Post by james_xxx on 2012-08-09
LeeJunFan's solution in post #10 worked for me!

Thanks!

---

### Post by Ofloo on 2012-08-14
It seems i've got the same issue only different packages, .. with precise xubuntu, ..

```
$ sudo apt-get install ia32-libs-multiarch
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
Sommige pakketten konden niet geïnstalleerd worden. Dit kan betekenen dat u
een onmogelijke situatie gevraagd hebt of dat u de 'unstable'-distributie 
gebruikt en sommige benodigde pakketten nog vastzitten in 'incoming'.
De volgende informatie helpt u mogelijk verder:

De volgende pakketten hebben niet-voldane vereisten:
 ia32-libs-multiarch:i386 : Vereisten: libglapi-mesa:i386 maar het zal niet geïnstalleerd worden
                            Vereisten: libglu1-mesa:i386 maar het zal niet geïnstalleerd worden
                            Vereisten: libqt4-opengl:i386 maar het zal niet geïnstalleerd worden
                            Aanbevelingen: libgl1-mesa-glx:i386 maar het zal niet geïnstalleerd worden
E: Kan problemen niet verhelpen, u houdt defecte pakketten vast.

```

however all the proposed fixes want to remove xubuntu-desktop and various others like xorg, .. compiz, and so forth

---

### Post by banifou on 2012-08-16
> **LeeJunFan said:**
> Yeah, mine's working now.

dpkg -r --force-all librtmp0
apt-get install librtmp0
apt-get install ia32-libs

This worked for me too!
Thanks

---

### Post by Ofloo on 2012-08-17
Nah no need, the problem went away by it self day later I got a upgrade from apt-get did it and i could install it. So the problem was with apt-get package tree it self !?

---

### Post by a.kazemi on 2012-11-22
```
dpkg -r --force-all librtmp0
apt-get install librtmp0
apt-get install ia32-libs
```

dear friends I find out somthing in my case that may be helpful for you, too.

the above commands work for someones and not work for some others like me! because for first group the issues comes out from librtmp0 and it was not appropriate version for their Ubuntu. So the first command remove just the librtmp0 and do not change other packages which are depend on it then the second command install it again but the appropriate version! and then the third one will do the last. but in other cases which the problem is not just from librtmp0 these codes doesn't work!

the solution is to find the other packages which are not the appropriate version and do the 2 first command for all of them then try to install ia32-libs! but me myself doesn't know what is the correct way to find those inappropriate version packages! but still I have an idea you can look for those packages among the dependencies which will be listed as unmet dependencies when you run this command:
```
sudo apt-get install ia32-libs-multiarch
```

try to reinstall them one by one through synaptic package manager and if one of them are inappropriate version synaptic show an error that you can see the warning detail said that the version which is installed is sth and you need to have another version installed! then for those packages try to do the two first commands:

```
dpkg -r --force-all "package name"
apt-get install "package name"
```

---

