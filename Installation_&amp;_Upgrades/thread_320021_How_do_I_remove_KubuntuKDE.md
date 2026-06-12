---
title: "How do I remove Kubuntu/KDE?"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by Old Pink on 2006-12-16
Hi there, 

I'm a long time GNOME user, and thought that KDE was worth a try after some people on here sang it's praises. So, I opened synaptic, installed kubuntu-desktop, agreed to all the dependencies, downloaded an extra 111Mb and logged out  of GNOME and into KDE. Well, although I didn't spend much time on it I can see it's not for me, and have decided not to use it. 

I'm back in GNOME now, and trying to remove my KDE trial. I've removed kubuntu-desktop, but it didn't take it's dependencies with it, and so I'm stuck with Kubuntu/KDE. 

How do I get rid of this? 
- Matt

---

### Post by Old Pink on 2006-12-16
Hm. I'll use a modified version of this:
[http://doc.gwos.org/index.php/Uninstall_kubuntu-desktop](http://doc.gwos.org/index.php/Uninstall_kubuntu-desktop)

But I want to keep just enough to satisfy amarok, etc.

---

### Post by Old Pink on 2006-12-16
Here's the situation:```
matt@matt-desktop:~$ sudo apt-get remove adept akregator ark arts debtags enscript gtk2-engines-gtk-qt gwenview imagemagick ivman kaddressbook kaffeine kamera kappfinder karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin libgadu3 libgpgme11 libjpeg-progs libkcal2a libkcddb1 libkdepim1 libkipi0 libkleopatra0a libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1a libopenobex-1.0-0 libpythonize0 libsensors3 libtdb1 openoffice.org2-kde poster psutils python-kde3 python-opengl python2.4-dev python2.4-kde3 python2.4-opengl python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex speedcrunch ttf-dejavu xlibs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ivman is not installed, so not removed
Package kappfinder is not installed, so not removed
Package kde-style-lipstik is not installed, so not removed
Package kdemultimedia-kappfinder-data is not installed, so not removed
Package klaptopdaemon is not installed, so not removed
Package konserve is not installed, so not removed
Package kubuntu-desktop is not installed, so not removed
Package kuser is not installed, so not removed
Package libkcal2a is not installed, so not removed
Package libkdepim1 is not installed, so not removed
Package libkleopatra0a is not installed, so not removed
Package libmimelib1a is not installed, so not removed
Package openoffice.org2-kde is not installed, so not removed
Package python-opengl is not installed, so not removed
Note, selecting python-kde3 for regex &#8216;python2.4-kde3&#8217;
Note, selecting python-opengl for regex &#8216;python2.4-opengl&#8217;
Package python-opengl is not installed, so not removed
Note, selecting python-qt3 for regex &#8216;python2.4-qt3&#8217;
Package python2.4-sip4-qt3 is not installed, so not removed
Package xlibs is not installed, so not removed
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog krdc libopenobex-1.0-0 krfb kscd kppp libktnef1 konversation
  kubuntu-default-settings libkscan1 kwifimanager python2.4-dev artsbuilder
  kdeprint adept-manager kmplayer-konq-plugins ksvg kscreensaver kwin
  kaffeine-xine libsensors3 kio-locate libpythonize0 ksnapshot liblockdev1
  kdebluetooth kooka kcontrol libkipi0 libbtctl4 wlassistant lives libkcal2b
  gnome-bluetooth adept-installer kdegraphics-kfile-plugins
  konqueror-nsplugins gwenview libtdb1 adept-updater hpijs kdepim-kio-plugins
  python-pymad krita hplip qca-tls klipper kdemultimedia-kio-plugins
  ubuntu-desktop kubuntu-artwork-usplash kontact kdeadmin-kfile-plugins kicker
  ksmserver ksysguard adept-batch libkcddb1 libgadu3 kmenuedit adept
  ksplash-engine-moodin kubuntu-konqueror-shortcuts ksplash foomatic-db-hpijs
  kaffeine libkleopatra1 konsole kipi-plugins korganizer
  kdenetwork-kfile-plugins akregator kio-apt kwin-style-crystal arts
  python-qt3 kamera ark kcron adept-common libksieve0 digikam amarok-xine kdm
  speedcrunch libkpimidentities1 amarok kpf libkdepim1a gaim kghostview
  kdemultimedia-kfile-plugins katapult poster kdenetwork-filesharing
  kubuntu-docs knotes kde-guidance debtags khelpcenter apt-index-watcher
  konqueror kaddressbook libkpimexchange1 gtk2-engines-gtk-qt kmailcvt
  knetworkconf ttf-dejavu ksysguardd konq-plugins psutils language-selector-qt
  qobex libgpgme11 kwalletmanager libsnmp9 imagemagick libgnomebt0 kopete karm
  kate kmail amarok-engines adept-notifier kde-guidance-powermanager
  libjpeg-progs dvdrip kde-systemsettings kdepim-kresources kdepim-wizards
  kmilo nautilus-sendto kaudiocreator enscript python-kde3 kdepasswd kmix
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  adept adept-batch adept-common adept-installer adept-manager adept-notifier
  adept-updater akregator amarok amarok-engines amarok-xine apt-index-watcher
  ark arts debtags digikam dvdrip enscript foomatic-db-hpijs gaim
  gnome-bluetooth gtk2-engines-gtk-qt gwenview hpijs hplip imagemagick
  kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kaudiocreator
  kcontrol kcron kde-guidance kde-guidance-powermanager kde-systemsettings
  kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources
  kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate
  kipi-plugins klipper kmail kmailcvt kmenuedit kmilo kmix
  kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror
  konqueror-nsplugins konsole kontact konversation kooka kopete korganizer
  kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash
  ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kwalletmanager kwifimanager kwin
  kwin-style-crystal language-selector-qt libbtctl4 libgadu3 libgnomebt0
  libgpgme11 libjpeg-progs libkcal2b libkcddb1 libkdepim1a libkipi0
  libkleopatra1 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0
  libktnef1 liblockdev1 libopenobex-1.0-0 libpythonize0 libsensors3 libsnmp9
  libtdb1 lives nautilus-sendto poster psutils python-kde3 python-qt3
  python2.4-dev qca-tls qobex speedcrunch ttf-dejavu ubuntu-desktop
  wlassistant
```I want to keep ubuntu-desktop etc! They *are* needed, what am I removing that makes it think they're not? :(

---

### Post by kyruz on 2006-12-16
I have also tryed KDE, but I liked Gnome better.

Use this link to remove KDE: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Old Pink on 2006-12-16
^ That'll remove nearly your entire system! It was about to "free" 781Mb of stuff, when I only installed 110! No thanks! 

I used: ```
sudo apt-get remove adept kaddressbook kaffeine kamera kappfinder karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin
```

---

### Post by melancholeric on 2006-12-16
I had the exact same problem. 

I just opened synaptic, went through installed packages and removed nearly everything that mentioned KDE. And checked on every package that it will not remove amarok. Took a while though.

Actually I think I left some other kde packages too, but most of it is gone now. And got something like 400 Mb of free space with that.

---

### Post by kyruz on 2006-12-16
Oki. Then I have a light version of Gnome. 

It worked for me. I get rid of all KDE and my system has worked excellent since.

---

### Post by Old Pink on 2006-12-16
> **Old Pink said:**
> I used: ```
sudo apt-get remove adept kaddressbook kaffeine kamera kappfinder karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin
```That was perfect, thanks for everyone's input, it did contribute to an overall brilliant result. :) 

And melan, that was a last resort I had in mind. ;)

---

### Post by Old Pink on 2006-12-16
Now trying Xubuntu, which is impressive. Still a GNOME fan though. :P

---

### Post by MCSE_Crossover on 2007-02-08
I have heard that using a command line "aptitude" instead of "apt-get" will allow for complete removal of a package and its dependencies. There is some information out there somewhere - I believe on the psychocats website. So, it would appear like this:

Instead of using:

"sudo apt-get install kubuntu-desktop" and "sudo apt-get remove kubuntu-desktop" 

Use:

"sudo aptitude install kubuntu-desktop" and "sudo aptitude remove kubuntu-desktop"


Searching for actuall site link.....

Got it!

[http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude")

Hope that helps!

---

