---
title: "Problem upgrading to 7.10 with alternate CD"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by argusBR on 2007-10-20
I tried to update 2 Ubuntu boxes with Feisty, using the alternate CD. They are not connected to the Internet.

For both computers, I get the following message in the GUI:

```

"Could not calculate the upgrade"
"A unresolvable problem occurred while calculating the upgrade. Please report this bug against the update manager" package and include the files in /var/log/dist-upgrade in the bug report"

```

The file main.log in that folder ends with the following error:

```

Can't mark 'ubuntu-desktop' for upgrade (E:Unable to correct problems, you have held broken packages.)

```

I connected the first machine to the Internet, and upgraded through "System->Upgrade Manager", and it worked all right, after ages of downloading (it seems there was no problem with ubuntu-desktop: Synaptic did not show it as held).

Isn't it possible to upgrade to 7.10 using the alternate CD, without a connection to the Internet?

---

### Post by ruibernardo on 2007-10-21
> **argusBR said:**
> 
```

Can't mark 'ubuntu-desktop' for upgrade (E:Unable to correct problems, you have held broken packages.)

```it seems there was no problem with ubuntu-desktop: Synaptics did not show it as held).

Apparently the problem is not directly related to the ubuntu-desktop package, but with one of its dependencies. Check fo broken packages with Synaptic (menu Edit, Broken packages) or with

```
sudo apt-get check
```This might be related with packages you have installed that are not available in the Alternate CD.

---

### Post by argusBR on 2007-10-21
I tried apt-get check, but there seems to be no problem:

```

sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

Having a look at apt.log (in /var/log/dist-upgrade), the final section looks suspect:
```
Starting
Starting 2
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on ttf-dejavu-core
  Considering ttf-dejavu-core 1 as a solution to ubuntu-desktop 0
  Re-Instated ttf-dejavu-core
  Re-Instated ubuntu-desktop
Investigating ttf-dejavu-core
Package ttf-dejavu-core has broken dep on ttf-dejavu
  Considering ttf-dejavu 4 as a solution to ttf-dejavu-core 1
  Holding Back ttf-dejavu-core rather than change ttf-dejavu
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on ttf-dejavu-core
  Considering ttf-dejavu-core 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change ttf-dejavu-core
Done
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating vlc
Package vlc has broken dep on ttf-dejavu
  Considering ttf-dejavu 2 as a solution to vlc 3
  Added ttf-dejavu to the remove list
  Fixing vlc via keep of ttf-dejavu
Investigating ttf-dejavu-core
Package ttf-dejavu-core has broken dep on ttf-dejavu
  Considering ttf-dejavu 2 as a solution to ttf-dejavu-core 0
  Holding Back ttf-dejavu-core rather than change ttf-dejavu
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on ttf-dejavu-core
  Considering ttf-dejavu-core 0 as a solution to ubuntu-desktop 10000
  Re-Instated ttf-dejavu-core
Investigating ttf-dejavu-core
Package ttf-dejavu-core has broken dep on ttf-dejavu
  Considering ttf-dejavu 2 as a solution to ttf-dejavu-core 0
  Holding Back ttf-dejavu-core rather than change ttf-dejavu
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on ttf-dejavu-core
  Considering ttf-dejavu-core 0 as a solution to ubuntu-desktop 10000
Done
```

As far as I know, the package ttf-dejavu-core didn't exist in Feisty (at least, I could't find it in [http://packages.ubuntu.com/feisty/allpackages](http://packages.ubuntu.com/feisty/allpackages)).

---

### Post by argusBR on 2007-10-21
Solved!

I uninstalled vlc, and the upgrade ran without problems.

Thank you, epimeteo!

---

