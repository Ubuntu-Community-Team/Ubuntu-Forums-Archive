---
title: "No Valid Kernel"
date: 2004-11-02
forum: Installation &amp; Upgrades
---

### Post by Vash-kun on 2004-11-02
I had played with the pre-release of Warty, and fell for Ubuntu a month or so ago.  When the release version was announced, I downloaded immediately.  During the install, the base system refuses to install and gives a "no valid kernel package" type of error.  All this after it hoses my partitons, forcing me back to windows.  What did I do wrong?

---

### Post by Mighty Mik on 2004-11-02
in a word...nothing. I think this is an installer bug, and it goes like this: You boot off the cd, and start the installer...it gets to aboiut 86%, then tells you no valid kernel blah blah, and can't install to unclean source. Ok...lets back up. Right at the network detection, it asks you which network connection is the right one (if you only have one, it's a no brainer), it then configures the network, then it asks you for a name for the network box (default is ubuntu), then rips thru the rest of the install. W O A H!! wait a minute. during the 'Sarge' install (similar installer)...right after the place where it asks for the name, it THEN asks for a server name (in my case IT GRABS IT FROM THE SERVER IT'S CONNECTED TO), *then* it rips SUCCESSFULLY thru the install. mind you, i'm using the Sarge netinstall, and it's only 150MB. (it's having a little trouble getting stuff from ftp.debian.org today). Looks like i have some work to do... i have to find the rest of my packages.

---

### Post by Vash-kun on 2004-11-02
That is exactly what happened.  Who do I report this to?

---

### Post by Mighty Mik on 2004-11-02
Hopefully the powers-that-be are paying attention. it might be usefull if you post details about your stuff. mine's an AMD processor, on an nForce2 chipset, with a nVidia TI4200 vid card.

---

### Post by jdong on 2004-11-02
[QUOTE=Vash-kun]That is exactly what happened.  Who do I report this to?[/QUOTE]
 [https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)

---

