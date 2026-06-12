---
title: "The following packages have been kept back:   sg3-utils"
date: 2009-07-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wayne_cat on 2009-07-12
anybody else with this message?

```
root@macbook:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  sg3-utils
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by ghindo on 2009-07-12
It's being held back for me too.  It doesn't look like the changelog has been updated yet either, if I'm not mistaken.

---

### Post by paul_in_london on 2009-07-12
In my case, I get this:

```
paul@karmic-sdb:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following packages are BROKEN:
  devicekit-disks 
The following NEW packages will be installed:
  libsgutils2-2{a} 
The following packages will be REMOVED:
  libsgutils2{a} 
The following packages will be upgraded:
  sg3-utils 
1 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 595kB of archives. After unpacking 4096B will be freed.
The following packages have unmet dependencies:
  devicekit-disks: Depends: libsgutils2 (>= 1.27~repack) but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
sg3-utils

Keep the following packages at their current version:
libsgutils2 [1.27~repack-0ubuntu2 (karmic, now)]
libsgutils2-2 [Not Installed]

Leave the following dependencies unresolved:
libsgutils1 recommends sg3-utils
Score is -1

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
paul@karmic-sdb:~$ 

```

---

### Post by pferraro on 2009-07-12
The new sg3-utils package replaces libsgutils2 with libsgutils2-2.  The devicekit-disks package still depends on the package to be replaced - hence the hold up.

---

### Post by wayne_cat on 2009-07-12
> **ghindo said:**
> It's being held back for me too.  It doesn't look like the changelog has been updated yet either, if I'm not mistaken.

I have found this:

[http://www.mail-archive.com/karmic-changes@lists.ubuntu.com/msg03618.html](http://www.mail-archive.com/karmic-changes@lists.ubuntu.com/msg03618.html)

---

### Post by ranch hand on 2009-07-12
I have been updating 9.10 through synaptic for the information I get there.

When this update would not be marked and gave libsgutils2-2 as the dependency I looked it up.  It is in the repos for 9.10.  Marked it for installation and hit apply.

The confirm box was very entertaining.  I did not read all the packages to be removed but there were a truckload of them.  Would have freed up a lot of space while gutting the OS.

Wait a few days and they will catch up to this.  It is obviously a known problem or synaptic would not say that it was not going to be updated because it depends on libsgutils2-2 which is not going to be installed even though it is available in the repo.  Obviously the many other things that are hooked to libsgutils2 need to be fixxed to work with libsgutils2-2 or it needs fixed to work with them.

---

### Post by afv on 2009-07-13
Upgradable now. :)

> 
…
The following NEW packages will be installed:
  libsgutils2-2{a} 
The following packages will be REMOVED:
  libsgutils2{u} 
The following packages will be upgraded:
  devicekit-disks sg3-utils 
…


---

