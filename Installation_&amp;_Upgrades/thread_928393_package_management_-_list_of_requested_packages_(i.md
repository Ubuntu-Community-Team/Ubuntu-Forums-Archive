---
title: "package management - list of requested packages (i.e. without dependencies)"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by scottsmith77 on 2008-09-23
I've been a user of Ubuntu for about 6 months (other distros - 10 years).

What I don't understand is how to generate a list of packages which I've explicitly requested - just to have a list for recovery purposes (as a side note, I have /home backed up, and all desired configs in /etc and /var - just want a list of packages needed for reinstall).

I have seen:
```
$ dpkg --get-selections
```
But that lists ALL installed packages, including dependencies. So if I use that list for reinstall, all the dependencies are now explicitly requested, and can't be autoremoved if the 

I also know about the debfoster package, but shouldn't it be easier than that? If I have debfoster, and I forget and use "apt-get" to install something, are my debfoster lists messed up?

Also, the dependecy information exists somehow - if I install googleearth, then purge it, the system knows that installed dependencies might need to be removed:
```
ssmith@laptop:~$ sudo apt-get purge -s googleearth
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  googleearth-4.2 googleearth-4.2-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  googleearth*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Purg googleearth [4.3.7204.836-0medibuntu1]
```
So based on that output, it seems like there should be a list of *requested* packages somewhere... but where?

---

### Post by Dave.G on 2008-10-27
I was hunting around for the answer to this today, and I've found a solution. Install the package "deborphan" and do:```
$ deborphan -a
```This will list all top-level (i.e. no one depends on it) packages it detects. This works much better than I expected, because Ubuntu has a few top-level meta packages for the default packages. The packages listed alongside the meta packages are the ones not in the defaults: the ones you installed.

Note that this works nicely but isn't perfect. For example, I've installed abiword and that requires a "-n" added to the command to list it along with quite a lot of unneeded other stuff. I've also installed msttcorefonts and that doesn't show in the list even with "-n". So, don't rely entirely on this list, but it's useful to get the main stuff.

---

### Post by scottsmith77 on 2008-10-27
Dave.G

Thanks! As you state, it's not perfect, but it is good enough to get me a mostly complete list of what I've installed.

---

