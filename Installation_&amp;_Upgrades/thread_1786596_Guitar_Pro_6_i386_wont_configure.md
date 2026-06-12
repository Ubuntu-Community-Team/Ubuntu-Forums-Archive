---
title: "Guitar Pro 6 i386 wont configure"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by rehaby on 2011-06-19
Guitar Pro 6 wont configure as it is 32bit and depends on some 32bit packages have tried using the command dpkg --get-selections | grep but i get the same output with out the force 

can anyone please help. I have already googled it and looked through the man pages and in the debian manual


$ sudo dpkg --configure --force-depends guitarpro6:i386dpkg: dependency problems prevent configuration of guitarpro6:i386:
 guitarpro6:i386 depends on libc6 (>= 2.1.3).
 guitarpro6:i386 depends on libstdc++6.
 guitarpro6:i386 depends on libasound2.
 guitarpro6:i386 depends on libxml2.
 guitarpro6:i386 depends on libxslt1.1.
 guitarpro6:i386 depends on libportaudio0.
 guitarpro6:i386 depends on libportaudio2.
 guitarpro6:i386 depends on libglu1-mesa.
 guitarpro6:i386 depends on gksu.
dpkg: error processing guitarpro6:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 guitarpro6:i386

---

