---
title: "How to remove dependencies!!!"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by dioxholster on 2010-07-15
i installed a program called kjots which is made for KDE not gnome. i run ubuntu. anyway it installed lots of dependencies and now i want to uninstall kjots but i know that will leave lots of unused dependencies or packages. i dont know how to clean after.
heres whats on the terminal when i installed:

> The following NEW packages will be installed:
  akonadi-server exiv2 gdebi-kde hal hal-info icoutils install-package kdebase-runtime kdebase-runtime-data kdelibs-bin
  kdelibs5 kdelibs5-data kdepim-runtime kdepimlibs-data kdepimlibs5 kdesudo kjots kpackagekit kubuntu-debug-installer
  libakonadiprivate1 libattica0 libboost-program-options1.40.0 libclucene0ldbl libdbusmenu-qt2 libexiv2-6 libiodbc2
  libmysqlclient16 libpackagekit-glib2-12 libpackagekit-qt-12 libplasma3 libpolkit-qt-1-0 libqca2 libqt4-assistant
  libqt4-help libqt4-opengl libqt4-qt3support libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test
  libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin
  libxine1-console libxine1-misc-plugins libxine1-x mysql-client-core-5.1 mysql-common mysql-server-core-5.1
  oxygen-icon-theme packagekit packagekit-backend-apt phonon phonon-backend-xine plasma-scriptengine-javascript
  polkit-kde-1 python-kde4 python-packagekit python-qt4 python-sip shared-desktop-ontologies smartdimmer
  software-properties-kde soprano-daemon ttf-dejavu ttf-dejavu-extra update-manager-kde virtuoso-nepomuk

i think that all of it. will that stuff slow the system and should i just leave it? im used to windows not linux so i dont know.

one more thing, i discovered a program called computer janitor, looks stupid but can it remove dependencies and everything KDE-related?

---

### Post by HenneBaby02 on 2010-07-15
I'm still new too, i kno u can either type in terminal

$ sudo apt-get remove kjots

or go to application>add/remove

as far as cleaning after.... i remember seeing "BleachBit" works good but i haven't tried it. hope that helps

---

### Post by kerry_s on 2010-07-15
use synaptic, on the bottom left click status. when you remove kjots it will show you all the stuff that can be auto removed.

---

### Post by dioxholster on 2010-07-15
BleachBit seems like Ccleaner which is useful for general cleaning so thanks. 

should  i use synaptic? i installed kjots in terminal, ive always used the terminal. 
and i found this advice from really old forums, but i aint sure coz its from 2005:  one guy said:


> here's a few "no dirty hands" deborphan commands:

$ sudo apt-get remove --purge `deborphan`
Removes and purges the orphan packages

$ sudo apt-get remove `deborphan`
Removes the orphan packages

$ sudo apt-get install wajig
$ sudo wajig orphans
installs wajig and removes orphan packages

$ su
$ dpkg --purge `deborphan`
similar to apt-get --purge

$ su
$ deborphan | xargs apt-get --purge remove -y
similar to apt-get --purge
__________________

then someone else said:

> A simple (but not retroactive) way to do what you want is to use "aptitude". It's a combination of apt-get & apt-cache. You can
"aptitude search package" to find packages, "aptitude show packagename" to show details about a package, and "aptitude install foo"/"aptitude remove foo".

Best of all, it marks any dependencies it automatically installs as "automatic". When you remove a package, and there is now an "automatic" package which nothing else depends on, it also removes the automatic package.

This, however, only works for things you've installed through aptitude. For stuff you've already done, deborphan/gtkorphan should work.

and last one:

> apt-get remove --purge <application name>



so are any of them right? how come there are so many ways in linux to do one thing? which course to take?

one more important question: is it worth it uninstalling kjots in the first place? i mean can i just ignore it. the reason i wanted to remove it, is because i realized tomboy is better, KDE fanboys tricked me into installing it. so now my main concern is it i dont want something not being used hogging the system, im running on 1 GB of ram here :)

---

### Post by jtarin on 2010-07-15
> so are any of them right? how come there are so many ways in linux to do one thing? which course to take?
Choose the one that works best for you and stay with it, I would advise. Synaptic seems to work for me best. Linux is about choice,independence. Learn to be free from the restrictions of proprietary software.

---

### Post by dioxholster on 2010-07-15
> **jtarin said:**
> Choose the one that works best for you and stay with it, I would advise. Synaptic seems to work for me best. Linux is about choice,independence. Learn to be free from the restrictions of proprietary software.

ah okay lol, i just wanna know how to properly remove those dependencies or whatever that was listed in the terminal that i quoted above. dont know about freedom from proprietary software though.

---

### Post by thahir1986 on 2010-07-15
i think this one remove the package with their dependencies...;)



```
$ sudo apt-get autoremove kjots
```

---

### Post by mc4man on 2010-07-15
Most of what's on the list could go, but you may have installed something esle since then that depends on something. Otherwise you could work the list into an sudo apt-get remove command.

Try 
```
sudo apt-get purge kjots
```

