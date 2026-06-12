---
title: "error during installation and update"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by oren tal on 2012-05-18
every time I installed or upgrade program I get the following error:
```
installArchives() failed: (Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 319450 files and directories currently installed.)
Preparing to replace blender 2.63+svn46701-0~precise1 (using .../blender_2.63+svn46744-0~precise1_amd64.deb) ...
Unpacking replacement blender ...
Preparing to replace update-manager 1:0.156.14.1 (using .../update-manager_1%%3a0.156.14.4_all.deb) ...
Unpacking replacement update-manager ...
Preparing to replace update-manager-core 1:0.156.14.1 (using .../update-manager-core_1%%3a0.156.14.4_amd64.deb) ...
Unpacking replacement update-manager-core ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Setting up lirc (0.9.0-0ubuntu1) ...
reload: Unknown instance: 
invoke-rc.d: initscript udev, action "reload" failed.
dpkg: error processing lirc (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up blender (2.63+svn46744-0~precise1) ...
No apport report written because MaxReports is reached already
Setting up update-manager-core (1:0.156.14.4) ...
Setting up update-manager (1:0.156.14.4) ...
Errors were encountered while processing:
 lirc
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

Error in function: 
Setting up lirc (0.9.0-0ubuntu1) ...
reload: Unknown instance: 
invoke-rc.d: initscript udev, action "reload" failed.
dpkg: error processing lirc (--configure):
 subprocess installed post-installation script returned error exit status 1
```


how can I solve this ?

---

### Post by plucky on 2012-05-18
> Setting up lirc (0.9.0-0ubuntu1) ...
reload: Unknown instance: 
invoke-rc.d: initscript udev, action "reload" failed.
dpkg: error processing lirc (--configure):
 subprocess installed post-installation script returned error exit status 1

Open a terminal and post output for ```
sudo apt-get install -f
```

If that doesn't work,run ```
sudo apt-get clean
``` and then run the first command again.It should then download a new version ofd **lirc** and try to install it.

Good luck

---

