---
title: "adept wont download"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by kubuman on 2007-03-12
hi...i'm new to the linux world and i'm trying to make the most out of it....
recently i installed the new kubuntu 6.10 edgy, and after some hard work also managed to get my wireless usb adapter (Alcatel speedtouch 120g) working.....
konqueror worked finebut, but when i came to get some updates, Adept package manager would get stuck at "WAITING FOR HEADERS 0%", and after a while just close....
i searched the linux forums for some guidence, and edited my sources.list file with the help of  "www.ubuntu-nl.org/source-o-matic/" ......i also configured my modem/router to forward the required ports......after all of this adept showed a message (at the bottom right corner of the screen) telling me i had some 86 new updates/upgrades available but when i clicked the "apply changes" button, it just stayed stuck at "WAITING FOR HEADERS 0%" and didnt download anything ....

please help me cuz this is frustrating....

my router is a Aztec 600ew with firewall and NAT working...

---

### Post by Kateikyoushi on 2007-03-12
Copy these commands to the terminal and show us their output.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by kubuman on 2007-03-12
message from command    "sudo aptitude update":
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?

and from "sudo aptitude upgrade":

Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-generic
The following packages have been kept back:
  kopete linux-headers-generic
The following packages will be upgraded:
  akregator ark arts avahi-daemon bind9-host dbus dnsutils gnupg info kaddressbook kamera karm kate kaudiocreator kbstate kcontrol kcron kde-icons-mono kdeadmin-kfile-plugins
  kdebase-bin kdebase-data kdebase-kio-plugins kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd kfind kghostview khelpcenter kicker klipper kmag kmail
  kmailcvt kmenuedit kmilo kmix kmousetool knetworkconf knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact kooka korganizer kpdf kpf
  kppp krdc krfb krita krita-data kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksysguardd kwalletmanager kwin libarts1-akode libarts1c2a libartsc0
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1 libavahi-core4 libavahi-qt3-1 libbind9-0 libdbus-1-3 libdns21 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libimlib2 libisc11 libisccc0 libisccfg1 libkcal2b libkcddb1 libkdepim1a libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkrb53
  libkscan1 libksieve0 libktnef1 liblwres9 libmagick++9c2a libmagick9 libmimelib1c2a libpng12-0 libpoppler1 libpoppler1-qt libpq4 libruby1.8 libsmbclient libxine1
  linux-generic linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic linux-image-2.6.17-10-generic linux-libc-dev linux-restricted-modules-2.6.17-10-generic
  linux-restricted-modules-common poppler-utils ruby1.8 samba-common screen slocate smbclient tar tcpdump w3m xserver-xorg-core
136 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 187MB of archives. After unpacking 24.3MB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  kpdf libgtk2.0-common krdc krfb libarts1c2a kscd kppp libktnef1 krita-data kdelibs4c2a libartsc0 libmagick9 libkscan1 kdeprint libisccc0 ksvg kscreensaver bind9-host kwin
  libbind9-0 libavahi-compat-libdnssd1 smbclient ksnapshot kooka kcontrol avahi-daemon libkcal2b dnsutils libmagick++9c2a libavahi-common-data libdbus-1-3
  kdegraphics-kfile-plugins konqueror-nsplugins kdelibs-data kdebase-data libpoppler1-qt kdepim-kio-plugins libarts1-akode libdns21 screen krita libmimelib1c2a klipper
  kdemultimedia-kio-plugins kontact kdeadmin-kfile-plugins kicker ksmserver ksysguard koffice-data libkcddb1 linux-libc-dev kde-icons-mono xserver-xorg-core libsmbclient
  kmenuedit linux-restricted-modules-2.6.17-10-generic libkrb53 tcpdump ksplash linux-image-2.6.17-10-generic ruby1.8 libkleopatra1 konsole korganizer
  kdenetwork-kfile-plugins kdebase-kio-plugins kbstate akregator dbus arts kamera ark kcron libkonq4 libavahi-qt3-1 libisccfg1 libgtk2.0-bin libksieve0 kfind kdebase-bin kdm
  linux-restricted-modules-common libkpimidentities1 libpoppler1 kpf w3m libkdepim1a kdnssd kghostview kdemultimedia-kfile-plugins kdenetwork-filesharing knotes tar
  khelpcenter kdesktop konqueror kaddressbook libkpimexchange1 liblwres9 kmailcvt knetworkconf libpng12-0 ksysguardd konq-plugins libkmime2 libavahi-client3 poppler-utils
  slocate libpq4 linux-headers-2.6.17-10 kwalletmanager samba-common karm kate kmail libruby1.8 libisc11 info koffice-libs libimlib2 libavahi-common3 linux-generic
  libavahi-core4 kmousetool libgtk2.0-0 kmag kdepim-kresources kdepim-wizards kmilo kaudiocreator linux-headers-2.6.17-10-generic gnupg kdepasswd kmix libxine1

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?

