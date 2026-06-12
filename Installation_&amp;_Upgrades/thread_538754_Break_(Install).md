---
title: "Break (Install)"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by opticyclic on 2007-08-30
I hadn't used my Linux installation for quite a whils so wasn't surprised that there were ~100 upgrades available when I ran the adept update tool.
Unfortunately it seems to have removed kdm and a couple of other packages.
Now when I try to reinstall them I get the message Break (install).

Running Synaptic gives me a bit more info :
```
kdm:
  Depends: kdebase-bin (=4:3.5.6-0ubuntu20.2) but 4:3.5.7-0ubuntu1~feisty1 is to be installed
  Depends: kdebase-data (<4:3.5.7) but 4:3.5.7-0ubuntu1~feisty1 is to be installed
```

Running sudo aptitude install kdm from the konsole gives the following output.
```
~$ sudo aptitude install kdm
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  kdm
The following packages are unused and will be REMOVED:
  adept adept-batch adept-installer adept-manager akregator amarok
  amarok-xine ark arts digikam gwenview hwdb-client-kde k3b kaffeine
  kaffeine-xine karm katapult kate kbstate kcron kde-guidance
  kde-guidance-powermanager kde-icons-mono kdeadmin-kfile-plugins
  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdnssd keep kfind khelpcenter
  kio-apt kio-locate kipi-plugins kitchensync klipper kmag kmailcvt
  kmenuedit kmilo kmix kmousetool kmplayer-base knetworkconf knotes
  konqueror-nsplugins kontact konversation kooka kopete korganizer kpf kppp
  krdc krfb kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksysguard
  ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-docs
  kwin-style-crystal language-selector-qt libavahi-compat-libdnssd1
  libflac++5c2 libgmp3c2 libifp4 libimlib2 libjasper-runtime libjpeg-progs
  libk3b2 libkipi0 libkpimexchange1 libkscan1 liblockdev1 libnjb5
  libpoppler1-qt libpythonize0 libqt4-qt3support libqt4-sql librsync1
  libskim0 libsqlite0 openoffice.org-kde poster psutils pykdeextensions
  python-kde3 qca-tls qobex rdiff-backup scim-qtimm skim speedcrunch
  vorbis-tools
The following packages have been automatically kept back:
  libemeraldengine0
0 packages upgraded, 1 newly installed, 105 to remove and 1 not upgraded.
Need to get 652kB of archives. After unpacking 284MB will be freed.
The following packages have unmet dependencies:
  kdm: Depends: kdebase-bin (= 4:3.5.6-0ubuntu20.2) but 4:3.5.7-0ubuntu1~feisty1 is installed.
       Depends: kdebase-data (< 4:3.5.7) but 4:3.5.7-0ubuntu1~feisty1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
kdebase-bin [4:3.5.7-0ubuntu1~feisty1 (<NULL>, now) -> 4:3.5.6-0ubuntu20.2
(feisty-security, feisty-security)]
kdebase-data [4:3.5.7-0ubuntu1~feisty1 (<NULL>, now) -> 4:3.5.6-0ubuntu20.2
(feisty-security, feisty-security)]
kdesktop [4:3.5.7-0ubuntu1~feisty1 (<NULL>, now) -> 4:3.5.6-0ubuntu20.2
(feisty-security, feisty-security)]
kicker [4:3.5.7-0ubuntu1~feisty1 (<NULL>, now) -> 4:3.5.6-0ubuntu20.2
(feisty-security, feisty-security)]

Score is -70

Accept this solution? [Y/n/q/?] 
```
It is wanting to remove all my KDE apps.
Is there anyway to downgrade the necessary packages to fix the dependencies without removing all those packages?
```
sudo dpkg --configure -a
``` is no use, neither is the 'Fix broken packages' command in Synaptic.

---

### Post by opticyclic on 2007-09-01
Couldn't work out what to do so I upgraded to Gutsy and the problem went away :-?

---

### Post by Seisen on 2007-09-01
Can you post your source list and what version of Ubuntu are you using?

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by opticyclic on 2007-09-03
The list has changed since I upgraded from Feisty to Gutsy.

---

### Post by of_darkness on 2007-09-06
> **opticyclic said:**
> I hadn't used my Linux installation for quite a whils so wasn't surprised that there were ~100 upgrades available when I ran the adept update tool.
Unfortunately it seems to have removed kdm and a couple of other packages.
Now when I try to reinstall them I get the message Break (install).

