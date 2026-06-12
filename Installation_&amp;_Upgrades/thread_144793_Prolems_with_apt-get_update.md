---
title: "Prolems with apt-get update"
date: 2006-03-15
forum: Installation &amp; Upgrades
---

### Post by Knut48 on 2006-03-15
Hello everybody,
I am trying to install Xubuntu and have followed instructions given in [https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu). I could install the server from the Ubuntu-Install-CD without problems. Next step is: "Run the command sudo apt-get update". Doesn't work. Here is what I get:
Hole:1 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy Release.gpg [189B]
Hole:2 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security Release.gpg [189B]
Hole:3 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates Release.gpg [189B]
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy Release
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security Release
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates Release
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/main Packages
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/restricted Packages
Hole:4 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/universe Packages [2304kB]
Ign  [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/universe Packages
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/multiverse Packages
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/main Sources
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/restricted Sources
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/universe Sources
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/multiverse Sources
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security/main Packages
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security/restricted Packages
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security/universe Packages
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security/multiverse Packages
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security/main Sources
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security/restricted Sources
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security/universe Sources
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-security/multiverse Sources
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates/main Packages
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates/restricted Packages
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates/universe Packages
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates/multiverse Packages
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates/main Sources
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates/restricted Sources
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates/universe Sources
OK   [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy-updates/multiverse Sources
Hole:5 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/universe Packages [3028kB]
Fehl [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/universe Packages
  Verbindung erlitt ZeitÃ¼berschreitung
Konnte [http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu/dists/breezy/universe/binary-i386/Packages.gz) nicht holen  Verbindung erlitt ZeitÃ¼berschreitung
Es wurden 3B in 4m7s geholt (0B/s)
Paketlisten werden gelesen...
W: Kann nicht auf die Liste [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/universe Packages (/var/lib/apt/lists/ftp.inf.tu-dresden.de_os_linux_dists_ubuntu_dists_breezy_universe_binary-i386_Packages) der Quellpakete zugreifen. - stat (2 Datei oder Verzeichnis nicht gefunden)
W: Sie mÃ¶chten vielleicht Â»apt-get updateÂ« aufrufen, um diese Probleme zu lÃ¶sen
E: Einige Indexdateien konnten nicht heruntergeladen werden, sie wurden ignoriert oder alte an ihrer Stelle benutzt.

Let me translate some of the messages from German.
"Hole" means "Get".
"Ign" means Ignore, I suppose.
"Fehl" is for "Error", "Verbindung erlitt Zeitüberschreitung" = "Connection timed out"
"Konnte [http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu/dists/breezy/universe/binary-i386/Packages.gz) nicht holen" = "Could not fetch [http://ftp](http://ftp). ..."
"W: Kann nicht auf die Liste [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/universe Packages (/var/lib/apt/lists/ftp.inf.tu-dresden.de_os_linux_dists_ubuntu_dists_breezy_universe_binary-i386_Packages) der Quellpakete zugreifen. - stat (2 Datei oder Verzeichnis nicht gefunden)"
means 
"W: Cannot access the list [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) breezy/universe Packages (/var/lib/apt/lists/ftp.inf.tu-dresden.de_os_linux_dists_ubuntu_dists_breezy_universe_binary-i386_Packages)
of the packages in the source - stat( 2 File or Directory not found)".

I have already posted this problem to our local forum at [http://forum.ubuntuusers.de/](http://forum.ubuntuusers.de/) and together with some helpful friend there I already tried the following: 
Changing the server adress in sources.list (result is the same)
I made a ping to the ftp-server - connection is good.

I cannot get over this point and install the Xubuntu-destop. Please help!
Oh, and I am a Linux-beginner.

Best regards
Knut

---

### Post by Stemp on 2006-03-15
why not [ftp://ftp.inf.tu-dresden.de/](ftp://ftp.inf.tu-dresden.de/) ?

---

### Post by Knut48 on 2006-03-15
Don't know, I copied it. You think it's worth trying to change the sources.list?
Regards
Knut
OK... now I did try... Same result. There is an additional error message:
Could not fetch [ftp://...universe/binary-i386/Packages.gz](ftp://...universe/binary-i386/Packages.gz). Subprocess bzip2 returned with error (2),     but the rest is the same.

---

### Post by Stemp on 2006-03-15
And what about changing your repositery ? using archive.ubuntu ? 

```
# Breezy 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

# Breezy Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
```

---

### Post by Knut48 on 2006-03-15
Hello Stemp,
same result, except: now I have got "Ignores" and "Time-outs" and "Could not access" not only for the universe Packages but also for the main packages.
Regards
Knut

---

