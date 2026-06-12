---
title: "Get a list of packages installed by the user"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by chrisstankevitz on 2012-07-20
Hello,

Q1: How can I get a list of packages installed by the user?

A1: history | grep apt-get\ install

Q2: My history does not go back that far.  Plus that method does not work for packages installed by the user using synaptic package manager.

A2: ???

Note: I am not interested in packages that were not installed by the user such as xorg, firefox, xterm, etc.

Thank you!

Chris__

---

### Post by oldfred on 2012-07-21
You can get a list of installed packages with dpkg, but it is everything and very long. Good for reinstalling as on reinstall it will not reinstall anything already installed.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

List with explanations of programs, not for reinstall
dpkg -l > ~/installed_programs.txt

You can install aptitude and get top level only, but still all top level.
Top level only - no depends
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

I am not sure if this is just the one's you have installed or not, for me it still is a long list:
A tabular list of all manually installed packages can be obtained using:
aptitude search '~i!~M'

---

