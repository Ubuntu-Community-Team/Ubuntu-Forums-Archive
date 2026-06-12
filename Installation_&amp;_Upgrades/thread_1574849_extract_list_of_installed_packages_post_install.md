---
title: "extract list of installed packages post install"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by tim042849 on 2010-09-14
I'm using ubuntu 10.04
Is it possible to get a list of all packages installed
**after** the initial installation?
thanks
tim

---

### Post by tommcd on 2010-09-15
Open a terminal and run this command:
```
dpkg -l > packages.txt
```
This will create a file in your home directory named *packages.txt* that will list each and every package on your system.

EDIT: Do you mean only updates? Or only packages that you have installed yourself? Sorry if I misunderstood you here.

---

### Post by oldfred on 2010-09-15
A tabular list of all manually installed packages can be obtained using:
aptitude search '~i!~M'


If you want a list for reinstalling:
 dpkg --get-selections > ubuntu-files
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)


I also copied this from another post:
Another example of what this process allows you to do is create a baseline of all the applications after a clean installation of Ubuntu.  Let’s say you would like to remove any applications installed since the clean install, perform the exact same process, and any package not defined in that list will be removed.

    sudo dpkg --get-selections > clean-install-package-list.txt
    sudo dpkg --clear-selections
    sudo dpkg --set-selections < clean-install-package-list.txt
    sudo aptitude install

Use sed,cat & uniq to combine two lists into an install & uninstall 
[http://ubuntuforums.org/showthread.php?t=261366&page=71](http://ubuntuforums.org/showthread.php?t=261366&page=71)

---

### Post by tim042849 on 2010-09-15
> **tommcd said:**
> Open a terminal and run this command:
```
dpkg -l > packages.txt
```
This will create a file in your home directory named *packages.txt* that will list each and every package on your system.

EDIT: Do you mean only updates? Or only packages that you have installed yourself? Sorry if I misunderstood you here.
Just the packages that I installed myself. But thanks for the tip;)

---

### Post by tim042849 on 2010-09-15
Thank you folks. That's what I need!:)

---

