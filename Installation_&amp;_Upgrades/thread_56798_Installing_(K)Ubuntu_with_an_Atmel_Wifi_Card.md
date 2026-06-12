---
title: "Installing (K)Ubuntu with an Atmel Wifi Card"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by Beuntje on 2005-08-14
I´m trying to install (K)Ubuntu linux, but he doesn´t see any network cards.
I have a Belkin USB Wifi Network card (Atmel Chipset)
But when installing it is not been found  :mad: 

I´ve read that (K)ubuntu has the ATMEL driver onboard, but why doesn´t it start at boot?
And how do i get it to work, and install (K)ubuntu?

Please type it in mickeymouse language (i´m a beginner  :smile: )

---

### Post by OwlManAtt on 2005-08-14
[QUOTE=Beuntje]I´m trying to install (K)Ubuntu linux, but he doesn´t see any network cards.
I have a Belkin USB Wifi Network card (Atmel Chipset)
But when installing it is not been found  :mad: 

I´ve read that (K)ubuntu has the ATMEL driver onboard, but why doesn´t it start at boot?
And how do i get it to work, and install (K)ubuntu?

Please type it in mickeymouse language (i´m a beginner  :smile: )[/QUOTE]
 Perhaps you should try this driver:

[http://at76c503a.berlios.de/](http://at76c503a.berlios.de/)

And see this wiki page, there are several Belkin wireless devices listed with notes about getting them to work:

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

Also, I believe there is some Atmel wireless driver stuff in the apt repositories. Do an apt-cache search atmel or use the search tool in synaptic, and install that if the Wiki page doesn't help.

---

### Post by Beuntje on 2005-08-14
How can i setup this if the installation doesn´t find my network card, 

Can I continue with installation, and afterwards install the driver?

I know that (K)ubuntu downloads a lot from Internet, or are this just update of some packages?

---

### Post by OwlManAtt on 2005-08-14
[QUOTE=Beuntje]How can i setup this if the installation doesn´t find my network card, 

Can I continue with installation, and afterwards install the driver?

I know that (K)ubuntu downloads a lot from Internet, or are this just update of some packages?[/QUOTE]If by 'set this up' you mean Ubuntu - An Ubuntu installation can be completed without network access. The installation CD holds all of the packages for your basic GNOME desktop (or KDE, in the case of Kubuntu) with OpenOffice, the default GNOME games, FireFox, etc. When Ubuntu is done installing, it tries to fetch any updates for these packages from the internet, but this step can be skipped.

---

### Post by Beuntje on 2005-08-14
Great, i´ll try it  :grin: 

I´ve already installed it on my notebook (Dell Latitude C640) and it works even better than I ever hoped. Wifi Works here without a problem!.

The desktop was always an issue due to some strange hardware, like my Atmel WiFi Card, TV Tuner Card (Pinnacle PCTV Stereo) and my Sony DV camera (Firewire connection) for DV capturing.

Does someone has info which package I can use to view TV under Linux (KDE, like KDETV?)
And a good Video Editing Package like pinnacle Studio (For the n00b) under linux (KDE, like Kino?)

And now let kick Microsoft out of my home  \\:D/

---

### Post by Beuntje on 2005-08-17
I've installed the atmeldriver

now with a 'sudo modprobe atmel' the module is loaded, but there is no device found

when I do a 'sudo lsusb' I see my card listed overthere.

Bus 2 Device 004: 050d:0050 Belkin Components

what am i missing to get the thing working?

 :-x

---

