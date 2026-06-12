---
title: "Problem with apt-get"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by blackbeard on 2007-05-13
I am running Kubuntu 7.04. I tried to install the mplayer and mozilla-mplayer packages through Adept and now i am having loads of trouble installing anything and i cannot uninstall anything. Somehow, directly after i attempted to install those, i managed to install ksirtet.

when i enter "sudo apt-get remove mplayer ksirtet" this is what i get:

sean@sean-desktop:~$ sudo apt-get remove mplayer ksirtet
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cd-discid
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ksirtet mplayer
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 11.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 81330 files and directories currently installed.)
Removing ksirtet ...

(update-desktop-database:9435): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing ksirtet (--remove):
 subprocess post-removal script returned error exit status 139
Removing mplayer ...

(update-desktop-database:9440): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing mplayer (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 ksirtet
 mplayer
E: Sub-process /usr/bin/dpkg returned an error code (1)

any help would be much appreciated

---

### Post by sdowney717 on 2007-05-13
You could try these commands

aptitude update
aptitude clean 
aptitude clean all
aptitude autoclean

---

### Post by blackbeard on 2007-05-13
Unfortunately, when i try to uninstall the broken packages, it is still failing

how can i get rid of them?

---

