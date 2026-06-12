---
title: "Ubuntu Linux 4.10: The Warty Warthog... howto upgrade"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by AJKDiablo on 2005-06-28
My Suse 9.2 went to a critical stage so I decided to install ubuntu (i've installed it to several places before) but the problem is that I don't have installation CD for Hoary (or to Suse, which I also liked :( ).  Are there any ways to upgrade Warty to Hoary, or do I need to get the installation CD for Hoary?

How about ftp? Are there any diskette solutions like "using this disk gives you an opportunity to install Hoary over net"

---

### Post by Leif on 2005-06-28
Open a terminal and type "sudo gedit /etc/apt/sources.list". Change every instance of warty there to hoary. Save and close. Now type "sudo apt-get update", and "sudo apt-get dist-upgrade". When it's all done, reboot, and you're in hoary. (This all assumes you have an internet connection, and may take a long time if you're on dialup and not broadband)

---

### Post by AJKDiablo on 2005-06-29
I'll give it try. If it is this easy I will never install a new OS on my computer  :---)

---

### Post by Leif on 2005-06-29
Hope it works for you. It did for me, with zero problems. And when the next release, breezy comes along in october, it will be just as easy to upgrade to that. Smart huh ?

---

### Post by AJKDiablo on 2005-06-29
[QUOTE=Leif]Hope it works for you. It did for me, with zero problems. And when the next release, breezy comes along in october, it will be just as easy to upgrade to that. Smart huh ?[/QUOTE]
Works perfectly and the upgrade was almost a complete success \o/

For some reason firefox does not work at the moment, but I think I can figure it out myself. Looking great, working fine, now I'm ready, Ubuntu is mine.

Thanks Leif.

EDIT:
ajkdiablo@ajkdiablo:~ $ firefox
*** loading the extensions datasource
*** loading the extensions datasource
*** loading the extensions datasource
*** loading the extensions datasource
*** loading the extensions datasource
(and keeps rolling like limp bizkit)

Dunno why   :roll:

---

### Post by Leif on 2005-06-29
Hmm, maybe it's some extensions you had installed that don't work with the newer version of firefox ? In that case, you might want to clear out the extensions in the ~/.mozilla/firefox/username/extensions directory. I've never tried this, so it might not work. Also, reinstalling might help, and as a final measure, complete remove and then reinstall.

---

### Post by AJKDiablo on 2005-06-29
[QUOTE=Leif]Hmm, maybe it's some extensions you had installed that don't work with the newer version of firefox ? In that case, you might want to clear out the extensions in the ~/.mozilla/firefox/username/extensions directory. I've never tried this, so it might not work. Also, reinstalling might help, and as a final measure, complete remove and then reinstall.[/QUOTE]
I chose the complete removal. Works like a dream \o/

---

