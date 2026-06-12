---
title: "much needed infos abt updates and ppas"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Elie-M on 2010-05-08
I keep reading and hearing that ubuntu updates his software with the update manager which simplifies the users tasks and keep us up to date. but from my experience nearly 80% of my software needed manual ppa adding for them to be upgraded (including gimp - to 1.7)

which brings me to my questions:

1- was what I read and heard true?
2- what packages does ubuntu upgrade without my interference
3- which software do I have to add the ppas for? cz honestly I'm adding a lot namely: firefox, vlc, wine, gimp, linux kernel, play on linux, gwibber, among others. is it normal that ubuntu does support upgrades for all of those?

please explanations if possible and thanks.. I'm confused.

(btw note: I generated a lucid software sources from the online software generator for my lucid)

---

### Post by zvacet on 2010-05-09
In most cases when one version of Ubuntu is out very rarely packages are upgraded.If you want newest packages you have to use ppa.Ubuntu,I think,doesn´t include them in updates because all packages have to be stable,witch mean tested.You can get latest FF on [Ubuntuzilla.]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page")Wine is availabe from [here.]("http://www.winehq.org/download/")If new packages doesn´t give extra options of fixing bugs I think there is no reason to use them.

---

### Post by P4man on 2010-05-09
Dont confuse updates with upgrades!

Using ubuntu greatly simplifies the process of keeping the OS and all apps updated, that means they all receive bug fixes and security patches. 

If you want new versions of those apps (*upgrades*), ubuntu tends to make it harder on you, not easier. Ubuntu keeps applications versions frozen per release. Every 6 months a new version of ubuntu comes with upgraded applications. Inbetween, ubuntu will never automatically upgrade your firefox, openoffice etc. It would be impossible to test properly. You just get bugfixes and security patches for the version you already have.

Understand that ubuntu is not just an OS. Its a distribution consisting of an OS and a wide range of applications that are distributed, installed and supported together. Openoffice and firefox are really part of ubuntu, and the version of those apps you get, is tied to the version of ubuntu you are running.

More info here:
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Also explains how to add backport repo to get upgrades for some selected apps.

---

### Post by Elie-M on 2010-05-09
this is the explanation I EXACTLY needed thx both :)

---

