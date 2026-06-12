---
title: "Update Manager - Problem with MergeList"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by rfv-370 on 2011-05-07
Hi,

I have been searching and tried few threads on this issue (problem with merger list) but nothing has worked so far.
I tried : [http://ubuntuforums.org/showthread.php?t=202619](http://ubuntuforums.org/showthread.php?t=202619) ; [http://ubuntuforums.org/showthread.php?t=1559837](http://ubuntuforums.org/showthread.php?t=1559837) and [http://ubuntuforums.org/archive/index.php/t-357256.html](http://ubuntuforums.org/archive/index.php/t-357256.html)

but no luck. I still get :
```

sudo apt-get -f install
Reading package lists... Error!
E: Problem parsing Provides line
E: Error occurred while processing python-pisock (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/fr.archive.ubuntu.com_ubuntu_dists_lucid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```would anybody would have an idea how to get out of the issue ?

Thanks

Robert
PS/ my system is running on a bootable USB drive since over a year now without any issue on 10.04. It started 2 weeks ago and can't find the root cause of it...

---

### Post by dino99 on 2011-05-07
open synaptic config repo to select "main serveur" instead of "fr"

sudo rm /var/cache/apt/archives/*
this clean the sources and index, no worry about the complain

then update again

---

### Post by rfv-370 on 2011-05-07
Well done Dino99!

That worked nicely!

:D

Many Thanks.

---