When done go this (copy the list of what's to be removed to compare with what was installed before answering y

```
sudo apt-get autoremove
```

Then anything from first list (installed) that wasn't removed do a search for in synaptic and see what would happen if marked for removal...

---

### Post by dioxholster on 2010-07-15
> **thahir1986 said:**
> i think this one remove the package with their dependencies...;)



```
$ sudo apt-get autoremove kjots
```


im tempted but i have a feeling i might turn into trouble if i use it, what if it deletes used dependencies? can i know exactly what it will remove?
maybe i should go with the synaptics idea since i would select them myself.

---

### Post by jtarin on 2010-07-15
Right-click on any pkg in Synaptic and it will show you what depends on that application.

---

### Post by dioxholster on 2010-07-15
> **mc4man said:**
> Most of what's on the list could go, but you may have installed something esle since then that depends on something. Otherwise you could work the list into an sudo apt-get remove command.

Try 
```
sudo apt-get purge kjots
```

When done go this (copy the list of what's to be removed to compare with what was installed before answering y

```
sudo apt-get autoremove
```

Then anything from first list (installed) that wasn't removed do a search for in synaptic and see what would happen if marked for removal...


i did the first part,sudo apt-get purge kjots btw i did not install anything after. this all happened today.


 > 
this is the list from before:

akonadi-server exiv2 gdebi-kde hal hal-info icoutils install-package kdebase-runtime kdebase-runtime-data kdelibs-bin
  kdelibs5 kdelibs5-data kdepim-runtime kdepimlibs-data kdepimlibs5 kdesudo kjots kpackagekit kubuntu-debug-installer
  libakonadiprivate1 libattica0 libboost-program-options1.40.0 libclucene0ldbl libdbusmenu-qt2 libexiv2-6 libiodbc2
  libmysqlclient16 libpackagekit-glib2-12 libpackagekit-qt-12 libplasma3 libpolkit-qt-1-0 libqca2 libqt4-assistant
  libqt4-help libqt4-opengl libqt4-qt3support libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test
  libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin
  libxine1-console libxine1-misc-plugins libxine1-x mysql-client-core-5.1 mysql-common mysql-server-core-5.1
  oxygen-icon-theme packagekit packagekit-backend-apt phonon phonon-backend-xine plasma-scriptengine-javascript
  polkit-kde-1 python-kde4 python-packagekit python-qt4 python-sip shared-desktop-ontologies smartdimmer
  software-properties-kde soprano-daemon ttf-dejavu ttf-dejavu-extra update-manager-kde virtuoso-nepomuk


this is after the code sudo apt-get purge kjots:

 kdepim-runtime linux-headers-2.6.32-21 mysql-client-core-5.1 mysql-server-core-5.1 linux-headers-2.6.32-21-generic
  akonadi-server

as you can see there is a big difference. lots of stuff got downloaded for that KDE program. the autoremove option will only remove 4 items out of 75 that were installed! should i continue and just autoremove?

---

### Post by dioxholster on 2010-07-15
alright, i uninstalled kjots only, then in the installed (autoremovable) the same 5 teobjects ms are listed, the are the one attached to the program. but what about the other 70 files? are they part pf the core system now that they should be installed?

right now you wont believ what im doing. im going through each file searching it in synaptic and marking it for removal.

---

### Post by dioxholster on 2010-07-15
i dont know if its wrong or right by i removed these individully in synaptic:

Commit Log for Thu Jul 15 12:25:05 2010


Completely removed the following packages:
akonadi-server
exiv2
gdebi-kde
hal
hal-info
icoutils
install-package
kdebase-runtime
kdebase-runtime-data
kdelibs-bin
kdelibs5
kdelibs5-data
kdepim-runtime
kdepimlibs-data
kdepimlibs5
kdesudo
kpackagekit
kubuntu-debug-installer
libakonadiprivate1
libattica0
libboost-program-options1.40.0
libclucene0ldbl
libdbusmenu-qt2
libexiv2-6
libiodbc2
libmysqlclient16
libpackagekit-glib2-12
libpackagekit-qt-12
libplasma3
libpolkit-qt-1-0
libqca2
libqt4-assistant
libqt4-help
libqt4-opengl
libqt4-qt3support
libqt4-scripttools
libqt4-sql
libqt4-sql-mysql
libqt4-svg
libqt4-test
libsoprano4
libssh-4
libstreamanalyzer0
libstreams0
libxcb-shape0
libxcb-shm0
libxcb-xv0
libxine1
libxine1-bin
libxine1-console
libxine1-misc-plugins
libxine1-x
mysql-client-core-5.1
mysql-common
mysql-server-core-5.1
oxygen-icon-theme
packagekit
packagekit-backend-apt
phonon
phonon-backend-xine
plasma-scriptengine-javascript
polkit-kde-1
python-kde4
python-packagekit
python-qt4
python-sip
shared-desktop-ontologies
smartdimmer
software-properties-kde
soprano-daemon
ttf-dejavu
ttf-dejavu-extra
update-manager-kde
virtuoso-nepomuk


----

74 objects the same on the install list. but i also deleted their config when i chose "mark for complete removal"

---

### Post by dioxholster on 2010-07-15
so is everyone okay with what i did?

---

