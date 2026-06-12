---
title: "Failed to update"
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by batrachian on 2005-09-28
follow the unofficial guide to get update:

"sudo apt-get update"

The following error message is found.  Can anyone help a newbie out on this?


Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main) /binary-i386/Packages.gz  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/univ](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/univ) erse/binary-i386/Packages.gz  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/mult](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/mult) iverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/rest](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/rest) ricted/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dist s_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory )
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dist s_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory )
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.

---

### Post by Leif on 2005-09-28
backports mirrors are being taken down. see [http://ubuntuforums.org/showthread.php?t=69681](http://ubuntuforums.org/showthread.php?t=69681)

---