---

### Post by Kateikyoushi on 2007-03-12
I think adept is still running, reboot and try the same comands again.

---

### Post by kubuman on 2007-03-13
reboot did help, but this what i got from the commands now
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
Err [http://kubuntu.org](http://kubuntu.org) edgy Release.gpg
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Connection failed
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg
  Connection failed
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release.gpg
  Connection failed
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy Release.gpg
  Connection failed [IP: 32.1.64.168 80]
Err [http://media.blutkind.org](http://media.blutkind.org) edgy Release.gpg
  Connection failed
Err [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) edgy-seveas Release.gpg
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main Translation-en_US
  Connection failed
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US
  Connection failed
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy/main Translation-en_US
  Connection failed [IP: 32.1.64.168 80]
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Translation-en_US
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
  Connection failed
Err [http://media.blutkind.org](http://media.blutkind.org) edgy/main-edgy Translation-en_US
  Connection failed
Err [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) edgy-seveas/all Translation-en_US
  Connection failed
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Translation-en_US
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
  Connection failed
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release
Err [http://kubuntu.org](http://kubuntu.org) edgy Release.gpg
  Connection failed
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy/restricted Translation-en_US
  Connection failed [IP: 32.1.64.168 80]
Ign [http://media.blutkind.org](http://media.blutkind.org) edgy Release
Ign [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) edgy-seveas Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
  Connection failed
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy/universe Translation-en_US
  Connection failed [IP: 32.1.64.168 80]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Err [http://kubuntu.org](http://kubuntu.org) edgy/main Translation-en_US
  Connection failed
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Ign [http://media.blutkind.org](http://media.blutkind.org) edgy/main-edgy Packages
Ign [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) edgy-seveas/all Packages
Hit [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) edgy-seveas/all Packages
Err [http://media.blutkind.org](http://media.blutkind.org) edgy/main-edgy Packages
  404 Not Found
Ign [http://kubuntu.org](http://kubuntu.org) edgy Release
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy/multiverse Translation-en_US
  Connection failed [IP: 32.1.64.168 80]
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
  Connection failed
Ign [http://kubuntu.org](http://kubuntu.org) edgy Release
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates Release.gpg
  Connection failed [IP: 32.1.64.168 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates/main Translation-en_US
  Connection failed [IP: 32.1.64.168 80]
Ign [http://kubuntu.org](http://kubuntu.org) edgy/main Packages
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
  Connection failed [IP: 32.1.64.168 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Ign [http://kubuntu.org](http://kubuntu.org) edgy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) edgy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) edgy/main Packages
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates/universe Translation-en_US
  Connection failed [IP: 32.1.64.168 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
  Connection failed [IP: 32.1.64.168 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports Release.gpg
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports/main Translation-en_US
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports/universe Translation-en_US
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
  Connection failed [IP: 32.1.64.168 80]
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy Release
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates Release
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports Release
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy/main Packages
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy/restricted Packages
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy/universe Packages
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy/multiverse Packages
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates/main Packages
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates/universe Packages
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates/multiverse Packages
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports/main Packages
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports/restricted Packages
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports/universe Packages
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports/multiverse Packages
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy/main Packages
  504 Gateway Timeout [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy/restricted Packages
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy/universe Packages
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy/multiverse Packages
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates/main Packages
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates/restricted Packages
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates/universe Packages
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-updates/multiverse Packages
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports/main Packages
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports/restricted Packages
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports/universe Packages
  Connection failed [IP: 32.1.64.168 80]
Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) edgy-backports/multiverse Packages
  Connection failed [IP: 32.1.64.168 80]
Reading package lists... Done


and for sudo aptitude updgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-generic
The following packages have been kept back:
  kopete linux-headers-generic
The following packages will be upgraded:
  akregator ark arts avahi-daemon bind9-host dbus dnsutils gnupg info kaddressbook kamera karm kate kaudiocreator kbstate kcontrol kcron kde-icons-mono kdeadmin-kfile-plugins
  kdebase-bin kdebase-data kdebase-kio-plugins kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd kfind kghostview khelpcenter kicker klipper kmag kmail
  kmailcvt kmenuedit kmilo kmix kmousetool knetworkconf knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact kooka korganizer kpdf kpf
  kppp krdc krfb krita krita-data kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksysguardd ktorrent kwalletmanager kwin libarts1-akode libarts1c2a libartsc0
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1 libavahi-core4 libavahi-qt3-1 libbind9-0 libdbus-1-3 libdns21 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libimlib2 libisc11 libisccc0 libisccfg1 libkcal2b libkcddb1 libkdepim1a libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkrb53
  libkscan1 libksieve0 libktnef1 liblwres9 libmagick++9c2a libmagick9 libmimelib1c2a libpng12-0 libpoppler1 libpoppler1-qt libpq4 libruby1.8 libsmbclient libxine1
  linux-generic linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic linux-image-2.6.17-10-generic linux-libc-dev linux-restricted-modules-2.6.17-10-generic
  linux-restricted-modules-common poppler-utils ruby1.8 samba-common screen slocate smbclient tar tcpdump w3m xserver-xorg-core
137 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 188MB of archives. After unpacking 24.3MB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  kpdf libgtk2.0-common krdc krfb libarts1c2a kscd kppp libktnef1 krita-data kdelibs4c2a libartsc0 libmagick9 libkscan1 kdeprint libisccc0 ksvg kscreensaver bind9-host kwin
  libbind9-0 libavahi-compat-libdnssd1 smbclient ksnapshot kooka kcontrol avahi-daemon libkcal2b dnsutils libmagick++9c2a libavahi-common-data libdbus-1-3
  kdegraphics-kfile-plugins konqueror-nsplugins kdelibs-data kdebase-data libpoppler1-qt kdepim-kio-plugins libarts1-akode libdns21 screen krita libmimelib1c2a klipper
  kdemultimedia-kio-plugins kontact kdeadmin-kfile-plugins kicker ksmserver ksysguard koffice-data libkcddb1 linux-libc-dev kde-icons-mono xserver-xorg-core libsmbclient
  kmenuedit linux-restricted-modules-2.6.17-10-generic libkrb53 tcpdump ksplash linux-image-2.6.17-10-generic ruby1.8 libkleopatra1 konsole korganizer
  kdenetwork-kfile-plugins kdebase-kio-plugins kbstate akregator dbus arts kamera ark kcron libkonq4 libavahi-qt3-1 libisccfg1 libgtk2.0-bin libksieve0 kfind kdebase-bin kdm
  linux-restricted-modules-common libkpimidentities1 libpoppler1 kpf w3m libkdepim1a kdnssd kghostview kdemultimedia-kfile-plugins kdenetwork-filesharing knotes tar
  khelpcenter kdesktop konqueror kaddressbook libkpimexchange1 liblwres9 kmailcvt knetworkconf libpng12-0 ksysguardd konq-plugins libkmime2 libavahi-client3 poppler-utils
  slocate ktorrent libpq4 linux-headers-2.6.17-10 kwalletmanager samba-common karm kate kmail libruby1.8 libisc11 info koffice-libs libimlib2 libavahi-common3 linux-generic
  libavahi-core4 kmousetool libgtk2.0-0 kmag kdepim-kresources kdepim-wizards kmilo kaudiocreator linux-headers-2.6.17-10-generic gnupg kdepasswd kmix libxine1

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main tar 1.15.91-2ubuntu0.3
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libartsc0 1.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libarts1c2a 1.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main screen 4.0.2-4.1ubuntu5.6.10
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdelibs4c2a 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main gnupg 1.4.3-2ubuntu3.3
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libisc11 1:9.3.2-2ubuntu3.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdelibs-data 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libdns21 1:9.3.2-2ubuntu3.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libktnef1 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libisccc0 1:9.3.2-2ubuntu3.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libkcal2b 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libisccfg1 1:9.3.2-2ubuntu3.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libkdepim1a 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libbind9-0 1:9.3.2-2ubuntu3.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main akregator 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main liblwres9 1:9.3.2-2ubuntu3.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main ark 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main bind9-host 1:9.3.2-2ubuntu3.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main arts 1.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main dnsutils 1:9.3.2-2ubuntu3.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libkleopatra1 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kaddressbook 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main info 4.8.dfsg.1-1ubuntu0.1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libkrb53 1.4.3-9ubuntu1.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kamera 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main tcpdump 3.9.4-4ubuntu0.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main karm 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main w3m 0.5.1-4ubuntu2.6.10
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kate 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libpng12-0 1.2.8rel-5.1ubuntu0.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libkcddb1 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libavahi-common-data 0.6.13-2ubuntu2.4
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kaudiocreator 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libavahi-common3 0.6.13-2ubuntu2.4
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdemultimedia-kio-plugins 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libdbus-1-3 0.93-0ubuntu3.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kbstate 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libavahi-client3 0.6.13-2ubuntu2.4
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libkonq4 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libavahi-qt3-1 0.6.13-2ubuntu2.4
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kicker 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libavahi-core4 0.6.13-2ubuntu2.4
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main ksplash 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main dbus 0.93-0ubuntu3.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdm 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main avahi-daemon 0.6.13-2ubuntu2.4
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main konqueror 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libsmbclient 3.0.22-1ubuntu4.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kcontrol 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libpoppler1-qt 0.5.4-0ubuntu4.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdebase-data 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libpoppler1 0.5.4-0ubuntu4.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdesktop 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libruby1.8 1.8.4-5ubuntu1.2
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdebase-bin 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libavahi-compat-libdnssd1 0.6.13-2ubuntu2.4
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdebase-kio-plugins 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main ktorrent 2.0.3+dfsg1-0ubuntu1.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kfind 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libgtk2.0-common 2.10.6-0ubuntu3.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kcron 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libgtk2.0-bin 2.10.6-0ubuntu3.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kde-icons-mono 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libgtk2.0-0 2.10.6-0ubuntu3.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdeadmin-kfile-plugins 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libimlib2 1.2.1-2ubuntu1.2
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdegraphics-kfile-plugins 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmagick9 7:6.2.4.5.dfsg1-0.10ubuntu0.2
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdemultimedia-kfile-plugins 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libmagick++9c2a 7:6.2.4.5.dfsg1-0.10ubuntu0.2
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdenetwork-filesharing 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libpq4 8.1.8-0ubuntu6.10
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdenetwork-kfile-plugins 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libxine1 1.1.2+repacked1-0ubuntu3.4
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdepasswd 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted linux-generic 2.6.17.11
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libkmime2 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main linux-headers-2.6.17-10 2.6.17.1-10.34
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdepim-kio-plugins 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main linux-headers-2.6.17-10-generic 2.6.17.1-10.34
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdepim-kresources 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main linux-image-2.6.17-10-generic 2.6.17.1-10.34
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libkpimidentities1 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main linux-libc-dev 2.6.17.1-11.35
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdepim-wizards 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted linux-restricted-modules-common 2.6.17.7-11.2
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdeprint 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted linux-restricted-modules-2.6.17-10-generic 2.6.17.7-10.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kdnssd 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main poppler-utils 0.5.4-0ubuntu4.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kghostview 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main ruby1.8 1.8.4-5ubuntu1.2
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main khelpcenter 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main smbclient 3.0.22-1ubuntu4.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main klipper 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main samba-common 3.0.22-1ubuntu4.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kmag 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main xserver-xorg-core 1:1.1.1-0ubuntu12.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libksieve0 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main slocate 3.1-1ubuntu0.1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libmimelib1c2a 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kmail 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kmailcvt 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kmenuedit 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kmilo 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kmix 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kmousetool 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main knetworkconf 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main knotes 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main krita 1:1.6.2-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main krita-data 1:1.6.2-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main koffice-libs 1:1.6.2-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main koffice-data 1:1.6.2-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main konq-plugins 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main konqueror-nsplugins 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main konsole 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libkpimexchange1 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main korganizer 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kontact 4:3.5.6-0ubuntu2~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libkscan1 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kooka 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kpdf 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kpf 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kppp 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main krdc 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main krfb 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kscd 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kscreensaver 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main ksmserver 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kwin 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main ksnapshot 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main ksvg 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main ksysguard 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main ksysguardd 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main kwalletmanager 4:3.5.6-0ubuntu1~edgy1
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) edgy/main libarts1-akode 4:3.5.6-0ubuntu1~edgy1
  Connection failed

---

### Post by Kateikyoushi on 2007-03-13
Can you use the net ? Browser, email client works ?

```
ping google.com
```

---

### Post by kubuman on 2007-03-13
browse works fine, all the sites i try work...the only thing that wont work is the adept

---

### Post by kubuman on 2007-04-09
well....i installed the new 7.04 feisty fawn beta....after some tweaking i also managed to install and configure my usb wfif card and the internet works fine.
i launched apt and let it work.... the first time nothing happened....but the next day i got a message that there are a good hundered of upgrades awaiting me...i let apt "apply changes" and let it work. came back a few hours later and it was still stuck at "waiting for headers 0%"
next thing i tried was sudu aptitude update...all i got were error messages of failing to connect.
i haven't tweaked the sources.list file since i'm not sure if any of the old (edgy) solutions work on feisty

---

### Post by robenroute on 2007-04-13
Could you try to connect your PC to your modem/router with a wire (thus bypassing the wireless stuff). See what happens then.

---

### Post by Nibes on 2008-02-12
I have the same problem but with kubuntu 7.10. Adept manager still waiting for headers sometimes at 26% other at 0% other even at 35%. but It can't load the repositories. 
I managed the sources.list and nothing. 

The web is working fine. mail and other stuff. (Open office doesn't work too.) 

The first time i noticed this was during the instalation of kubuntu when It was trying to connect to the security upgrades. near the 86 or 82% of the instalation progress. 

I think it may be a bad Live CD. I checkd the cd with the main instalation menu. and it was ok. I checkd the Md5sum before burning the iso and it was also correct. So my hipotesis of a bad Live CD could be wrong. 

But something is going on that's for sure. Now without more time to waste with the Kubuntu  I am downloading the Ubuntu Gutsy Gibbon Live CD and I will install it over the Kubuntu. Hoping it works. And I am pretty sure it will work. 

Anyway if there is a solution for the Adept Manager problem or The office beside the re-instalation of a new Os I would apreciate the news about it. Many thanx. 

P.S. Once in another computer I installed Kubuntu along with Ubuntu and the sistem also crashed. Broken circle I guess. hehe

---

