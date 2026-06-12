---
title: "AppStream cache update completed, but some metadata was ignored due to errors."
date: 2018-07-13
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2018-07-13
There are other post on this issue before dated in 2016. However this issue is resurfacing on my system: 
Ubuntu 16.04.
```
$ uname -r
4.10.0-42-generic


$ dpkg -l | grep appstream
ii  appstream                         0.9.4-1ubuntu3               amd64        Software component index
ii  libappstream-glib8:amd64      0.5.13-1ubuntu5            amd64        GNOME library to access AppStream services
ii  libappstream3:amd64             0.9.4-1ubuntu3              amd64        Library to access AppStream services

```


Error:
```
$ sudo apt-get update
...........            
Get:32 http://ppa.launchpad.net/tista/adapta/ubuntu xenial InRelease [17.5 kB]                                                                                          
Fetched 3,106 kB in 7s (440 kB/s)                                                                                                                                       
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing lxshortcut (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```


Previous posting includes: 
[https://askubuntu.com/q/854168/541417](https://askubuntu.com/q/854168/541417)   --->  Answer: [https://askubuntu.com/a/859116/541417](https://askubuntu.com/a/859116/541417) 

I have enabled xenial-backports repository but still get the same error:

```
$ sudo apt install appstream/xenial-backports
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing lxshortcut (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```


How do I fix this issue?

---

