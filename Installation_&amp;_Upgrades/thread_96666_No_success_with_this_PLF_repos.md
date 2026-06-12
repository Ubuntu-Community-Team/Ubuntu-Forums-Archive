---
title: "No success with this PLF repos"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by fourhead on 2005-11-29
I'm trying to use EasyKubuntu to make my two Kubuntu systems "usable". One is an AMD64 (bot with x86 Kubuntu installed), the other one is a PPC machine. On both machines, the EasyKubuntu script has altered the sources.list. On the AMD64 machine, everything works fine, but on the PPC machine, when I do an apt-get update, I always get this:

```

Hole:1 http://kubuntu.org breezy Release.gpg [189B]
Hole:2 http://security.ubuntu.com breezy-security Release.gpg [189B]
Hole:3 http://archive.ubuntu.com breezy Release.gpg [189B]
Hole:4 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
OK   http://kubuntu.org breezy Release
OK   http://security.ubuntu.com breezy-security Release
OK   http://archive.ubuntu.com breezy Release
Ign  http://kubuntu.org breezy Release
OK   http://archive.ubuntu.com breezy-updates Release
OK   http://kubuntu.org breezy/main Packages
OK   http://security.ubuntu.com breezy-security/main Packages
OK   http://archive.ubuntu.com breezy/main Packages
OK   http://archive.ubuntu.com breezy/restricted Packages
OK   http://security.ubuntu.com breezy-security/restricted Packages
OK   http://security.ubuntu.com breezy-security/universe Packages
OK   http://archive.ubuntu.com breezy/universe Packages
OK   http://archive.ubuntu.com breezy/multiverse Packages
OK   http://archive.ubuntu.com breezy/main Sources
OK   http://archive.ubuntu.com breezy/restricted Sources
OK   http://archive.ubuntu.com breezy/universe Sources
OK   http://archive.ubuntu.com breezy/multiverse Sources
OK   http://archive.ubuntu.com breezy-updates/main Packages
OK   http://archive.ubuntu.com breezy-updates/restricted Packages
OK   http://security.ubuntu.com breezy-security/multiverse Packages
OK   http://security.ubuntu.com breezy-security/main Sources
OK   http://security.ubuntu.com breezy-security/restricted Sources
OK   http://security.ubuntu.com breezy-security/universe Sources
OK   http://security.ubuntu.com breezy-security/multiverse Sources
OK   http://archive.ubuntu.com breezy-updates/universe Packages
OK   http://archive.ubuntu.com breezy-updates/multiverse Packages
OK   http://archive.ubuntu.com breezy-updates/main Sources
OK   http://archive.ubuntu.com breezy-updates/restricted Sources
OK   http://archive.ubuntu.com breezy-updates/universe Sources
Hole:5 ftp://ftp.free.fr breezy Release.gpg
OK   http://archive.ubuntu.com breezy-updates/multiverse Sources
Ign  ftp://ftp.free.fr breezy Release.gpg
Hole:6 ftp://ftp.free.fr breezy Release
Ign  ftp://ftp.free.fr breezy Release
Hole:7 ftp://ftp.free.fr breezy/free Packages
Ign  ftp://ftp.free.fr breezy/free Packages
Hole:8 ftp://ftp.free.fr breezy/non-free Packages
Ign  ftp://ftp.free.fr breezy/non-free Packages
Hole:9 ftp://ftp.free.fr breezy/free Sources
Ign  ftp://ftp.free.fr breezy/free Sources
Hole:10 ftp://ftp.free.fr breezy/non-free Sources
Ign  ftp://ftp.free.fr breezy/non-free Sources
Hole:11 ftp://ftp.free.fr breezy/free Packages
Fehl ftp://ftp.free.fr breezy/free Packages
  Kann Datei nicht holen, Server antwortete »Failed to open file.  «
Hole:12 ftp://ftp.free.fr breezy/non-free Packages
Fehl ftp://ftp.free.fr breezy/non-free Packages
  Kann Datei nicht holen, Server antwortete »Failed to open file.  «
OK   ftp://ftp.free.fr breezy/free Sources
OK   ftp://ftp.free.fr breezy/non-free Sources
Es wurden 192B in 13s geholt (14B/s)
Konnte ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-powerpc/Packages.gz nicht holen  Kann Datei nicht holen, Server antwortete »Failed to open file.  «
Konnte ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-powerpc/Packages.gz nicht holen  Kann Datei nicht holen, Server antwortete »Failed to open file.  «
Paketlisten werden gelesen... Fertig
W: GPG error: http://kubuntu.org breezy Release: Die folgenden Signaturen konnten nicht überprüft werden weil ihre öffentlichen Schlüssel nicht verfügbar sind: NO_PUBKEY A506E6D4DD4D5088
W: Kann nicht auf die Liste ftp://ftp.free.fr breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-powerpc_Packages) der Quellpakete zugreifen. - stat (2 Datei oder Verzeichnis nicht gefunden)
W: Kann nicht auf die Liste ftp://ftp.free.fr breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-powerpc_Packages) der Quellpakete zugreifen. - stat (2 Datei oder Verzeichnis nicht gefunden)
W: Sie möchten vielleicht »apt-get update« aufrufen, um diese Probleme zu lösen
E: Einige Indexdateien konnten nicht heruntergeladen werden, sie wurden ignoriert oder alte an ihrer Stelle benutzt.
Hole:1 http://kubuntu.org breezy Release.gpg [189B]
Hole:2 http://security.ubuntu.com breezy-security Release.gpg [189B]
Hole:3 http://archive.ubuntu.com breezy Release.gpg [189B]
Hole:4 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
OK   http://kubuntu.org breezy Release
OK   http://security.ubuntu.com breezy-security Release
OK   http://archive.ubuntu.com breezy Release
Ign  http://kubuntu.org breezy Release
OK   http://archive.ubuntu.com breezy-updates Release
OK   http://kubuntu.org breezy/main Packages
OK   http://security.ubuntu.com breezy-security/main Packages
OK   http://archive.ubuntu.com breezy/main Packages
OK   http://archive.ubuntu.com breezy/restricted Packages
OK   http://security.ubuntu.com breezy-security/restricted Packages
OK   http://security.ubuntu.com breezy-security/universe Packages
OK   http://archive.ubuntu.com breezy/universe Packages
OK   http://archive.ubuntu.com breezy/multiverse Packages
OK   http://archive.ubuntu.com breezy/main Sources
OK   http://archive.ubuntu.com breezy/restricted Sources
OK   http://archive.ubuntu.com breezy/universe Sources
OK   http://archive.ubuntu.com breezy/multiverse Sources
OK   http://archive.ubuntu.com breezy-updates/main Packages
OK   http://archive.ubuntu.com breezy-updates/restricted Packages
OK   http://security.ubuntu.com breezy-security/multiverse Packages
OK   http://security.ubuntu.com breezy-security/main Sources
OK   http://security.ubuntu.com breezy-security/restricted Sources
OK   http://security.ubuntu.com breezy-security/universe Sources
OK   http://security.ubuntu.com breezy-security/multiverse Sources
OK   http://archive.ubuntu.com breezy-updates/universe Packages
OK   http://archive.ubuntu.com breezy-updates/multiverse Packages
OK   http://archive.ubuntu.com breezy-updates/main Sources
OK   http://archive.ubuntu.com breezy-updates/restricted Sources
OK   http://archive.ubuntu.com breezy-updates/universe Sources
Hole:5 ftp://ftp.free.fr breezy Release.gpg
OK   http://archive.ubuntu.com breezy-updates/multiverse Sources
Ign  ftp://ftp.free.fr breezy Release.gpg
Hole:6 ftp://ftp.free.fr breezy Release
Ign  ftp://ftp.free.fr breezy Release
Hole:7 ftp://ftp.free.fr breezy/free Packages
Ign  ftp://ftp.free.fr breezy/free Packages
Hole:8 ftp://ftp.free.fr breezy/non-free Packages
Ign  ftp://ftp.free.fr breezy/non-free Packages
Hole:9 ftp://ftp.free.fr breezy/free Sources
Ign  ftp://ftp.free.fr breezy/free Sources
Hole:10 ftp://ftp.free.fr breezy/non-free Sources
Ign  ftp://ftp.free.fr breezy/non-free Sources
Hole:11 ftp://ftp.free.fr breezy/free Packages
Fehl ftp://ftp.free.fr breezy/free Packages
  Kann Datei nicht holen, Server antwortete »Failed to open file.  «
Hole:12 ftp://ftp.free.fr breezy/non-free Packages
Fehl ftp://ftp.free.fr breezy/non-free Packages
  Kann Datei nicht holen, Server antwortete »Failed to open file.  «
OK   ftp://ftp.free.fr breezy/free Sources
OK   ftp://ftp.free.fr breezy/non-free Sources
Es wurden 192B in 13s geholt (14B/s)
Konnte ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-powerpc/Packages.gz nicht holen  Kann Datei nicht holen, Server antwortete »Failed to open file.  «
Konnte ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-powerpc/Packages.gz nicht holen  Kann Datei nicht holen, Server antwortete »Failed to open file.  «
Paketlisten werden gelesen... Fertig
W: GPG error: http://kubuntu.org breezy Release: Die folgenden Signaturen konnten nicht überprüft werden weil ihre öffentlichen Schlüssel nicht verfügbar sind: NO_PUBKEY A506E6D4DD4D5088
W: Kann nicht auf die Liste ftp://ftp.free.fr breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-powerpc_Packages) der Quellpakete zugreifen. - stat (2 Datei oder Verzeichnis nicht gefunden)
W: Kann nicht auf die Liste ftp://ftp.free.fr breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-powerpc_Packages) der Quellpakete zugreifen. - stat (2 Datei oder Verzeichnis nicht gefunden)
W: Sie möchten vielleicht »apt-get update« aufrufen, um diese Probleme zu lösen
E: Einige Indexdateien konnten nicht heruntergeladen werden, sie wurden ignoriert oder alte an ihrer Stelle benutzt.

```

The latter error says something like "Couldn't fetch index files, they've been ignored or older ones have been used". The other errors read something like "stat 2 (File or directory not found)".

I checked both sources.list on both machines, and they are the same. Is it just that those PLF repos are not compatible with PPC, or what is the error here?


Any help would be appreciated!

Tom

---

