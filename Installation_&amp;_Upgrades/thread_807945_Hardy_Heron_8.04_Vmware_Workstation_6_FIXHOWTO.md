---
title: "Hardy Heron 8.04 Vmware Workstation 6 FIX/HOWTO"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by gotlinuxed on 2008-05-26
There are a lot of threads like this one:
[http://ubuntuforums.org/showthread.php?t=775531&highlight=vmware](http://ubuntuforums.org/showthread.php?t=775531&highlight=vmware)
full of people like me whose upgrade to 8.04 broke their VmWare install. I tried everything, modifying source, the latest any-any patch (117), etc. None of it works. 

The key difference I think is architecture; I'm on x64, and I think the changes to 64 bit primitive data types in the newer kernel source totally broke the vmware install. But I have the solution!

1) If you don't have g++ installed, sudo apt-get install g++. I had to do this.
2) Download the latest 6.03 tarball from vmware ( 6.0.3, Build 80004 )
3) Re-run the install script with no special options

That's it! I know it seems too simple to work but it works like a charm. I even got the integrated Eclipse debugging to install. 

Created a new top level thread so the right keywords would be in the title. Hope this post helps folks who are struggling. Enjoy!

:guitar:

---

