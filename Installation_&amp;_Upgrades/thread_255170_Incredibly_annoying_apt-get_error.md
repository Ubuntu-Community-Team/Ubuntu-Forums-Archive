---
title: "Incredibly annoying apt-get error"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by thomasca on 2006-09-11
Alright, I tried to fix it for a long time now, but I still get this error everytime I do ANYTHING in apt-get or synaptic.

[PHP]dpkg: parse error, in file `/var/lib/dpkg/available' near line 8665 package `totem-gstreamer':
 field name `' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/PHP]

Please help. :confused:

---

### Post by amo-ej1 on 2006-09-11
Have you tried:

a) create a backup of /var/lib/dpkg/available
b) modify line 8665 and remove the weird thingy
c) use apt ?

But according to [http://forums.debian.net/viewtopic.php?t=400&](http://forums.debian.net/viewtopic.php?t=400&) each apt-get update will overwrite the available file, they suggest walking through the soruces masking each one out one of a time and find out which source it causing the trouble ...

---

### Post by randell6564 on 2006-09-11
> **thomasca said:**
> Alright, I tried to fix it for a long time now, but I still get this error everytime I do ANYTHING in apt-get or synaptic.

[PHP]dpkg: parse error, in file `/var/lib/dpkg/available' near line 8665 package `totem-gstreamer':
 field name `' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/PHP]

Please help. :confused:

Hi!  Open a terminal, and type '**sudo gedit /var/lib/dpkg/available**'
Look for a description refering to 'totem-gstreamer'. The rest should be self-explanatory. I am just going by what I have found in MY [B]/var/lib/dpkg/available 
[/B]
The "field name" is not in the proper syntax.

I'm NOT a pro, but this is what it looks like to me.

---

