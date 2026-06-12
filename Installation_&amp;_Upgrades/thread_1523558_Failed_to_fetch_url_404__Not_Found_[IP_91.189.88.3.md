---
title: "Failed to fetch url: 404  Not Found [IP: 91.189.88.30 80]"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by grigory.soid on 2010-07-03
Trying to install gvim:
```
soid@ubuntu:~$ sudo aptitude install vim-gnome
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  gvfs{a} gvfs-backends{a} indicator-application{a} libappindicator0{a} libbonoboui2-0{a} libdbusmenu-gtk1{a} libgail18{a} libglade2-0{a} libgnome2-0{a}
  libgnomecanvas2-0{a} libgnomeui-0{a} libgtk2.0-0{a} libgtk2.0-bin{a} libgtk2.0-common{a} libindicator0{a} libsoup-gnome2.4-1{a} libsoup2.4-1{a}
  policykit-1-gnome{a} vim-gnome
0 packages upgraded, 19 newly installed, 0 to remove and 17 not upgraded.
Need to get 4,083kB/6,907kB of archives. After unpacking 41.5MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libgtk2.0-common 2.20.1-0ubuntu1
  404  Not Found [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libgtk2.0-0 2.20.1-0ubuntu1
  404  Not Found [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libsoup2.4-1 2.30.1-0ubuntu1
  404  Not Found [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libsoup-gnome2.4-1 2.30.1-0ubuntu1
  404  Not Found [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libgail18 2.20.1-0ubuntu1
  404  Not Found [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libgtk2.0-bin 2.20.1-0ubuntu1
  404  Not Found [IP: 91.189.88.30 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.20.1-0ubuntu1_all.deb: 404  Not Found [IP: 91.189.88.30 80]
```

I've checked ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.20.1-0ubuntu1_all.deb on other mirrors but it doesn't exist anywhere.
How could I pass over that?

---

