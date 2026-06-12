---
title: "Apt-Get is corrupted (fsck is suspected to have caused this)"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by PureW on 2007-11-24
Hello, recently I had to run fsck through the live-cd to correct some errors.

After this some packages just wont install. Look at this when trying to install bjam for example:> $ sudo apt-get install bjam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bjam is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up bittorrent (3.4.2-11ubuntu3~7.10) ...
update-alternatives: unable to open /var/lib/dpkg/alternatives/btcompletedir: Not a directory
dpkg: error processing bittorrent (--configure):
 subprocess post-installation script returned error exit status 2
Setting up bjam (3.1.14-1) ...
update-alternatives: unable to open /var/lib/dpkg/alternatives/jam: Not a directory
dpkg: error processing bjam (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gedit (2.20.3-0ubuntu1) ...
update-alternatives: unable to open /var/lib/dpkg/alternatives/gnome-text-editor: Not a directory
dpkg: error processing gedit (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gnome-session (2.20.1-0ubuntu1) ...
update-alternatives: unable to open /var/lib/dpkg/alternatives/x-session-manager: Not a directory
dpkg: error processing gnome-session (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libwxbase2.6-dev (2.6.3.2.1.5ubuntu12) ...
update-alternatives: unable to open /var/lib/dpkg/alternatives/wx-config: Not a directory
dpkg: error processing libwxbase2.6-dev (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libwxgtk2.6-dev:
 libwxgtk2.6-dev depends on libwxbase2.6-dev (= 2.6.3.2.1.5ubuntu12); however:
  Package libwxbase2.6-dev is not configured yet.
dpkg: error processing libwxgtk2.6-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bittorrent
 bjam
 gedit
 gnome-session
 libwxbase2.6-dev
 libwxgtk2.6-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)


Purging it doesn't help:
> $ sudo apt-get --purge remove bjam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  bjam*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 414kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 111755 files and directories currently installed.)
Removing bjam ...
update-alternatives: unable to open /var/lib/dpkg/alternatives/jam: Not a directory
dpkg: error processing bjam (--purge):
 subprocess pre-removal script returned error exit status 2
update-alternatives: unable to open /var/lib/dpkg/alternatives/jam: Not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 bjam
E: Sub-process /usr/bin/dpkg returned an error code (1)


What do I do?

---

