---
title: "build-essential woes - hash sum mismatches?"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by Nancarrow on 2008-06-23
Hi, I'm coming back to Linux after a five-year hiatus. I've attempted to install Ubuntu-7.10, aka 'Gutsy'. It's ok but I will need to compile source-code, for which I've gathered I need to type 'apt-get install build-essential' in a terminal, to get the required packages installed. There's where my problems start.

Five packages that build-essential depends on, won't install. They're linux-libc-dev, libc6-dev, g++, g++-4.1, and libstdc++6-4.1. For all of them it tells me there was a 'hash sum mismatch'.

I have tried downloading these packages from the ubuntu packages repository. linux-libc-dev *appears not to exist* - whenever I click a link to a mirror site, I get a 'not found' error.

Does anyone know how I can fix this? Please note I can only access the internet through Windows at the moment, not my new Ubuntu distro.

Thanks in advance.

---

### Post by Nancarrow on 2008-06-23
OK never mind I fixed it! I got my wireless internet connection working under ubuntu, then ran Synaptic package manager, turned off the CD-ROM lookup and got it to do everything off the net.

---

