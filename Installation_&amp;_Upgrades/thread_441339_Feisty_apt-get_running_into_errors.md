---
title: "Feisty: apt-get running into errors"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by orrorin on 2007-05-12
Hi,

I'm a newbie to Ubuntu and I recently installed Feisty (7.04) on my x86.
Whenever I do apt-get, I get the following errors. It looks like gnome-panel, gnome-panel-data and gnome-applets were not installed properly. 

It complains about missing file /usr/share/gconf/defaults/10_libgksu, which is a link to /etc/alternatives/libgksu-gconf-defaults, which in turn is a link to /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo.

However, the entire "debian" dir under /usr/share/libgksu seems to be missing.

What do I need to install to get this entire directory correctly installed?

Thanks.




$ sudo apt-get install gnome-panel
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-panel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/322kB of archives.
After unpacking 0B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 87997 files and directories currently installed.)
Preparing to replace gnome-applets 2.18.0-0ubuntu1 (using .../gnome-applets_2.18.0-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-applets ...
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error processing /var/cache/apt/archives/gnome-applets_2.18.0-0ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-applets_2.18.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by raphoun on 2007-11-25
I have the same trouble, how to fix it??? Please

---

