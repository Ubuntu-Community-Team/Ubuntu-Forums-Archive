---
title: "upgrading 6.06 lts to 8.04 problem"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by birdman3131 on 2008-08-23
sorry for the bad spelling but ff 1.5 seems to be short one spellchecker

ok i am trying to upgrade to the latest version of ubuntu. (8.04?)

i have a pretty much clean install of 6.06 on this that ive never used because i tend to use windows but windows was on a separate drive that crashed.

i am trying to follow this guide [http://www.ubuntu.com/getubuntu/upgrading#head-e48a0e69b52e605383bbfc727322f8d0ce0f7d99-2](http://www.ubuntu.com/getubuntu/upgrading#head-e48a0e69b52e605383bbfc727322f8d0ce0f7d99-2)

now im not entirely sure what the "dapper-updates" software channel is but i went to system > administration > synaptics package manager > settings > repositorys > and selected everything under instalation media.

i then run ```
gksu "update-manager -d"
``` in the terminal.
it says your system is up to date (i installed a couple hundred megs of updates last night.) and gives me the option to upgrade to 8.04

when i go to upgrade sometime during the "setting up new software channels" step it quites and gives me this error message.
```
W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/source/Sources.bz2  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

i do not have any cds avalible to burn an iso to or i would do it that way.

---

### Post by overdrank on 2008-08-23
Hi and you may try and change your server location, under system, administration, software sources. Download location.

---

