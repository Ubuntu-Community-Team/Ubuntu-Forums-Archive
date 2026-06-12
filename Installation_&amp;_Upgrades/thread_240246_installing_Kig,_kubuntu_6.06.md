---
title: "installing Kig, kubuntu 6.06"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by mazo on 2006-08-20
I tried to install the Kig package (using adept or aptitude), but the installation failed:

  --\ Depends
    --- kdelibs4c2 (>= 4:3.4.3) (UNAVAILABLE)
    --- libart-2.0-2 (>= 2.3.16)
    --- libaudio2
    --- libboost-python1.33.0 (< 1.32.0+1.33.0-cvs20050727-99) (UNAVAILABLE)
    --- libboost-python1.33.0 (>= 1.32.0+1.33.0-cvs20050727-0) (UNAVAILABLE)
    --- libc6 (>= 2.3.4-1)
    --- libfontconfig1 (>= 2.3.0)
    --- libfreetype6 (>= 2.1.5-1)
    --- libgamin0
    --- libgcc1 (>= 1:4.0.1)
    --- libice6
    --- libidn11 (>= 0.5.13)
    --- libjpeg62
    --- libpng12-0 (>= 1.2.8rel)
    --- libqt3-mt (>= 3:3.3.4)
    --- libsm6
    --- libstdc++6 (>= 4.0.1)
    --- libx11-6
    --- libxcursor1 (> 1.1.2)
    --- libxext6
    --- libxft2 (> 2.1.1)
    --- libxi6
    --- libxinerama1
    --- libxrandr2
    --- libxrender1
    --- libxt6
    --- python2.4 (>= 2.3.90)
    --- zlib1g (>= 1:1.2.1)
  --\ Suggests
    --- kdeedu-doc-html (UNAVAILABLE)
    --- khelpcenter
  --\ Recommends
    --- kdeedu-data (>= 4:3.4.3-0ubuntu2) (UNAVAILABLE)
  --- Packages which depend on kig
  --\ Versions

So there are some missing packages unavailable at standard ubuntu repository (main, universe, ...). What should I do to install kdeedu and kig properly? (Please write me your replies also to j.mazak at gmail.com, maybe I will forget to read your reply if you write it only here.)

---

### Post by linear on 2006-08-20
Check the contents of sources.list (or post here so others can look it over).  The dependencies should all be in the repositories.

---

