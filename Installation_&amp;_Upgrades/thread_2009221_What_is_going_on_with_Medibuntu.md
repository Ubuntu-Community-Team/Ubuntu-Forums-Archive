---
title: "What is going on with Medibuntu"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by BigBaka on 2012-06-24
I try and follow these [instructions]("http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/") after re-installing 12.04 and am getting these crazy error messages with medibuntu. When i type in the following command

> sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

I get this error message

> jvc@CountryRep:~$ sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for jvc: 
--2012-06-24 18:54:38--  [http://www.medibuntu.org/sources.list.d/precise.list](http://www.medibuntu.org/sources.list.d/precise.list)
Resolving [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org](www.medibuntu.org))... 88.191.127.22
Connecting to [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org)|88.191.127.22|:80](www.medibuntu.org)|88.191.127.22|:80)... failed: Connection timed out.
Retrying.

--2012-06-24 18:55:43--  (try: 2)  [http://www.medibuntu.org/sources.list.d/precise.list](http://www.medibuntu.org/sources.list.d/precise.list)
Connecting to [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org)|88.191.127.22|:80](www.medibuntu.org)|88.191.127.22|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 284 [text/plain]
Saving to: '/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 284         --.-K/s   in 0s      

2012-06-24 18:55:44 (22.0 MB/s) - '/etc/apt/sources.list.d/medibuntu.list' saved [284/284]

Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_AU
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
  Unable to connect to extras.ubuntu.com:http:
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_AU
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
  Unable to connect to extras.ubuntu.com:http:
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise InRelease
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates InRelease
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports InRelease
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise Release.gpg
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates Release.gpg
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports Release.gpg
  Unable to connect to la.archive.ubuntu.com:http:
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise Release
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates Release
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports Release
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/main Sources/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/restricted Sources/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/universe Sources/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/multiverse Sources/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/main i386 Packages/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/main TranslationIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/multiverse TranslationIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/restricted TranslationIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/universe TranslationIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/main Sources/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/restricted Sources/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/universe Sources/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse Sources/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/main i386 Packages/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/restricted i386 Packages/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/universe i386 Packages/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse i386 Packages/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/main TranslationIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/universe TranslationIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/main Sources/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/restricted Sources/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/universe Sources/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/multiverse Sources/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/main i386 Packages/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/restricted i386 Packages/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/universe i386 Packages/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/multiverse i386 Packages/DiffIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/main TranslationIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/universe TranslationIndex
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/main Sources
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/restricted Sources
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/universe Sources
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/multiverse Sources
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/main i386 Packages
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/restricted i386 Packages
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/universe i386 Packages
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/multiverse i386 Packages
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/main Translation-en_AU
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/main Translation-en
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/multiverse Translation-en_AU
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/multiverse Translation-en
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/restricted Translation-en_AU
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/restricted Translation-en
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/universe Translation-en_AU
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/universe Translation-en
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/main Sources
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/restricted Sources
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/universe Sources
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse Sources
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/main i386 Packages
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/restricted i386 Packages
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/universe i386 Packages
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse i386 Packages
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/main Translation-en_AU
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/main Translation-en
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse Translation-en_AU
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse Translation-en
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/restricted Translation-en_AU
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/restricted Translation-en
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/universe Translation-en_AU
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/universe Translation-en
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/main Sources
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/restricted Sources
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/universe Sources
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/multiverse Sources
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/main i386 Packages
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/restricted i386 Packages
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/universe i386 Packages
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/multiverse i386 Packages
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/main Translation-en_AU
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/main Translation-en
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/multiverse Translation-en_AU
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/multiverse Translation-en
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/restricted Translation-en_AU
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/restricted Translation-en
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/universe Translation-en_AU
  Unable to connect to la.archive.ubuntu.com:http:
Err [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/universe Translation-en
  Unable to connect to la.archive.ubuntu.com:http:
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Sources
  Unable to connect to packages.medibuntu.org:http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Sources
  Unable to connect to packages.medibuntu.org:http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages
  Unable to connect to packages.medibuntu.org:http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages
  Unable to connect to packages.medibuntu.org:http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_AU
  Unable to connect to packages.medibuntu.org:http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
  Unable to connect to packages.medibuntu.org:http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_AU
  Unable to connect to packages.medibuntu.org:http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
  Unable to connect to packages.medibuntu.org:http:
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
  Unable to connect to security.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
  Unable to connect to security.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
  Unable to connect to security.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
  Unable to connect to security.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
  Unable to connect to security.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en_AU
  Unable to connect to security.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
  Unable to connect to security.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en_AU
  Unable to connect to security.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
  Unable to connect to security.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en_AU
  Unable to connect to security.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
  Unable to connect to security.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en_AU
  Unable to connect to security.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
  Unable to connect to security.ubuntu.com:http:
Fetched 316 B in 1min 8s (4 B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/source/Sources](http://packages.medibuntu.org/dists/precise/free/source/Sources)  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/source/Sources](http://packages.medibuntu.org/dists/precise/non-free/source/Sources)  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_AU](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_AU)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://la.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://la.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://la.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://la.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://la.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://la.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://la.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://la.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://la.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_AU](http://la.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_AU)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://la.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_AU](http://la.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_AU)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en](http://la.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_AU](http://la.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_AU)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en](http://la.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_AU](http://la.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_AU)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en](http://la.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_AU](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_AU)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_AU](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_AU)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_AU](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_AU)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_AU](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_AU)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en](http://la.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_AU](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_AU)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_AU](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_AU)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_AU](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_AU)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_AU](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_AU)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en](http://la.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en)  Unable to connect to la.archive.ubuntu.com:http:

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_AU](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_AU)  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_AU](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_AU)  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_AU](http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_AU)  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en)  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_AU](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_AU)  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en)  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_AU](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_AU)  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en)  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_AU](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_AU)  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en)  Unable to connect to security.ubuntu.com:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.

