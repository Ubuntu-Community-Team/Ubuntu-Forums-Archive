---
title: "Problem uninstalling Sanduhr"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by abrichr on 2007-07-27
I installed the Sanduhr alarm clock available in the repos with no problems.  When I try to uninstall it, however:

```
sudo apt-get remove -mf sanduhr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-bin libgtk1.2 libglib1.2 libgnomeui32 libgnome32 libart2 oaf libxml1
  libdb3 libgnorbagtk0 gnome-libs-data imlib-base libgtk1.2-common liborbit0
  gdk-imlib11 libgnomesupport0 liboaf0 libgnorba27
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  sanduhr
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 1085kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 127140 files and directories currently installed.)
Removing sanduhr ...
/usr/share/omf/sanduhr/sanduhr-C.omf: could not delete file: No such file or directory at /usr/sbin/install-docs line 640.
dpkg: error processing sanduhr (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 sanduhr
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Also, interestingly enough, when I try to remove the unused packages:

```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

any help would be appreciated :)

---

