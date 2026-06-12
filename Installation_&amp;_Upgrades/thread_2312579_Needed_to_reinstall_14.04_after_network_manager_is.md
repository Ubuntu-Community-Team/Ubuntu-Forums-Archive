---
title: "Needed to reinstall 14.04 after network manager is gone"
date: 2016-02-05
forum: Installation &amp; Upgrades
---

### Post by colonel2 on 2016-02-05
Hi all, I reinstall after my network manager vanished, I searched for solutions but they were no enough.  So now I am trying to get my system back and I need help finding the names of the programs I used to have. I looking in the Software Center but I can find the one for the built in camera I used to have.  What is the best Movie software for regular DVD?  

Thank you for you time. Again, It was painful to do the reinstall but I could no get the applet back from the console whatever solution I got.  Sudo!!

---

### Post by oldfred on 2016-02-05
My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. You may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.

   from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

   and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

---

