---
title: "migrating to a new system, different versions"
date: 2018-11-19
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2018-11-19
I see that there are insructions for easily miggrating from System A to B if both are running the same version of Ubuntu.

I however just loaded Ubuntu 18.04 on a new system (with a GREAT deal of help from people on this forum, so Thank You.). My old system is running 16.04.
is there an easy way to move my various applications over the the new machine, short of reloading and reinstalling them one by one?

on a related note, can I just copy the entire contents of my current /home directory to the new system and have it all magically function there? (is there any functionality at all under /home? or is it just dumb file storage?)

Peter

---

### Post by oldfred on 2018-11-19
Your normal backup should include all the things you need to be able to do a new clean install & restore you configuration & data. Tomorrow when hard drive totally fails, you then can easily install & restore to new drive and have working system in a very short time.

Your /home has all your configurations, mostly hidden (. folders).

You can copy /home over. 
It also has things like Firefox or Thunderbird profiles & you then have all that copied over.

You can export list of installed apps and just reinstall those. Often best to review, some may be obsolete, and you do not want old kernels, if new version.
       My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install

---

