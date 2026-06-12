---
title: "Unresolved Dependency While Installing RealPlayer"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by kalix on 2006-06-13
I'm trying to install the RealPlayer installer from the repositories, to install the cs2 rpm.. I already installed Reaplayer on my desktop, but when I do it on the laptop from add/remove it sends me to the Synaptic Package Manager. When I try to install Realplayer in the Syanptic Package Manager, I get the unresolved dependency that says:

realplayer:
 Depends: xlibs  but it is not installable

  So, I installed xlibs-dev, and tried again.. Got exactly the same message.. Any suggestions?

---

### Post by johnc4510 on 2006-06-13
Use this web site to install real player:
[ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb)
When the download manager appears, choose to open with GDebi package manager. This will install it automatically.

---

### Post by kalix on 2006-06-13
[QUOTE=johnc4510]Use this web site to install real player:
[ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb)
When the download manager appears, choose to open with GDebi package manager. This will install it automatically.[/QUOTE]

 Wow.. Thanks :)

---

### Post by vihm on 2006-06-22
[QUOTE=johnc4510]Use this web site to install real player:
[ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb)
When the download manager appears, choose to open with GDebi package manager. This will install it automatically.[/QUOTE]

Link not working. Couldn't find it while browsing the ftp site either :(

Okay... found another one:
[http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb)

---

### Post by nu2this on 2006-06-28
I'd love to install from the .deb but I originally put Realplayer in with Automatix. The only trouble is Automatix doesn't install Realplayer all the way. One has to do the rpm
which chose I not to do. Then even after removing RealPlayer(both thru Synaptic & terminal)  I try the .deb & it says i have realplyer installed & stops the install there.
In Synaptic the installer realplayer 8.0.11 is in there set as removed.
For removal in terminal I used apt-get & aptitude remove Realplayer is there another command I can use?
Is there a way I can use the .deb?

---

### Post by dfavro on 2006-08-10
This works: apt-get install realplay

---

