---
title: "Package management broken."
date: 2014-11-19
forum: Installation &amp; Upgrades
---

### Post by aFoxNamedMorris on 2014-11-19
Heya, everybody. Well, I installed the Oibaf graphics PPA and everything seemed fine at first. Now my system is refusing to fix a dependency while upgrading the packages from said PPA. I've tried running with -f, I've tried the now broken ppa-purge utility... nothing is working. Please help.

```
aaronmorris@f0xb0x:~$ sudo apt-get -f install [sudo] password for aaronmorris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libfltk1.1
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  libgl1-mesa-dri
The following packages will be upgraded:
  libgl1-mesa-dri
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
14 not fully installed or removed.
Need to get 0 B/5,446 kB of archives.
After this operation, 5,634 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 352073 files and directories currently installed.)
Preparing to unpack .../libgl1-mesa-dri_10.5~git1411191810.9460cd~gd~t_amd64.deb ...
Unpacking libgl1-mesa-dri:amd64 (10.5~git1411191810.9460cd~gd~t) over (10.4~git1411171930.920f87~gd~t) ...
dpkg: error processing archive /var/cache/apt/archives/libgl1-mesa-dri_10.5~git1411191810.9460cd~gd~t_amd64.deb (--unpack):
 trying to overwrite directory '/usr/lib/x86_64-linux-gnu/pkgconfig' in package libgl1-mesa-dev:amd64 10.5~git1411191810.9460cd~gd~t with nondirectory
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa-dri_10.5~git1411191810.9460cd~gd~t_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
aaronmorris@f0xb0x:~$ 





```

---

### Post by MERB on 2014-11-20
Exact same thing happening to me. Just tried to add the repository and update. I then tried to ppa-purge it and ran into the same error you're seeing.

---

### Post by jhay2 on 2014-11-20
anyone able to fix this problem ?    i have the same issue now :(

---

### Post by MERB on 2014-11-20
> **jhay2 said:**
> anyone able to fix this problem ?    i have the same issue now :(

Check this link: [http://www.phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers/page140](http://www.phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers/page140)

Looks like it's been fixed.

---

### Post by QIII on 2014-11-20
It might be worthwhile to read [this.]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers")

There is a debugging and bug reporting section.

Cheers!

---

### Post by jhay2 on 2014-11-20
> **MERB said:**
> Check this link: [http://www.phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers/page140](http://www.phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers/page140)

Looks like it's been fixed.

thanks for the link .. :)

---

### Post by chick2 on 2014-11-20
I fixed this with 

sudo dpkg -i --force-overwrite /var/cache/apt/archives/libgl1-mesa-dri_10.5~git1411191810.9460cd~gd~t_amd64.deb

---

### Post by zika on 2014-11-20
Forced overwrite did not help. New package edition did help. Thank You Oibaf.

---

### Post by aFoxNamedMorris on 2014-11-20
Heh.. So it gets fixed while I was reinstalling the OS and dropping my home folder back in. XD Typical me. Though, for the record, I think there's something to be said for staying away from "nightly", "daily", or "beta" PPA's. I mean, these kinds of problems can be system breaking. I'm not telling everyone to stop using the Oibaf graphics repo, I am however saying that it's for those who are willing to take a risk.

---

