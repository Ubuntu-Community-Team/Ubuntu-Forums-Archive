---
title: "Upgrade fails"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by lift_test on 2006-12-29
When I try to upgrade following the "sticky" instructions it fails with these error messages:-

Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz) 404 Not Found

[I]'ve noticed these before when using Synaptic,  Is there a solution?

](*,)

---

### Post by Sef on 2006-12-29
Could you post your repositories?

Open the terminal (Applications > Accessories > Teriminal)

Then type this code:

```
gksudo gedit /ect/apt/sources.list
```

---

### Post by taurus on 2006-12-29
You need to comment out that repo in /etc/apt/sources.list by placing a # in front of it (or them if there are more than one line..)

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Save it and update it again.

```
sudo aptitude update
sudo aptitude upgrade
```

p.s.  LOST to Sef this time...

---

### Post by lift_test on 2006-12-29
Thank you both, tried that and machine hung (reminds me of another OS).  Am rebooting to see what happens.

---

### Post by lift_test on 2006-12-30
Commented the 2 lines out and upgraded to Edgy OK but has now hung changing to KDE desktop!
Postfix config, I make a choice, it goes back to dialoge,  make a choice, etc ad infinitum.

Any ideas , apart from pulling the plug out of the socket?

---

