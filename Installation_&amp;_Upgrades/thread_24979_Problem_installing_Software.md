---
title: "Problem installing Software"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by Sleepy_Sentry on 2005-04-08
I'm trying to install ndiswrapper but I'm having problems.

When I type in sudo dpkg -i filename.deb in Konsole I get a message saying it can't find the file or directory. The same thing happens when I do tar -xvpf filename.tar.gz for .tar.gz files. 

Thanks!

---

### Post by nemin on 2005-04-09
[QUOTE=Sleepy_Sentry]
When I type in sudo dpkg -i filename.deb in Konsole I get a message saying it can't find the file or directory. The same thing happens when I do tar -xvpf filename.tar.gz for .tar.gz files. [/QUOTE]
Are you sure you're in the right directory? You can list the files of the current directory with `ls`. When you see the .deb file then, it should work :) Otherwise `cd` to the right directory.

---

