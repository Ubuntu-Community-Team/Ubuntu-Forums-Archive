---
title: "cups installation problem"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by klausi banausi on 2007-10-17
hello,
I've got troubles installing cupsys on my ubuntu 6.06 server

here some details:

```

root@loslocos:/home/server# apt-get install cupsys
Paketlisten werden gelesen... Fertig
AbhÃ¤ngigkeitsbaum wird aufgebaut... Fertig
cupsys ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 1 nicht aktualisiert.
1 nicht vollstÃ¤ndig installiert oder entfernt.
Es mÃ¼ssen 0B Archive geholt werden.
Nach dem Auspacken werden 0B Plattenplatz zusÃ¤tzlich benutzt.
Richte cupsys ein (1.2.2-0ubuntu0.6.06.3) ...
 * Starting Common Unix Printing System: cupsd                                                               
cupsd: Child exited with status 1!
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: Fehler beim Bearbeiten von cupsys (--configure):
 Unterprozess post-installation script gab den Fehlerwert 2 zurÃ¼ck
Fehler traten auf beim Bearbeiten von:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@loslocos:/home/server#

```

anybody an idea?
merci klaus

---

