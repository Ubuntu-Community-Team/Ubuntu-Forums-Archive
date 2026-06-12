---
title: "Problem Upgrading from 7.04 to 7.10"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by treblesix on 2007-10-23
I am trying to upgrade my Feisty to Gutsy, but when the upgrade installer runs, it does the first part in the list, then i get this ....................


[B]Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.[/B]

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found

Anyone got any ideas ?

---

### Post by Stemp on 2007-10-23
Medibuntu moved, check [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by treblesix on 2007-10-23
Cheers,

That has worked now :)

I cannot open my local Vmware sessions now though. Remote ones seem fine.

Any ideas on that?

---

### Post by Stemp on 2007-10-23
> **treblesix said:**
> 
I cannot open my local Vmware sessions now though. Remote ones seem fine.

Any ideas on that?

Nope, sorry ;)

---

### Post by jeff-- on 2007-10-23
Hi, I'm having this same problem but I don't really understand what to do on that website.  If you could elaborate a little that would be great. :)

edit: just to explain a little more, I mean the original problem of failed to fetch from medibuntu.  Thanks for any help. :)

---

### Post by Stemp on 2007-10-23
Menu System, Administration,  Software sources....
Third party (parties ?)
Change medibuntu.sos-sts.com to fr.packages.medibuntu.org

---

### Post by jeff-- on 2007-10-23
Thanks!  So far that worked, I got passed that step and am in the process of "fetching the upgrade"...:D

---

### Post by defenestratos on 2007-11-01
> **Stemp said:**
> Menu System, Administration,  Software sources....
Third party (parties ?)
Change medibuntu.sos-sts.com to fr.packages.medibuntu.org

I got a problem now and i can't seem to get update manager to work. I get

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 15 in source list /etc/apt/sources.list.d/easyubuntu.list (URI parse), E:The list of sources could not be read.'

When I update in Software sources, I get
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

and then it tells me an  error occurred

E: Malformed line 15 in source list /etc/apt/sources.list.d/easyubuntu.list (URI parse)
E: Unable to lock the list directory

What gives? I'd like to fix my system so that I can check out the new rat distro

---

### Post by Stemp on 2007-11-01
Just erase the easyubuntu lines ;)

```
sudo rm /etc/apt/sources.list.d/easyubuntu.list
```

---

### Post by Lorenia on 2008-01-22
I've had a similar problem, defenestratos.

I was in Spain and am now in Cancun, tried choosing a repository which was closer to me here so it would download more quickly, and got this when I chose a new repository when I wanted to upgrade to 7.10.

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 5 in source list /etc/apt/sources.list (URI parse), E:The list of sources could not be read.'

That from the Update Manager and this from Synaptic:

E: Malformed line 5 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Frustration!

---

