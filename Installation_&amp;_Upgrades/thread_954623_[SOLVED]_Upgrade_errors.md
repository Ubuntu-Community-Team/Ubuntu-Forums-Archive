---
title: "[SOLVED] Upgrade errors"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by Mariane on 2008-10-21
Hi, 

I did 
sudo apt-get update, went fine
sudo apt-get upgrade, got errors:

Preconfiguring packages ...
(Reading database ...
dpkg: serious warning: files list file for package `x11proto-input-dev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `dmidecode' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `system-services' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `apparmor-utils' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/sun-java6-plugin_6-07-3ubuntu2_i386.deb (--unpack):
 files list file for package `cabextract' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-plugin_6-07-3ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


I retried, and I also tried to remove and reinstall the problematic packages. At one point I was told by the terminal to do:

sudo dpkg --configure -a

So I did it and it seemed to take me a step further. But When I retried update an upgrade it did exactly the same. 

What should I do, please? 

Mariane

---

### Post by Pumalite on 2008-10-21
Try:
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Mariane on 2008-10-22
The first 2 went fine but the last one failed. I post the error below, still the same cabextract with a missing newline at the end, apparently... Pasted below.

I'll try to boot from the ubuntu cd and see if I manage to do anything... 

I found the cabextract file in usr/bin but when I opened it it was a binary file and I got the message "Saving it will result in a corrupted file". Otherwse I would have added the <***> newline at the end of the file, if it's simply that which is causing the problem... 

Mariane 


tux@tux-laptop:/usr/bin$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  linux-headers-2.6.24-21 linux-headers-2.6.24-21-generic
  linux-image-2.6.24-21-generic linux-restricted-modules-2.6.24-21-generic
  linux-ubuntu-modules-2.6.24-21-generic
The following packages will be upgraded:
  akregator amor ark arts artsbuilder atlantik atlantikdesigner blinken cupsys
  cupsys-bsd cupsys-client cupsys-common dbus dbus-x11 dcoprss eyesapplet
  fifteenapplet gstreamer0.10-tools hal-info indi jockey-common jockey-gtk juk
  kaboodle kaddressbook kaddressbook-plugins kalarm kalzium kalzium-data
  kamera kanagram kandy kappfinder karm kasteroids kate kate-plugins katomic
  kaudiocreator kbackgammon kbattleship kblackbox kbounce kbruch kbstate kcalc
  kcharselect kcoloredit kcontrol kcron kdat kdeaccessibility kdeaddons
  kdeaddons-kfile-plugins kdeadmin kdeadmin-kfile-plugins kdebase kdebase-bin
  kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdeedu kdeedu-data
  kdegames kdegames-card-data kdegraphics kdegraphics-kfile-plugins kdelibs
  kdelibs-data kdelibs4c2a kdelirc kdemultimedia kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork
  kdenetwork-kfile-plugins kdepasswd kdepim kdepim-kfile-plugins
  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdessh
  kdetoys kdeutils kdewebdev kdf kdict kdnssd kdvi kedit keduca kenolaba kfax
  kfaxview kfilereplace kfind kfloppy kfouleggs kgamma kgeography
  kgeography-data kget kghostview kgoldrunner kgpg khangman khelpcenter
  khexedit kicker kicker-applets kiconedit kig kimagemapeditor kitchensync
  kiten kjots kjumpingcube klaptopdaemon klatin kleopatra klettres
  klettres-data klickety klines klinkstatus klipper kmag kmahjongg kmail
  kmailcvt kmenuedit kmid kmilo kmines kmix kmoon kmousetool kmouth kmplot
  kmrml knetwalk knetworkconf knewsticker knode knotes kodo kolf kolourpaint
  kommander konq-plugins konqueror konqueror-nsplugins konquest konsole
  konsolekalendar kontact kooka kopete korganizer korn kpackage kpager kpat
  kpdf kpercentage kpersonalizer kpf kpilot kpoker kpovmodeler kppp krdc krec
  kregexpeditor kreversi krfb kruler ksame ksayit kscd kshisen ksig ksim ksirc
  ksirtet ksmiletris ksmserver ksnake ksnapshot ksokoban kspaceduel ksplash
  kstars kstars-data ksvg ksysguard ksysguardd ksysv kteatime ktimer ktip
  ktnef ktouch ktron kttsd ktuberling kturtle ktux kuser kverbos kview
  kviewshell kvoctrain kwalletmanager kweather kwifimanager kwin kwin4
  kwordquiz kworldclock kxsldbg libarts1-akode libarts1-audiofile
  libarts1-mpeglib libarts1-xine libarts1c2a libartsc0 libcupsimage2
  libcupsys2 libcupsys2-dev libcvsservice0 libdbus-1-3 libexif12
  libgstreamer0.10-0 libindex0 libkcal2b libkcddb1 libkdeedu3 libkdegames1
  libkdepim1a libkgantt0 libkiten1 libkleopatra1 libkmime2 libkonq4
  libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1
  libmimelib1c2a librss1 linux-generic linux-headers-generic
  linux-image-generic linux-libc-dev linux-restricted-modules-common
  linux-restricted-modules-generic lskat mpeglib networkstatus noatun
  noatun-plugins nvidia-glx-new quanta quanta-data sun-java6-bin sun-java6-jre
  sun-java6-plugin superkaramba tzdata
275 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 51.3MB/260MB of archives.
After this operation, 197MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main linux-image-2.6.24-21-generi
c 2.6.24-21.42 [18.4MB]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main linux-ubuntu-modules-2.6.24-
21-generic 2.6.24-21.32 [5429kB]
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted linux-generic 2.6.24.2
1.23 [26.5kB]
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main linux-image-generic 2.6.24.2
1.23 [26.5kB]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted linux-restricted-modul
es-2.6.24-21-generic 2.6.24.14-21.51 [18.6MB]
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted linux-restricted-modul
es-generic 2.6.24.21.23 [26.5kB]
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main linux-headers-2.6.24-21 2.6.
24-21.42 [8134kB]
Get: 8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main linux-headers-2.6.24-21-gene
ric 2.6.24-21.42 [647kB]
Get: 9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main linux-headers-generic 2.6.24
.21.23 [26.5kB]
Fetched 51.3MB in 2min16s (376kB/s)
debconf: Unable to initialise frontend: Dialog
debconf: (Dialogue frontend requires a screen at least 13 lines tall and 31 colu
mns wide.)
debconf: falling back to frontend: Readline
Extract templates from packages: 100%
Preconfiguring packages ...
Selecting previously deselected package linux-image-2.6.24-21-generic.
(Reading database ...
dpkg: serious warning: files list file for package `x11proto-input-dev' missing,
 assuming package has no files currently installed.

dpkg: serious warning: files list file for package `dmidecode' missing, assuming
 package has no files currently installed.

dpkg: serious warning: files list file for package `system-services' missing, as
suming package has no files currently installed.

dpkg: serious warning: files list file for package `apparmor-utils' missing, ***                            uming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-21-generic_2.6                            .24-21.42_i386.deb (--unpack):
 files list file for package `cabextract' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-21-generic_2.6.24-21.42_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Mariane on 2008-10-22
The files <packagename>.list are in 
/var/lib/dpkg/info/

I took one which was alright: not binary and not empty, 
it contained:

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/x11proto-fixes-dev
/usr/share/doc/x11proto-fixes-dev/copyright
/usr/share/doc/x11proto-fixes-dev/changelog.Debian.gz
/usr/include
/usr/include/X11
/usr/include/X11/extensions
/usr/include/X11/extensions/xfixesproto.h
/usr/include/X11/extensions/xfixeswire.h
/usr/lib
/usr/lib/pkgconfig
/usr/lib/pkgconfig/fixesproto.pc
      <- This is part of the file: a new line at the end

I copied it (as root) as replacement for all the .list files which were either giving an error message (such as missing newline) or which were missing. As soon as I copied one I removed WITH PURGE the corresponding package and reinstalled it. So this would be:

Suppose the file causing trouble is called problematic.list and my example above, with a newline at the end, is goodExample.list

cd /var/lib/dpkg/info/
sudo cp goodExample.list problematic.list
sudo apt-get remove --purge problematic
sudo apt-get install problematic

For all the problematic .list files. 

Finally, this had removed or lost the package corresponding to goodExample so I did 

sudo apt-get install goodExample

WARNING: When you do a "sudo apt-get remove" it can tell you a list of packages which will also be removed because they depend upon the package you are removing. Read this list. If you see anything which either you know you'll need or you are unsure about, write its name down and reinstall it also. Once I was trying to fix a Fedora with yum ("yum" is Fedora's way of saying "apt-get") and I nearly removed yum itself by mistake. 

Mariane

---

