---
title: "How do I install my sagem dsl modem?"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by stripy tiger on 2005-05-18
Hi,

I'm very new to Ubuntu and to linux in general, but I've loved the taste of Ubuntu I've had so far. My problem is that I can't find a way to install my dsl modem, which is a sagem f@st 800 E2T. It's very important that I am able to use the internet and unless I can find a way to install my modem, it won't be possible to keep Ubuntu as my OS. So the stakes are high!

I have already found the eagle-usb drivers which are available in the synaptic package, but I'm ashamed to say, I don't understand the intructions that come with them. 

So I'd greatly appreciate it if someone could describe to me how I should go about installing and configuring the drivers and afterwards starting the modem.

Thankyou!

---

### Post by defkewl on 2005-05-18
Have your modem been connected? Did Ubuntu detect your modem?

---

### Post by stripy tiger on 2005-05-18
The modem was plugged in while the installation was taking place, but it wasn't detected, I understand that's usual for USB modems.

---

### Post by sporniket on 2005-05-18
I had the same problem than you (with a 4.10) : the package to get are not in the install CD.

I wrote a [solution](http://www.sporniket.com/page/blog/david/200504032149) about it on my site, in French, for the sake of remembering. Here is a summary. There is also a [French site](http://dev.eagle-usb.org/) about this modem, hosting the driver.

Requirements :
[list]
[*]An installation where you have access to the net (I have an old Mandrake-Linux on a separate hard-disk, and I had to use linx, as my Xsetup is screwed up for this install  ](*,) ), because you'll have to download some packages.
[*]a space to save the package to download. This space should be accessible to your Ubuntu installation
[/list]

Ubuntu packages to install
[list]
[*]linux-kernel-header
[*]linux-header-<version>
[*]gcc
[/list] 

Debian packages to download and install (internet required !!) : 
[list]
[*]module-assistant
[/list] 

Package to download from [Eagle USB](http://dev.eagle-usb.org/) (internet required !!) :

[list]
[*]eagle-usb-data
[*]eagle-usb-module-sources
[*]eagle-usb-utils
[/list] 

Then follow these [instructions](http://dev.eagle-usb.org/wakka.php?wiki=DocDebian) 

> Devenez root :
su -
Installez les fichiers contenant les codes DSP :
dpkg -i eagle-usb-data-1.9.8-3_all.deb
Installez le code source du driver eagle-usb :
dpkg -i eagle-usb-modules-source-1.9.8-3_all.deb
(juste au cas où) Effacez l'archive décompressée provenant d'une installation antérieure :
cd /usr/src
rm -rf modules/eagle-usb/
Détermine le nom du paquet kernel-headers requis (éventuellement aucun)
module-assistant prepare
Décompressez l'archive :
module-assistant get eagle-usb
Compilez le driver et créer le paquet qui l'installe :
module-assistant build eagle-usb
Installez le driver eagle-usb :
module-assistant install eagle-usb
Installez tous les utilitaires accompagnants le driver :
dpkg -i eagle-usb-utils-1.9.8-3_i386.deb


To setup again : > dpkg-reconfigure eagle-usb-utils

However, the connection is not automatic, so before accessing the net, you have to open a console and invoke :
> eaglectrl -d
sudo startadsl

Et voilà ! (hopefully...)

---

