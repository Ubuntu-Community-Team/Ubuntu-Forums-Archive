---
title: "Problem upgrading to 6.10"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by sandbagger on 2007-01-31
I'm trying to upgrade my work PC from 6.06 to 6.10 using gksu "update-manager -c".
After it does a bit of downloading I get this message, "Failed to fetch [http://ubuntu.beryl-project.org/dists/dapper/Release](http://ubuntu.beryl-project.org/dists/dapper/Release) Unable to find expected entry  aiglx/binary-i386/Packages in Meta-index file (malformed Release file?)".
The upgrade doesn't go any further than that. Any advice would be appreciated.

---

### Post by taurus on 2007-01-31
Why don't you edit /etc/apt/sources.list

[code[gksudo gedit /etc/apt/sources.list[/code]
and place a # in front of that repo to comment it out for now.  Then, run that command to upgrade your machine again.

Usually, you want to comment out those 3rd party repos when you upgrade your machine; otherwise, that is one sure why to break it.

---

### Post by sandbagger on 2007-02-01
Thanks!
I'll get the hang of this ubuntu stuff eventually :)

---

### Post by sandbagger on 2007-02-01
More problems...
The upgrade process just finished but when the pc rebooted I got the following message:
"Failed to start the X-server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?"
As you might have noticed from my earlier post I have beryl installed, which I'm guessing is the problem.

---

### Post by sandbagger on 2007-02-01
I'm ok now.
I got it working with
dpkg-reconfigure xserver-xorg
startx

---

