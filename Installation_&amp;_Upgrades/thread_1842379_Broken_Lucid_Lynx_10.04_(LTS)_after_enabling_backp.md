---
title: "Broken Lucid Lynx 10.04 (LTS) after enabling backport repos"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by mue.de on 2011-09-11
Hello, 

I'm in big trouble, after i enabled backport repositories, just to get a newer version of *amarok (V2.4.0)* 
[http://forum.kde.org/viewtopic.php?f=121&t=96487](http://forum.kde.org/viewtopic.php?f=121&t=96487).
Now my loved Kubuntu Lucid Lynx (10.04 LTS) is damaged at all corners, for two weeks now i'm trying to get it working again!
If you suggest installing a new ubuntu over it, please have a look at [http://emuede.pbworks.com/](http://emuede.pbworks.com/).

Some Information on my system:
```
muelux@muelux-LT6cA:/$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
```Some Packages were lost during the re-installing:
```
muelux@muelux-LT6cA:/var/lib$ sudo dpkg --get-selections|grep "deinstall"                                                                  
festival                                        deinstall
freecad                                         deinstall
freeglut3                                       deinstall
kompozer                                        deinstall
kompozer-data                                   deinstall
ksudoku                                         deinstall
kttsd                                           deinstall
libboost-filesystem1.40.0                       deinstall
libboost-regex1.40.0                            deinstall
libboost-signals1.40.0                          deinstall
libboost-system1.40.0                           deinstall
libcoin60                                       deinstall
libdmtx0a                                       deinstall
libestools1.2                                   deinstall
libgdal1-1.6.0                                  deinstall
libgeos-3.1.0                                   deinstall
libgeos-c1                                      deinstall
libgfortran3                                    deinstall
libhdf4-0-alt                                   deinstall
libhdf5-serial-1.8.4                            deinstall
libkdegames5                                    deinstall
libnetcdf4                                      deinstall
libogdi3.2                                      deinstall
libopencascade-foundation-6.3.0                 deinstall
libopencascade-modeling-6.3.0                   deinstall
libpq5                                          deinstall
libproj0                                        deinstall
libqt4-multimedia                               deinstall
libqtwebkit4                                    deinstall
libqyoto4.5-cil                                 deinstall
libsmokesoprano3                                deinstall
libsoqt4-20                                     deinstall
libspeechd2                                     deinstall
libxerces-c28                                   deinstall
libzipios++0c2a                                 deinstall
qlandkartegt                                    deinstall
qt4-designer                                    deinstall
qt4-dev-tools                                   deinstall
showfoto                                        deinstall
skype                                           deinstall
ubufox                                          deinstall
muelux@muelux-LT6cA:/var/lib$
```Now almost everthing is running again, but i have some problems in the background:

The QDBUS seems to have a problem, i'm not notified, when i plug in an external usb-storage device, 
Kontact forgot it's certificates, in the system settings i can't open the 'Dienste' -tab (engl. services/ daemons?), all services are greyed out, the errormessage is displayed:
[ATTACH]201921[/ATTACH]

P.S. some further information
> muelux@muelux-LT6cA:/var/lib$ sudo apt-get clean
[sudo] password for muelux:                                                                                                                              
muelux@muelux-LT6cA:/var/lib$ sudo apt-get update
OK   [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg                                                                                                    
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid Release.gpg                                                                                                      
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/contrib Translation-de                                                                       
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/non-free Translation-de                                                                      
OK   [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid/main Translation-de
OK   [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-de                                                                                
OK   [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-de                                                                                
OK   [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid/universe Translation-de                                                                                  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-updates Release.gpg                                                                                              
Ign [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-de                                                                               
Ign [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-de                                                                         
Ign [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-de                                                                         
Ign [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-de                                                                           
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-security Release.gpg                                                                                             
Ign [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-de                                                                              
Ign [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-de
OK   [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release                                                                                                        
OK   [http://download.virtualbox.org](http://download.virtualbox.org) lucid/contrib Packages
OK   [http://download.virtualbox.org](http://download.virtualbox.org) lucid/non-free Packages                                                                                              
Ign [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-de                                                                        
Ign [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-de
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid Release                                                                                                          
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-updates Release
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-security Release
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/main Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/restricted Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/multiverse Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/universe Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/main Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/restricted Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid/universe Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-updates/main Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-updates/restricted Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-updates/multiverse Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-updates/universe Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-updates/main Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-updates/restricted Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-updates/universe Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-security/main Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-security/restricted Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-security/multiverse Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-security/universe Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-security/main Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-security/restricted Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) lucid-security/universe Sources
Paketlisten werden gelesen... Fertig
muelux@muelux-LT6cA:/var/lib$ sudo apt-get upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
muelux@muelux-LT6cA:/var/lib$ 

I can't get these problems solved allone
](*,)

---

### Post by mue.de on 2011-09-16
[SIZE=3]Hello, couldn't somewone have a look at this problem?
[/SIZE]
here's a short summary:

[SIZE=3]The Main Problem arised after:
 * The Kubuntu Lucid Lynx repo has as newest Amarok-Version the V2.3.0 available
 * against my fears i followed a tip (of an KDE-Developer!) and tried to install the newest Amarok-Version from a **backport** repository 
 * I hit (in the oppinion of the mentor) the wrong ppa, so i tried to change it to *Lucid Lynx * backports and reinstall the new Amarok Version from there
 * The reinstalling failed (-my Lucid Lynx was still running fine-) and following another tip i tried as a terminal-command [/SIZE]
```
sudo apt-get -f install amarok 

``` * [SIZE=3]**That implied the whole bunch of changes (22 updates, 153 security updates from the backport repository** [/SIZE]for *Lucid Lynx*) and from that point on the [SIZE=3]**system wasn't unusable**![/SIZE]

After three weeks of struggling the system is now** almost running again** (with Amarok 2.3.0, so everything was senseless!) 
The Main Error is an QDBUS-Problem (the services are greyed out in the system settings, i get the message 'Kein Kontakt zu KDED' !?
KMail asks at every start for the certificate to be accepted.

Any advice appreciated !

---

### Post by mue.de on 2011-10-23
So i still can't use Lucid Lynx as a stable operating system, it's only good for 'playstation'.
After 10 years of trial and error i think the time has come to go back solving the real problems instead of messing around with such an experimental operating system.
I don't have on line of code running on the avr-processor, trying with eclipse and burn-o-mat, while a friend of mine is miles away (on the real problems) with WinAVR. OpenOffice (LibreOffice) does always a stupid Open as Text-File when i try to import Excel or Access-Sheets, i even don't try to import my macros or visual basic routines from excel. I can't compare files on different sources (Stick and home-directory) with diff or diff3 as i could do with filesync. I still can't use Amarok as i could use Silverjuke and so on....
So what is Linux good for ?
To spend thousands of hours struggling with the system instead of solving real problems !

---

