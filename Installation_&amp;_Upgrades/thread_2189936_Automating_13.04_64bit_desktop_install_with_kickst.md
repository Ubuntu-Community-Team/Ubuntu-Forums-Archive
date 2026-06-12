---
title: "Automating 13.04 64bit desktop install with kickstart?"
date: 2013-11-24
forum: Installation &amp; Upgrades
---

### Post by rjvilla2 on 2013-11-24
I am trying to automate the installation of 13.04 64 bit desktop edition for easy recovery purposes using kickstart. All the documentation and "how to's" I run across reference using kickstart with the "alternate install cd". However, it appears that doesn't exist any longer for 13.04 +. Is there still a way to do this with the regular Live CD? It's become a bigger challenge than I expected. I'm sure there must be a way.

---

### Post by ian-weisser on 2013-11-26
Historically, Ubuntu automated installers use a Preseed file. But at least one Canionical engineer seems willing to support Kickstart.

Did you see [https://help.ubuntu.com/community/KickstartCompatibility](https://help.ubuntu.com/community/KickstartCompatibility) ? Looking that over, Alternate ve Live installer shouldn't make a differences - both should work. Kickstart is implemented as a layer of Preseed, and the first thing *any* installer does is check for a Preseed file...

...but I have never tried kickstart myself, so my opinion is cheap.

---

