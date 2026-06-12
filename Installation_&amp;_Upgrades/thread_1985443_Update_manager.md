---
title: "Update manager"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2012-05-23
I get frequently:

The action would require the installation of packages from not authenticated sources.

How to solve that?

---

### Post by cortman on 2012-05-23
You might be missing some GPG keys.
Run

```
sudo apt-get update
```

and post back the results so we can see which ones.

---

### Post by ELMIT on 2012-06-02
Many program I could not download anymore from the Taiwan archive, so I switched to the Main arichive, but still I get many for many things "not found"

```
sudo apt-get update >update-list

W: Failed to fetch [http://ppa.launchpad.net/bjfs/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/bjfs/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bjfs/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/bjfs/ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bjfs/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/bjfs/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found


cat update-list
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]
Get:3 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,239 B]
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,226 B]
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Hit [http://repository.spotify.com](http://repository.spotify.com) stable InRelease
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg [198 B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg [198 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Get:8 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender InRelease
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free TranslationIndex
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release [49.6 kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Hit [http://deb.opera.com](http://deb.opera.com) stable Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages
Hit [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender Release.gpg
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex
Hit [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release [49.6 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources [934 kB]
Hit [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [997 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [1,289 B]
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [1,298 B]
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages
Ign [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources [5,470 B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources [5,019 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources [155 kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages [1,273 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages [8,452 B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages [4,786 kB]
Ign [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free Translation-en_US
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages [119 kB]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages [1,274 kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US
Ign [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free Translation-en
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources [94.1 kB]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources [1,379 B]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources [18.0 kB]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources [696 B]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages [220 kB]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages [2,417 B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages [54.1 kB]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages [1,578 B]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [221 kB]
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [2,439 B]
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [54.7 kB]
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [1,802 B]
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [74 B]
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex [71 B]
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex [71 B]
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex [73 B]
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Sources [700 B]
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Sources [6,109 B]
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Sources [1,383 B]
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main amd64 Packages [559 B]
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe amd64 Packages [5,200 B]
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse amd64 Packages [996 B]
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages [559 B]
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages [5,227 B]
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources [13.7 kB]
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources [14 B]
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources [4,522 B]
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources [696 B]
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main amd64 Packages [44.0 kB]
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted amd64 Packages [14 B]
Get:65 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe amd64 Packages [11.0 kB]
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse amd64 Packages [1,142 B]
Get:67 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages [45.0 kB]
Get:68 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:69 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages [10.9 kB]
Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages [1,393 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Fetched 19.5 MB in 37s (522 kB/s)
E: Some index files failed to download. They have been ignored, or old ones used instead.
```


Thanks for  your help!

---

### Post by raja.genupula on 2012-06-02
open update manager -> settings -> in the 1st TAB at download from change your server to main server or best server and try again .

all the best , :)

---

### Post by wilee-nilee on 2012-06-02
With only a check on the first PPA fail, bjfs/ppa, this one does not have a precise release, check every one to see if they support your release.

[https://launchpad.net/~bjfs/+archive/ppa](https://launchpad.net/~bjfs/+archive/ppa)

---

### Post by ELMIT on 2012-06-04
Checked, ... don't exist.

So what is the solution?

---

### Post by plucky on 2012-06-04
> Checked, ... don't exist.

So what is the solution? 


Remove all the PPAs that are giving the 404 Not Found errors as they probably don't have a repository for the Precise release.

Good Luck

---

