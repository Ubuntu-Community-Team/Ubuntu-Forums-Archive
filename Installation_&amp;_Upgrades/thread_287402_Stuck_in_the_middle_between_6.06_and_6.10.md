---
title: "Stuck in the middle between 6.06 and 6.10?"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by DINO2411 on 2006-10-28
Hey guys,

I decided to upgrade from 6.06 to 6.10 this morning, and everything (download etc.) seemed to work fine in the beginning. But then problems started and I can't figure out how to either complete the entire upgrade nor to step down back to "cleaner" 6.06. 
(I have a German system running, so everything that I translate is not the exact wording, but as I would translate it to English. Please excuse any inconvenience)
Luckily, more or less everything seems to be working (e.g. internet, printer) and all I notice within "usual" work is a lower quality of graphics (I think fglrx was deactivated, but I haven't focused on this yet) and the permanent present of the update button (the orange thing near the clock) that informs me that something is wrong ("There was an error - please use package management or apt-get to find out what happened. Error Code is: "Error: Broken Count > 0")

So, what happened? During the upgrade process I got the following message:
[I]This upgrade requires that the /usr/X11R6/bin directory be removed and replaced with a symlink. An attempt was made to do so, but it failed, most likely because the directory is not yet empty. You must move the files that are currently in the directory out of the way so that the installation can complete. If you like, you may move them back after the symlink is in place.

This package installation will now fail and exit so that you can do this. Please re-run your upgrade procedure after you have cleaned out the directory. [/I]
Of course, I was a bit shocked, but at least the computer was still running on the system after a reboot.
I found out that there was an Opera-file inside the directory, but even emptying it manually did not help. Furthermore, I did not manage to remove Opera entirely. 
When I opened Synaptic Package Management, I was informed that two packages were broken. These two are
- libxdmcp6
- xutils-dev 
"Repair" couldn't fix the problem, all I got was the advice to reinstall using *sudo apt-get install -f*.

Next, I tried some command line stuff (italics=translation)
dirk@dirk-laptop:~$ sudo apt-get remove opera
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
*- Reading package lists, creating dependency tree*
Sie möchten wahrscheinlich »apt-get -f install« aufrufen, um dies zu korrigieren:
*- You likely wanted to use »apt-get -f install« in order to correct the following.*
Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
*- Broken dependencies in these packages:*
libxdmcp6: Hängt ab: x11-common (>= 1:7.0.0) aber 7.0.0-0ubuntu45 soll installiert werden
[I]- libxdmcp6: depends on: x11-common (>= 1:7.0.0) but 7.0.0-0ubuntu45 shall be installed.
[/I]
xutils-dev: Hängt ab: x11-common (>= 1:7.0.0) aber 7.0.0-0ubuntu45 soll installiert werden
*- xutils-dev: Depends on: x11-common (>= 1:7.0.0) but 7.0.0-0ubuntu45 shall be installed.*
E: Nichterfüllte Abhängigkeiten. Versuchen Sie »apt-get -f install« ohne jeglich Pakete (oder geben Sie eine Lösung an).
*- E: Broken dependencies. Try "apt-get -f install" without any packages or provide a solution.*

-----

dirk@dirk-laptop:~$ sudo apt-get -f install
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
Abhängigkeit werden korrigiert... Fertig
*- Reading package lists, creating dependency tree, dependencies corrected*
Die folgenden zusätzlichen Pakete werden installiert:
*- The following packages will be installed:*
x11-common
Die folgenden Pakete werden aktualisiert:
*- The following packages will be updated: *
x11-common
1 aktualisiert, 0 neu installiert, 0 zu entfernen und 932 nicht aktualisiert.
*- 1 updated, 0 new, 0 to be removed, 932 not updated.*
3 nicht vollständig installiert oder entfernt.
*- 3 not completely installed or removed.*
Es müssen noch 0B von 291kB Archiven geholt werden.
Nach dem Auspacken werden 418kB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
Vorkonfiguration der Pakete ...
(Lese Datenbank ... 163464 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von x11-common 7.0.0-0ubuntu45 (durch .../x11-common_1%3a7.1.1ubuntu6_i386.deb) ...
*- Trying to replace xyz by xyz*
Entpacke Ersatz für x11-common ...
*- Unpacking replacement for x11-common*
Ersetze die Dateien im alten Paket xinit ...
*- Replacing files in old xinit-package*
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb (--unpack):
versuche »/usr/X11R6/bin« zu überschreiben, welches auch in Paket opera ist
*- dpkg: Error when working on xyz (unpack): Tried to overwrite »/usr/X11R6/bin«, which is part of the Opera package as well.*
Fehler traten auf beim Bearbeiten von:
/var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb
*- Error when working on: xyz*
E: Sub-process /usr/bin/dpkg returned an error code (1)
dirk@dirk-laptop:~$ 

-----

That was that ... I've been trying for the entire evening now, but I have no idea what's wrong. I would be totally satisfied if I could either continue to 6.10 or end up with a 6.06 that I can trust in, which means: That has no evident mistakes as outlined above.

If you have any ideas, I would be glad if you could provide some suggestions.

Yours,

Dirk#

---

