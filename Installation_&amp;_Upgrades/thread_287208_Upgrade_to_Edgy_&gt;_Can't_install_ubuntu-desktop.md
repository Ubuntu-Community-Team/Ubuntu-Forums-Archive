---
title: "Upgrade to Edgy &gt; Can't install ubuntu-desktop"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by 4nT0 on 2006-10-28
I tried to upgrade from Dapper to Edgy with "update-manager -c", but some servers didn't work.

So I then upgraded with cdrom. All was right till the end. But after a reboot, 4 updated packages for me show up. When I click it says he can't install them before doing a distribution upgrade (that I've already done, my ubuntu is now 'mostly' a 6.10!).

Anyway, when I accept to do a distro upgrade an error occours:

> Can't install 'ubuntu-desktop'
Notify this event as a bug.

and then

> An unsolvable error occurred while calculating upgrade. Notify this event as a bug regarding the packet "update manager" and include files from /var/log/dist-upgrade.
Notify this event as a bug.

Files are in the attached archive.

What should I do now?

Thank you in advance! :)

---

### Post by 4nT0 on 2006-10-28
ops, sorry... I forgot attachment... here it is.

---

### Post by garrido on 2006-11-23
I have the same problem....  The problem seems to be related to the xorg-xserver package.  This is what it says when I try to install ubuntu-desktop:

```
 ubuntu-desktop: Dependency: xorg but this will not be installed
```

Do I have to uninstall X and then try it?  I don't want to try this for fear that all my nice XGL/Compiz stuff will break...

---

### Post by Carl Petersen on 2006-11-25
Same problem. Anyone know of a work around? Here's the relevant section of the log file:

Starting
Starting 2
Investigating libgl1-mesa-dri
Package libgl1-mesa-dri has broken dep on libgl1-mesa
  Considering libgl1-mesa 3 as a solution to libgl1-mesa-dri 1
  Removing libgl1-mesa-dri rather than change libgl1-mesa
Investigating xorg
Package xorg has broken dep on libgl1-mesa-dri
  Considering libgl1-mesa-dri 1 as a solution to xorg 1
  Holding Back xorg rather than change libgl1-mesa-dri
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on xorg
  Considering xorg 1 as a solution to ubuntu-desktop 9999
    Reinst Failed because of libgl1-mesa-dri
Done

---

### Post by Vevmesteren on 2007-01-28
same problem here. Has anyone found a solution....please?


```

sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: xorg but it is not going to be installed
E: Broken packages

```

---

