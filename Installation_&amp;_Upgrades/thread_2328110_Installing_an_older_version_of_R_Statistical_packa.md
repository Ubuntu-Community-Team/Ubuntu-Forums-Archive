---
title: "Installing an older version of R Statistical package."
date: 2016-06-17
forum: Installation &amp; Upgrades
---

### Post by Jonathan_Nowacki on 2016-06-17
I'm currently running R version 3.0.2 and would like to install R version 3.0.1.   

Investigating slightly different results with some hardcore number crunching.   I tried this:

[COLOR=#222222][FONT=arial]
[LIST]
[*] sudo apt-get install r-base=3.0.1-1precise0 
[/LIST]
[/FONT][/COLOR]

But get this:
[INDENT]jnowacki@Ubuntu-Z800F:~$ **sudo apt-get remove r-base**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'r-base' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  account-plugin-windows-live libupstart1 linux-headers-3.13.0-32
  linux-headers-3.13.0-32-generic linux-image-3.13.0-32-generic
  linux-image-extra-3.13.0-32-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
jnowacki@Ubuntu-Z800F:~$ **sudo apt-get clearn; sudo apt-get autoclean**
E: Invalid operation clearn
Reading package lists... Done
Building dependency tree
Reading state information... Done
jnowacki@Ubuntu-Z800F:~$ **sudo apt-get install r-base=3.0.1-1precise0**
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Version '3.0.1-1precise0' for 'r-base' was not found

[/INDENT]

Which I find odd as it clearly exists:

[URL="https://cloud.r-project.org/bin/linux/ubuntu/precise/r-base_3.0.1-1precise0_all.deb"]https://cloud.r-project.org/bin/linux/ubuntu/precise/r-base_3.0.1-1precise0_all.deb


[/URL]Protocol I'm following is here:

[http://askubuntu.com/questions/435232/install-older-version-of-software-and-dependencies](http://askubuntu.com/questions/435232/install-older-version-of-software-and-dependencies)

---

