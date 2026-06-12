---
title: "apt-get update doesn't works"
date: 2006-03-08
forum: Installation &amp; Upgrades
---

### Post by Schneehenry on 2006-03-08
Hello,
I got a little Problem concerning the command:
**[COLOR="DarkGreen"]sudo apt-get update[/COLOR]**
When I type this line, I get the Message to excecute apt-get update. I just upgraded my dist yesterday.
Greets,
Simon

---

### Post by navilon on 2006-03-08
is it asking for the cdrom?

---

### Post by aysiu on 2006-03-08
Please say exactly what the problem is.
What error messages do you get?

---

### Post by Schneehenry on 2006-03-11
No it doesn't ask for cd-rom.
Ok thats the output of apt-get update:

[B]simon@simon:~$ sudo apt-get update
Hole:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Hole:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hole:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security Release.gpg [189B]
Hole:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hole:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30,9kB]
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release.gpg
Hole:6 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge Release.gpg [191B]
Hole:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security Release [27,0kB]
Hole:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19,6kB]
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hole:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [34,8kB]
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Hole:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Hole:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages [12,4kB]
Hole:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages [708B]
Hole:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [17,3kB]
Hole:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Hole:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Sources [1343B]
Hole:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Sources [365B]
Hole:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/main Packages [43,2kB]
Hole:18 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release.gpg [191B]
Hole:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/restricted Packages [4458B]
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Hole:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/universe Packages [29,3kB]
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Hole:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/multiverse Packages [3830B]
Hole:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/main Sources [13,1kB]
Hole:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/restricted Sources [960B]
Hole:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/universe Sources [4750B]
Hole:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/multiverse Sources [1025B]
Hole:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14,0kB]
Hole:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Hole:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26,1kB]
Hole:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Hole:30 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sid Release.gpg [191B]
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
OK   [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge Release
Ign  [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge Release
OK   [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release
Ign  [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release
OK   [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sid Release
Ign  [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sid Release
Hole:31 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge/main Packages
Ign  [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge/main Packages
OK   [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch/main Packages
OK   [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sid/main Packages
OK   [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge/main Packages
Es wurden 288kB in 2s geholt (98,3kB/s)
Paketlisten werden gelesen... Fertig
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge Release: Die folgenden Signaturen konnten nicht überprüft werden weil ihre öffentlichen Schlüssel nicht verfügbar sind: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: Die folgenden Signaturen konnten nicht überprüft werden weil ihre öffentlichen Schlüssel nicht verfügbar sind: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sid Release: Die folgenden Signaturen konnten nicht überprüft werden weil ihre öffentlichen Schlüssel nicht verfügbar sind: NO_PUBKEY 07DC563D1F41B907
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages)
W: Sie möchten vielleicht »apt-get update« aufrufen, um diese Probleme zu lösen[/B]

I hope you can help me although some messages are in german.

---

