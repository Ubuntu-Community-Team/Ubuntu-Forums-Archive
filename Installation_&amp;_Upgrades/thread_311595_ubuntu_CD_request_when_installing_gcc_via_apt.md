---
title: "ubuntu CD request when installing gcc via apt??"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by spip on 2006-12-03
Hello,

While installing gcc via apt, the installation process requested the ubuntu installation disc:

[I][INDENT]Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main binutils 2.16.1cvs20060117-1ubuntu2.1 [1407kB]
Media change: please insert the disc labeled
 'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
in the drive '/cdrom/' and press enter
[/INDENT][/I]

How does this happen? Does the gcc package refer to the binutils package (see above), with the local apt runtime then knowing (some way or another) that this package can be found on the ubuntu image?

I'm just curious how a package downloaded from the net can end up triggering a request for my original installation CD.

Thank you.

---

### Post by mssever on 2006-12-03
I'm guessing that if you look in /etc/apt/sources.list--or the repositories section in Synaptic--that you'll find a reference to your CD there. Basically, the Live CD contains a repo already. If you remove the reference to the CD, then it won't ask for the CD anymore.

---

