---
title: "Upgrade and config files"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by michal-urban on 2014-04-19
Hi,

Ive been using my Ubuntu 12.04 amd64 installation for about a year. I have three partition - root, home and swap. Im using many programs and also many PPAs. Now, I generally prefer new installation to upgrade. Now, Im curious how safe would it be to just keep all the config files in /home and install a new (14.04) version of Ubuntu. Im afraid of uncompatible config files causing error and making difficult to find their roots. 

What say you, would it be safe?

---

### Post by oldfred on 2014-04-20
If you have a separate /home, you can do a new install and reuse existing /home in the install. You have to use Something else and specify current /home as a mount but DO NOT reformat it.
You should export a list of installed applications and probably your list of ppa.
Often the issue with upgrades is the ppas as they may not have trusty version yet and will then cause major upgrade issues as it cannot find all the sources.

I always install to another / (root) partition so I can go back to working install. The once new install is fully configured and I have copied everything I want from old install, I then have a new working install.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

    
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

      
 From old install
dpkg --get-selections > ~/my-packages

---