What on earth is going on!!??
BB

---

### Post by coffeecat on 2012-06-24
There's nothing wrong with medibuntu. You are getting unable to connect messages with la.archive.ubuntu, extras.ubuntu, and security.ubuntu as well as medibuntu. Looking at your apt-get output, it looks like an intermittent connectivity problem - getting worse towards the end. Are you having any other problems with the internet?

---

### Post by BigBaka on 2012-06-24
hmmm, could be that, although I have no problems browsing Internet, using this forum etc.

The internet here is pretty slow only 256 kbps ADSL. Could try and move to an internet cafe that I know has fast speeds.

Will keep you posted.

Regards,
BB

---

### Post by BigBaka on 2012-06-24
Doh, you're right. 

I guess my crappy Internet at home is really crappy!

Thanks for the observation.

---

### Post by coffeecat on 2012-06-24
You're welcome!

Good luck with updating at the internet cafe.

---

### Post by BigBaka on 2012-06-24
Maybe I spoke to soon.

Still got this error message at the end of everything

> Fetched 6,374 kB in 9min 37s (11.0 kB/s)
Reading package lists...
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,448 B of archives.
After this operation, 49.2 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Err [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise/free medibuntu-keyring all 2008.04.20
  Could not connect to packages.medibuntu.org:80 (88.191.127.22). - connect (110: Connection timed out)
Failed to fetch [http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb](http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb) Could not connect to packages.medibuntu.org:80 (88.191.127.22). - connect (110: Connection timed out)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Any advice appreciated

---

### Post by BigBaka on 2012-06-24
I tried to run the same command in terminal again, now at the internet cafe, 

and at package 24 I get this error that seems to be associated with medibuntu.

> Get:24 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_AU
  Unable to connect to packages.medibuntu.org:http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
  Unable to connect to packages.medibuntu.org:http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_AU
  Unable to connect to packages.medibuntu.org:http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
  Unable to connect to packages.medibuntu.org:http:

Is this anything?

---

### Post by coffeecat on 2012-06-24
medibuntu is resolving for me so the medibuntu server is not down, which can sometimes be the problem with any repository. The forum software has made links out of the medibuntu URLs - try clicking on one of them in your post, or this:

[http://packages.medibuntu.org](http://packages.medibuntu.org)

Also - post the output of this terminal command to check the medibuntu sources file:

```
/etc/apt/sources.list.d/medibuntu.list
```

---

### Post by BigBaka on 2012-06-24
jvc@CountryRep:~$ /etc/apt/sources.list.d/medibuntu.list
bash: /etc/apt/sources.list.d/medibuntu.list: Permission denied


The URL to the medibuntu packages worked no problem though.

---

### Post by coffeecat on 2012-06-24
Oops sorry. My bad. That terminal command should have been:

```
cat /etc/apt/sources.list.d/medibuntu.list
```

Another thought. I've given up adding medibuntu to my repositories since the medibuntu packages I use don't need upgrading. One thing you could do is simply click on that link, click on the Precise link, and then download whichever .deb packages you need and install them with Software Center by double-clicking on them.

---

### Post by BigBaka on 2012-06-24
> jvc@CountryRep:~$ cat /etc/apt/sources.list.d/medibuntu.list
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"

yeah, that it certainly an option to do it that way I guess.

to remove medibuntu I should just go into the ppa and delete the medibuntu lines? the sudo apt-get update?

---

### Post by coffeecat on 2012-06-24
The medibuntu.list file looks OK so I don't know why you were getting unable to connect message with medibuntu. Perhaps another unrelated glitch with connectivity. It might be worth trying again.

If you want to disable the medibuntu repository, you can hand edit the medibuntu.list file, simply putting a '#' character at the beginning of the second line. Or open either Update Manager -> click on settings button, or Software Center -> Edit menu -> Software Sources. Then simply untick the medibuntu box, close either Update Manager or Software Sources and do a "sudo apt-get update".

---