Running Synaptic gives me a bit more info :
```
kdm:
  Depends: kdebase-bin (=4:3.5.6-0ubuntu20.2) but 4:3.5.7-0ubuntu1~feisty1 is to be installed
  Depends: kdebase-data (<4:3.5.7) but 4:3.5.7-0ubuntu1~feisty1 is to be installed
```

Running sudo aptitude install kdm from the konsole gives the following output.
```
~$ sudo aptitude install kdm
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  kdm
The following packages are unused and will be REMOVED:
  adept adept-batch adept-installer adept-manager akregator amarok
  amarok-xine ark arts digikam gwenview hwdb-client-kde k3b kaffeine
  kaffeine-xine karm katapult kate kbstate kcron kde-guidance
  kde-guidance-powermanager kde-icons-mono kdeadmin-kfile-plugins
  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdnssd keep kfind khelpcenter
  kio-apt kio-locate kipi-plugins kitchensync klipper kmag kmailcvt
  kmenuedit kmilo kmix kmousetool kmplayer-base knetworkconf knotes
  konqueror-nsplugins kontact konversation kooka kopete korganizer kpf kppp
  krdc krfb kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksysguard
  ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-docs
  kwin-style-crystal language-selector-qt libavahi-compat-libdnssd1
  libflac++5c2 libgmp3c2 libifp4 libimlib2 libjasper-runtime libjpeg-progs
  libk3b2 libkipi0 libkpimexchange1 libkscan1 liblockdev1 libnjb5
  libpoppler1-qt libpythonize0 libqt4-qt3support libqt4-sql librsync1
  libskim0 libsqlite0 openoffice.org-kde poster psutils pykdeextensions
  python-kde3 qca-tls qobex rdiff-backup scim-qtimm skim speedcrunch
  vorbis-tools
The following packages have been automatically kept back:
  libemeraldengine0
0 packages upgraded, 1 newly installed, 105 to remove and 1 not upgraded.
Need to get 652kB of archives. After unpacking 284MB will be freed.
The following packages have unmet dependencies:
  kdm: Depends: kdebase-bin (= 4:3.5.6-0ubuntu20.2) but 4:3.5.7-0ubuntu1~feisty1 is installed.
       Depends: kdebase-data (< 4:3.5.7) but 4:3.5.7-0ubuntu1~feisty1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
kdebase-bin [4:3.5.7-0ubuntu1~feisty1 (<NULL>, now) -> 4:3.5.6-0ubuntu20.2
(feisty-security, feisty-security)]
kdebase-data [4:3.5.7-0ubuntu1~feisty1 (<NULL>, now) -> 4:3.5.6-0ubuntu20.2
(feisty-security, feisty-security)]
kdesktop [4:3.5.7-0ubuntu1~feisty1 (<NULL>, now) -> 4:3.5.6-0ubuntu20.2
(feisty-security, feisty-security)]
kicker [4:3.5.7-0ubuntu1~feisty1 (<NULL>, now) -> 4:3.5.6-0ubuntu20.2
(feisty-security, feisty-security)]

Score is -70

Accept this solution? [Y/n/q/?] 
```
It is wanting to remove all my KDE apps.
Is there anyway to downgrade the necessary packages to fix the dependencies without removing all those packages?
```
sudo dpkg --configure -a
``` is no use, neither is the 'Fix broken packages' command in Synaptic.
As you se in the depndency message it is depending on a diffrent version, that comes with using 3 party repos -specialy debian repos who is 1or 2 versions before the stable ubuntu repo.

What you nead 2 do is 2 manuly go through the the unmet depndancys n force a diffrent version in either synptic or aptitude then you should be able 2 uppgrade again.

---

### Post by utkjamie on 2007-09-06
I've got a similar problem. Even though I keep my software up-to-date, last night I had over 100 packages ready to be upgraded. I made the upgrades and now I am getting "could not find mime type application/octet-stream" errors when I attempt to use Kontact and Adept_Manager. I expect that the problem is widespread throughout my system.  Any idea what's going on?

UPDATE: Scratch this. A quick reboot seems to have cleared the problem up. After 8 months without Windows XP, I've already gotten used to not having to reboot after every upgrade or software patch.

---

