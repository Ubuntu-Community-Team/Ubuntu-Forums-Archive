---
title: "Export Synaptic history"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by Jaraxle on 2010-02-26
Hi, I'm trying to find a way to export my Synaptic History (what you see if you browse through History using Synaptic). Ideally, I'd like to export this to a csv file or xml, but plain text will do.

I've searched, and the closest I've come to finding a solution is going to /var/log/ and looking through the various dpkg.log files and archives. It has the information I need buried in there, but there is also a ton of system info.

What I would like is just the names of the packages I installed. I could copy and paste it into a text file directly from Synaptic, but there is a lot of data and that would take a very long time. Does anyone know of a more elegant (and faster) solution? If not, I guess I'll have to abandon this idea. Thanks for any help you can give.

---

### Post by Barriehie on 2010-02-26
Try looking in /root/.synaptic/log I think it is and you'll find a log file for every session of synaptic where something was either installed or removed.  I cat those into one file in my $HOME and it makes for easy searching...

HTH,
Barrie

---

### Post by Jaraxle on 2010-02-26
That worked perfectly! Thanks, mate.

---

