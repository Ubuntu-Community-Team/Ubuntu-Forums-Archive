---
title: "Corrupted x86 Install ISO?"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by bjeezus on 2005-04-09
I previously had warty installed on my old compaq and tried to install the hoary release today. I downloaded it from the US download site. The set-up goes through the CD-ROM, NIC, Network, other hardware set-up and starts to install the ubuntu base system before I get the error that there was an error finding the debootstrap package, man-db.

I tried re-burning the ISO at a slower speed with 2 different burning softwares and got the same error. I also did an integrity check on the CD in the set-up options and found that ./pool/main/m/man-db/man-db2.4.2-21_i386.deb was missing or corrupted.

Is there something I'm not doing right or (as I suspect) is the image corrupted? I'm trying to download from a different mirror to see if that helps at all.

Thanks.

Ben

P.S. 
ubuntu rocks, I've been searching for a distro I liked and ubuntu is the bee's knees. The support is tremendous, I had several problems with my fan and sound card, when I signed on here and searched the forum I found the fix right away. Thanks guys!

---

### Post by humanity_to_others on 2005-04-09
Copy your non-corrupt files in a directory an use jigdo.

---

### Post by bjeezus on 2005-04-09
[QUOTE=humanity_to_others]Copy your non-corrupt files in a directory an use jigdo.[/QUOTE]
 Thanks! Downloaded Jigdo and it's downloading the packages and generating an ISO now.

---

