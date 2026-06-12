---
title: "updating problem dapper to latest version"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by TimTimTimma on 2007-08-25
Hello,

I recently decided to check out ubuntu and installed 5.10 using the cd's and then managed to upgrade to 6.06 successfully

now i am trying to update my system completely using the update manager but when it updates it skips two updates


**Cannot install all available updates**

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

The following updates will be skipped:
gnome-cups-manager
python-netcdf


I did what it said with synaptic and nothing was marked. Then i tried with the terminal and it says

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Anyway to fix this?

Also, I try to install automatix2 and get this error aswell

timtimtimma@ubuntu:~$ sudo dpkg -i automatix2_1.1-4.2-6.06dapper_i386.deb
Selecting previously deselected package automatix2.
(Reading database ... 62687 files and directories currently installed.)
Unpacking automatix2 (from automatix2_1.1-4.2-6.06dapper_i386.deb) ...
dpkg: dependency problems prevent configuration of automatix2:
 automatix2 depends on tango-icon-theme-common; however:
  Package tango-icon-theme-common is not installed.
 automatix2 depends on tango-icon-theme; however:
  Package tango-icon-theme is not installed.
 automatix2 depends on python-vte; however:
  Package python-vte is not installed.
dpkg: error processing automatix2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 automatix2


Any ideas on how to fix this??

---

### Post by TimTimTimma on 2007-08-25
Disregard the last post, I have successfully upgraded the python and gnome files and are now upgrade to ubuntu 6.10

---

