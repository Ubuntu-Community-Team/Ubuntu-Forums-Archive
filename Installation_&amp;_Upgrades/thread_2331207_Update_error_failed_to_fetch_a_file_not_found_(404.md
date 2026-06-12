---
title: "Update error: failed to fetch a file not found (404)"
date: 2016-07-19
forum: Installation &amp; Upgrades
---

### Post by shabbarraza on 2016-07-19
I am getting the following error while trying to update my Ubuntu 16.04 LTS.

I have tried to get reuse the old backup status files but that does not seem to work.

Any help will be much appreciated. Thanks a lot in advance!

```
sudo apt-get update
[sudo] password for shabbar: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://de.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:3 http://de.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:4 http://de.archive.ubuntu.com/ubuntu xenial-backports InRelease
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [94,5 kB]
Hit:6 http://dl.google.com/linux/chrome/deb stable Release          
Ign:7 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial InRelease 
Ign:8 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial Release   
Ign:9 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main amd64 Packages
Ign:10 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main i386 Packages
Ign:11 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main all Packages
Ign:12 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main Translation-en_US
Ign:13 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main Translation-en 
Ign:14 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main DEP-11 64x64 Icons
Ign:9 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main amd64 Packages
Ign:10 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main i386 Packages  
Ign:11 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main all Packages   
Ign:12 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main Translation-en_US
Ign:13 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main DEP-11 64x64 Icons
Ign:9 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main amd64 Packages  
Ign:10 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main i386 Packages  
Ign:11 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main all Packages   
Ign:12 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main Translation-en_US
Ign:13 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main DEP-11 64x64 Icons
Hit:16 http://packages.ros.org/ros/ubuntu xenial InRelease
Ign:9 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main amd64 Packages
Ign:10 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main i386 Packages
Ign:11 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main all Packages
Ign:12 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main Translation-en_US
Ign:13 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main DEP-11 64x64 Icons
Ign:9 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main amd64 Packages
Ign:10 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main i386 Packages
Ign:11 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main all Packages
Ign:12 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main Translation-en_US
Ign:13 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main DEP-11 64x64 Icons
Err:9 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main amd64 Packages
  404  Not Found
Ign:10 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main i386 Packages
Ign:11 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main all Packages
Ign:12 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main Translation-en_US
Ign:13 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial/main DEP-11 64x64 Icons
Fetched 94,5 kB in 1s (80,6 kB/s)
Reading package lists... Done
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
W: The repository 'http://ppa.launchpad.net/kilian/f.lux/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list.d/ros-latest.list:1
```

---

### Post by Bashing-om on 2016-07-19
shabbarraza; Hello;

In essence; the system is telling you that:
1)
There are duplicates in the source list files.
Find and remove them from:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
paying attention to line 55 in /etc/apt/sources.list that is probably duplicated within the directory /etc/apt/sources.list.d/ .

2)
If ya look:
[http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/](http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/)
you see that there is no support here for 16.04 .. remove this PPA/

[INDENT][INDENT]the package manager
[INDENT][INDENT][INDENT]a wonder to behold
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

