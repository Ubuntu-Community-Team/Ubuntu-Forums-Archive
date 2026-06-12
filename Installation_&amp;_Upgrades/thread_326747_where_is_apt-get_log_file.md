---
title: "where is apt-get log file??"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by bitzer on 2006-12-28
Hi guys,
Here is a simple question: Where is/Where are apt-get log file/files?? I looked in /var/log but I found nothing. I'm looking for a log file listing all packages that were installed, removed or upgraded by apt-get; just like the one created by pacman in archlinux and/or in frugalware. Is there something similar in ubuntu edgy?

---

### Post by bapoumba on 2006-12-28
Hi, apt-get does not log and relies on dpkg's log.

Synaptic logs a history file (>File > History) , aptitude logs both history in /var/log/aptitude and auto-installed packages in /var/lib/aptitude/pkgstates, so just guess which one I am using ;)

---

### Post by bitzer on 2006-12-28
Thanks! dpkg log file is what I was looking for. Are you using Synaptic? :D

---

### Post by bapoumba on 2006-12-28
Wow, that was a wild guess :D

---

