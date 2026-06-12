---
title: "apt-get update long delay then errors check your internet connection, etc."
date: 2018-08-29
forum: Installation &amp; Upgrades
---

### Post by bulgin on 2018-08-29
Ubuntu 16.04 
Linux version 4.4.0-134-generic (buildd@lgw01-amd64-033) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.10) ) #160-Ubuntu SMP Wed Aug 15 14:58:00 UTC 2018

Issue with sudo apt-get update throwing the following errors:
```
E problem executing scripts APT::Update post-Invoke-Success 'if  /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then  appstreamcli refresh-cache > /dev/null; fi', E:Sub-process returned  an error code
Failed to download repository information
Check your Internet connection.

```There is no problem with the internet connection. 

I've checked other posts that suggest:

```
sudo apt install --reinstall libappstream3
``` 

but that doesn't help.

---

### Post by Bashing-om on 2018-08-29
bulgin; Hello

Try:
[https://ubuntuforums.org/showthread.php?t=2348398](https://ubuntuforums.org/showthread.php?t=2348398)
where you can install the fixed version: appstream/xenial-backports .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by bulgin on 2018-08-29
Thanks for that I'm still getting the same error message.  I've also attached a screen shot of what I see when using synaptic.  Maybe that can provide some clues.

---

### Post by bulgin on 2018-08-29
Screenshot above.

---

### Post by Bashing-om on 2018-08-30
bulgin; Hey -

Screen shots are difficult to work with.
Post back the results of:
```

sudo apt update
sudo apt upgrade

```
so we get the errors in context.
Maybe all we have here is PPA issues ?

[INDENT][INDENT]all in that process
[/INDENT][/INDENT]

---

### Post by bulgin on 2018-08-30
Here you go, hope this helps.  Now what I'm seeing are loooooooong delays before anything happens and my Internet connection is superb:

sudo apt update
[sudo] password for xs: 

after about 30 seconds or more of waiting, then:


Hit:1 [https://dl.ring.cx/ring-nightly/ubuntu_16.04](https://dl.ring.cx/ring-nightly/ubuntu_16.04) ring InRelease
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                                                                                                                                        
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                                                      
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                                                                   
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                                        
Hit:6 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) xenial InRelease                          
Ign:8 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable InRelease                                                                 
Hit:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease                                                          
Hit:10 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable Release                                           
Hit:11 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) xenial InRelease                             
Hit:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease      
Hit:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease                                    
Hit:15 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) xenial InRelease                                   
Hit:16 [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) xenial InRelease
Hit:17 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial InRelease          
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
6 packages can be upgraded. Run 'apt list --upgradable' to see them.
 
sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libx11-6 libx11-data libx11-xcb1 phpmyadmin python-urllib3 python3-urllib3
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 116 kB/4,754 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 




sudo apt upgrade

after about 30 seconds or more:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libx11-6 libx11-data libx11-xcb1 phpmyadmin python-urllib3 python3-urllib3
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 116 kB/4,754 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 python-urllib3 all 1.13.1-2ubuntu0.16.04.2 [57.9 kB]                                                                             
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 python3-urllib3 all 1.13.1-2ubuntu0.16.04.2 [58.1 kB]
Fetched 116 kB in 20s (5,537 B/s)       
Preconfiguring packages ...
(Reading database ... 280322 files and directories currently installed.)
Preparing to unpack .../libx11-data_2%3a1.6.3-1ubuntu2.1_all.deb ...
Unpacking libx11-data (2:1.6.3-1ubuntu2.1) over (2:1.6.3-1ubuntu2) ...
Preparing to unpack .../libx11-6_2%3a1.6.3-1ubuntu2.1_amd64.deb ...
Unpacking libx11-6:amd64 (2:1.6.3-1ubuntu2.1) over (2:1.6.3-1ubuntu2) ...
Preparing to unpack .../libx11-xcb1_2%3a1.6.3-1ubuntu2.1_amd64.deb ...
Unpacking libx11-xcb1:amd64 (2:1.6.3-1ubuntu2.1) over (2:1.6.3-1ubuntu2) ...
Preparing to unpack .../python-urllib3_1.13.1-2ubuntu0.16.04.2_all.deb ...
Unpacking python-urllib3 (1.13.1-2ubuntu0.16.04.2) over (1.13.1-2ubuntu0.16.04.1) ...
Preparing to unpack .../python3-urllib3_1.13.1-2ubuntu0.16.04.2_all.deb ...
Unpacking python3-urllib3 (1.13.1-2ubuntu0.16.04.2) over (1.13.1-2ubuntu0.16.04.1) ...
Preparing to unpack .../phpmyadmin_4%3a4.5.4.1-2ubuntu2.1_all.deb ...
Unpacking phpmyadmin (4:4.5.4.1-2ubuntu2.1) over (4:4.5.4.1-2ubuntu2) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1.1) ...
Processing triggers for doc-base (0.10.7) ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Setting up libx11-data (2:1.6.3-1ubuntu2.1) ...
Setting up libx11-6:amd64 (2:1.6.3-1ubuntu2.1) ...
Setting up libx11-xcb1:amd64 (2:1.6.3-1ubuntu2.1) ...
Setting up python-urllib3 (1.13.1-2ubuntu0.16.04.2) ...
Setting up python3-urllib3 (1.13.1-2ubuntu0.16.04.2) ...
Setting up phpmyadmin (4:4.5.4.1-2ubuntu2.1) ...
apache2_invoke phpmyadmin: already enabled
apache2.service is not active, cannot reload.
invoke-rc.d: initscript apache2, action "reload" failed.
Processing triggers for libc-bin (2.23-0ubuntu10) .

---

### Post by Bashing-om on 2018-08-30
bulgin; Well ..

so far so good .. I see nothing wrong in the outputs you provided.
30 seconds or so is not long for the system to parse what has to be done - if anything.

leastways -
[INDENT][INDENT]that is my thoughts on the matter
[/INDENT][/INDENT]

---

