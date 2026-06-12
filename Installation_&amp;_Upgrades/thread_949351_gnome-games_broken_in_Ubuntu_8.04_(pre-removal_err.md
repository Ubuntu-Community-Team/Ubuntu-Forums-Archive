---
title: "gnome-games broken in Ubuntu 8.04 (pre-removal error)"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by subheaven on 2008-10-16
I have a problem with gnome-games 1:2.22.1.1-0ubuntu3 (running Ubuntu 8.04). Synaptic, apt-get and dpkg can't remove or upgrade the package. dpkg seems to produce most output, given below. How do I get rid of this package? Can I remove a package without pre/post (un)install scripts?

I can't do any changes on the package system now anymore.

Cheers




sudo dpkg -r gnome-games 
dpkg: status database area is locked by another process
lukas@emu:~$ sudo dpkg -r gnome-games
(Reading database ... 225472 files and directories currently installed.)
Removing gnome-games ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1891, in <module>
    main()
  File "/usr/bin/pycentral", line 1885, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1404, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 707, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing gnome-games (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gnome-games

---

### Post by subheaven on 2008-10-16
Though I've been trying a lot, I found a post helping me to remove the package.

Go to /var/lib/dpkg/info and create and empty gnome-games.prerm script. Then apt-get install gnome-games gnome-games-data

---

