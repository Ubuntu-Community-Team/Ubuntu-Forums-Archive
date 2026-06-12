---
title: "The package system is broken; unmet dependencies; mongodb"
date: 2019-11-09
forum: Installation &amp; Upgrades
---

### Post by gilhini on 2019-11-09
Dear all,

I am a rather new linux user and I am completely and utterly stuck. I've set up a brand new ubuntu 19.10 for mainly use as a plex server. All wen well and is generally still running great. Then I decided to install unifi video with the help of a script I found on the [unifi support forum]("https://community.ui.com/questions/UniFi-Video-Installation-Scripts-or-UniFi-Lets-Encrypt-or-Ubuntu-16-04-18-04-18-10-19-04-and-19-10-/c272abf8-7680-4b73-9d10-c876ab86f4c9"). I followed it to the letter and got some nasty errors (I remember red boxes and such) - but as it seemed that the program was successfully installed (i could reach the port and set it up properly) I did not really copy the errors. Wanting to keep my system up2date i started the softwareupdater and got the following Message:

```
The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:


mongodb-org: Depends: mongodb-org-server but it is not installed
             Depends: mongodb-org-mongos but it is not installed
             Depends: mongodb-org-tools but it is not installed
unifi-video: Depends: mongodb-server (>= 2.4.9) but it is not installed

```

I then started a google search to get rid of the problem and tried all suggestions of different forums but they all returned more or less this (here is an example of "apt-get install -f")

```
root@skynet:~# apt-get install -fReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libboost-filesystem1.67.0 libboost-iostreams1.67.0
  libboost-program-options1.67.0 libgoogle-perftools4 libpcrecpp0v5
  libtcmalloc-minimal4 libyaml-cpp0.6 mongo-tools mongodb-server-core
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
  mongodb-org-mongos mongodb-org-server mongodb-org-tools
The following NEW packages will be installed:
  mongodb-org-mongos mongodb-org-server mongodb-org-tools
0 upgraded, 3 newly installed, 0 to remove and 15 not upgraded.
2 not fully installed or removed.
Need to get 0 B/79,4 MB of archives.
After this operation, 266 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 168960 files and directories currently installed.)
Preparing to unpack .../mongodb-org-server_3.4.23_amd64.deb ...
Unpacking mongodb-org-server (3.4.23) ...
dpkg: error processing archive /var/cache/apt/archives/mongodb-org-server_3.4.23_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/mongod', which is also in package mongodb-server-core 1:3.6.9+really3.6.8+90~g8e540c0b6d-0ubuntu2
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Preparing to unpack .../mongodb-org-mongos_3.4.23_amd64.deb ...
Unpacking mongodb-org-mongos (3.4.23) ...
dpkg: error processing archive /var/cache/apt/archives/mongodb-org-mongos_3.4.23_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/mongos', which is also in package mongodb-server-core 1:3.6.9+really3.6.8+90~g8e540c0b6d-0ubuntu2
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Preparing to unpack .../mongodb-org-tools_3.4.23_amd64.deb ...
Unpacking mongodb-org-tools (3.4.23) ...
dpkg: error processing archive /var/cache/apt/archives/mongodb-org-tools_3.4.23_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/bsondump', which is also in package mongo-tools 3.6.3-0ubuntu1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mongodb-org-server_3.4.23_amd64.deb
 /var/cache/apt/archives/mongodb-org-mongos_3.4.23_amd64.deb
 /var/cache/apt/archives/mongodb-org-tools_3.4.23_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

I even tried to just plain rm the /usr/bin/mongod file for example but that did not change anything.

I really do not know what to try anymore - I mean the easy way out would be to just scrap the installation and start from beginning, but where's the fun in that ;). I'd rather know what the problem is and learn how to fix it!

Thank you for your help
Gil

---

### Post by rsteinmetz70112 on 2019-11-09
try:
```
sudo dpkg --configure -a
sudo apt install -f
```
and report the results.

---

### Post by TheFu on 2019-11-09
Really new Linux users should run LTS releases like 18.04.  19.10 is not an LTS.

---

### Post by gilhini on 2019-11-09
> **rsteinmetz70112 said:**
> try:
```
sudo dpkg --configure -a
sudo apt install -f
```
and report the results.

Thank you for helping me!


```
mark@skynet:~$ sudo dpkg --configure -a[sudo] password for mark: 
dpkg: dependency problems prevent configuration of unifi-video:
 unifi-video depends on mongodb-10gen (>= 2.4.10) | mongodb-org-server (>= 2.6.0) | mongodb-server (>= 2.4.9); however:
  Package mongodb-10gen is not installed.
  Package mongodb-org-server is not installed.
  Package mongodb-server is not installed.


dpkg: error processing package unifi-video (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mongodb-org:
 mongodb-org depends on mongodb-org-server; however:
  Package mongodb-org-server is not installed.
 mongodb-org depends on mongodb-org-mongos; however:
  Package mongodb-org-mongos is not installed.
 mongodb-org depends on mongodb-org-tools; however:
  Package mongodb-org-tools is not installed.


dpkg: error processing package mongodb-org (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 unifi-video
 mongodb-org
mark@skynet:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libboost-filesystem1.67.0 libboost-iostreams1.67.0 libboost-program-options1.67.0 libgoogle-perftools4 libpcrecpp0v5 libtcmalloc-minimal4
  libyaml-cpp0.6 mongo-tools mongodb-server-core
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  mongodb-org-mongos mongodb-org-server mongodb-org-tools
The following NEW packages will be installed:
  mongodb-org-mongos mongodb-org-server mongodb-org-tools
0 upgraded, 3 newly installed, 0 to remove and 15 not upgraded.
2 not fully installed or removed.
Need to get 0 B/79,4 MB of archives.
After this operation, 266 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 168960 files and directories currently installed.)
Preparing to unpack .../mongodb-org-server_3.4.23_amd64.deb ...
Unpacking mongodb-org-server (3.4.23) ...
dpkg: error processing archive /var/cache/apt/archives/mongodb-org-server_3.4.23_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/mongod', which is also in package mongodb-server-core 1:3.6.9+really3.6.8+90~g8e540c0b6d-0ubuntu2
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Preparing to unpack .../mongodb-org-mongos_3.4.23_amd64.deb ...
Unpacking mongodb-org-mongos (3.4.23) ...
dpkg: error processing archive /var/cache/apt/archives/mongodb-org-mongos_3.4.23_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/mongos', which is also in package mongodb-server-core 1:3.6.9+really3.6.8+90~g8e540c0b6d-0ubuntu2
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Preparing to unpack .../mongodb-org-tools_3.4.23_amd64.deb ...
Unpacking mongodb-org-tools (3.4.23) ...
dpkg: error processing archive /var/cache/apt/archives/mongodb-org-tools_3.4.23_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/bsondump', which is also in package mongo-tools 3.6.3-0ubuntu1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mongodb-org-server_3.4.23_amd64.deb
 /var/cache/apt/archives/mongodb-org-mongos_3.4.23_amd64.deb
 /var/cache/apt/archives/mongodb-org-tools_3.4.23_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mark@skynet:~$ 



```

---

### Post by gilhini on 2019-11-09
> **TheFu said:**
> Really new Linux users should run LTS releases like 18.04.  19.10 is not an LTS.

You are right of course, now that you say it...I am just in the habit of thinking in windows terms where the latest update has the most security patches ;-) If I need to wipe and reinstall I will heed your advice!

---

### Post by rsteinmetz70112 on 2019-11-10
I'm not familiar with those packages. Did they come form the Ubuntu repositories?
Next I'd try 
sudo apt update
sudo apt upgrade

Did you try 
```
sudo apt install -f
```
That command will attempt to fix any broken packages. 

Next I'd try 
```
sudo apt update
sudo apt upgrade
```

If that doesn't work you could try to reinstall the missing packages:
```
sudo apt install --reinstall <package name>
```

You may need to first remove the partially installed packages.
But before you try that report back.

---

### Post by gilhini on 2019-11-11
ok so I tried all you suggestions.

> [COLOR=#000000]I'm not familiar with those packages. Did they come form the Ubuntu repositories?[/COLOR]
Nope i installed it with a script from the unifi site directly


_**here is "sudo apt update" and "sudo apt upgrade"**_
```

mark@skynet:~$ sudo apt update
Hit:1 http://at.archive.ubuntu.com/ubuntu eoan InRelease
Hit:2 http://linux.teamviewer.com/deb stable InRelease                                                                             
Get:3 http://at.archive.ubuntu.com/ubuntu eoan-updates InRelease [97,5 kB]                                                         
Ign:4 http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 InRelease                                          
Hit:5 http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 Release                                            
Ign:6 http://dl.google.com/linux/chrome/deb stable InRelease                                                  
Get:7 http://at.archive.ubuntu.com/ubuntu eoan-backports InRelease [88,8 kB]                                  
Get:8 http://security.ubuntu.com/ubuntu eoan-security InRelease [97,5 kB]      
Hit:9 http://dl.google.com/linux/chrome/deb stable Release
Get:11 http://at.archive.ubuntu.com/ubuntu eoan-updates/main amd64 DEP-11 Metadata [204 B]
Get:12 http://at.archive.ubuntu.com/ubuntu eoan-updates/universe amd64 DEP-11 Metadata [208 B]
Get:13 http://at.archive.ubuntu.com/ubuntu eoan-backports/universe amd64 DEP-11 Metadata [7.756 B]
Get:15 http://security.ubuntu.com/ubuntu eoan-security/main amd64 DEP-11 Metadata [204 B]
Get:16 http://security.ubuntu.com/ubuntu eoan-security/universe amd64 DEP-11 Metadata [208 B]
Fetched 292 kB in 1s (404 kB/s)                         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
15 packages can be upgraded. Run 'apt list --upgradable' to see them.
mark@skynet:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 mongodb-org : Depends: mongodb-org-server but it is not installed
               Depends: mongodb-org-mongos but it is not installed
               Depends: mongodb-org-tools but it is not installed
 unifi-video : Depends: mongodb-10gen (>= 2.4.10) but it is not installable or
                        mongodb-org-server (>= 2.6.0) but it is not installed or
                        mongodb-server (>= 2.4.9) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```


[U][B]"sudo apt --install reinstall" does look like this with alternating unmet dependencies depending on the package:
[/B][/U]
```
mark@skynet:~$ sudo apt install --reinstall mongodb-org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 mongodb-org : Depends: mongodb-org-server but it is not going to be installed
               Depends: mongodb-org-mongos but it is not going to be installed
               Depends: mongodb-org-tools but it is not going to be installed
 unifi-video : Depends: mongodb-10gen (>= 2.4.10) but it is not installable or
                        mongodb-org-server (>= 2.6.0) but it is not going to be installed or
                        mongodb-server (>= 2.4.9) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
mark@skynet:~$ apt --fix-broken install unifi-video
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?
mark@skynet:~$ sudo apt --fix-broken install unifi-video
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unifi-video is already the newest version (3.10.10).
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 mongodb-org : Depends: mongodb-org-server but it is not going to be installed
               Depends: mongodb-org-mongos but it is not going to be installed
               Depends: mongodb-org-tools but it is not going to be installed
 unifi-video : Depends: mongodb-10gen (>= 2.4.10) but it is not installable or
                        mongodb-org-server (>= 2.6.0) but it is not going to be installed or
                        mongodb-server (>= 2.4.9) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```


_**The only exception being if I do "sudo apt install --reinstall mongodb-server" i get something new from mongodb-org-shell:**_

```
mark@skynet:~$ sudo apt install --reinstall mongodb-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 mongodb-org : Depends: mongodb-org-server but it is not going to be installed
               Depends: mongodb-org-mongos but it is not going to be installed
               Depends: mongodb-org-tools but it is not going to be installed
               Conflicts: mongodb-server but 1:3.6.9+really3.6.8+90~g8e540c0b6d-0ubuntu2 is to be installed
[COLOR=#ff0000] mongodb-org-shell : Conflicts: mongodb-server but 1:3.6.9+really3.6.8+90~g8e540c0b6d-0ubuntu2 is to be installed[/COLOR]
 mongodb-server : Depends: mongodb-clients but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```

_**I have also tried removing and purging the packages but get the following message:**_

```
mark@skynet:~$ sudo apt purge unifi-video 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 mongodb-org : Depends: mongodb-org-server but it is not going to be installed
               Depends: mongodb-org-mongos but it is not going to be installed
               Depends: mongodb-org-tools but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```

Thx again for sticking with me!

---

### Post by Impavidus on 2019-11-11
Be careful when running random scripts from websites, in particular when you want to run them as the root user. When you try it often enough, one will break your system, as this script has obviously done. I've skimmed through the script (one of the versions at least) and found some things that I wouldn't want to happen on my computer.

The script, amongst other things, adds some repositories and installs some packages. Unfortunately, the packages mongodb-org-server, mongodb-org-mongos and mongodb-org-tools (which are not in the official repos, so I assume they come from the sources added by your script) are in conflict with the packages mongodb-server-core and mongo-tools (which are from the official repos). You have to remove one of those sets. Normally, I would remove the packages not from the official repos. But if you know what you're doing, you can choose otherwise.

---

### Post by rsteinmetz70112 on 2019-11-11
YOu might want to try:

```
sudo apt --fix-broken install
```

This is the equivlent as 

```
sudo apt install -f
```

I posted earlier.

---

### Post by gilhini on 2019-11-11
> **Impavidus said:**
> [...]You have to remove one of those sets. Normally, I would remove the packages not from the official repos. But if you know what you're doing, you can choose otherwise.

Thank you for taking the time of scimming the script. I do know now that I shouldn't have done that and will not use a script in the future if I do not understand what it does... Could you maybe elaborate on how I can remove the packages not from the official repos - or maybe point me to a source where I can learn about how to do it (I did try removing the whole unif-video with sudo apt purge unifi-video but got the now familiar response with the dependencies)


> **rsteinmetz70112 said:**
> YOu might want to try:

```
sudo apt --fix-broken install
```

This is the equivlent as 

```
sudo apt install -f
```

I posted earlier.

I did try that already but got the same as all the other things. 

```
mark@skynet:~$ sudo apt --fix-broken install[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libboost-filesystem1.67.0 libboost-iostreams1.67.0 libboost-program-options1.67.0 libgoogle-perftools4 libpcrecpp0v5 libtcmalloc-minimal4
  libyaml-cpp0.6 mongo-tools mongodb-server-core
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  mongodb-org-mongos mongodb-org-server mongodb-org-tools
The following NEW packages will be installed:
  mongodb-org-mongos mongodb-org-server mongodb-org-tools
0 upgraded, 3 newly installed, 0 to remove and 15 not upgraded.
2 not fully installed or removed.
Need to get 0 B/79,4 MB of archives.
After this operation, 266 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 168960 files and directories currently installed.)
Preparing to unpack .../mongodb-org-server_3.4.23_amd64.deb ...
Unpacking mongodb-org-server (3.4.23) ...
dpkg: error processing archive /var/cache/apt/archives/mongodb-org-server_3.4.23_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/mongod', which is also in package mongodb-server-core 1:3.6.9+really3.6.8+90~g8e540c0b6d-0ubuntu2
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Preparing to unpack .../mongodb-org-mongos_3.4.23_amd64.deb ...
Unpacking mongodb-org-mongos (3.4.23) ...
dpkg: error processing archive /var/cache/apt/archives/mongodb-org-mongos_3.4.23_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/mongos', which is also in package mongodb-server-core 1:3.6.9+really3.6.8+90~g8e540c0b6d-0ubuntu2
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Preparing to unpack .../mongodb-org-tools_3.4.23_amd64.deb ...
Unpacking mongodb-org-tools (3.4.23) ...
dpkg: error processing archive /var/cache/apt/archives/mongodb-org-tools_3.4.23_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/bsondump', which is also in package mongo-tools 3.6.3-0ubuntu1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mongodb-org-server_3.4.23_amd64.deb
 /var/cache/apt/archives/mongodb-org-mongos_3.4.23_amd64.deb
 /var/cache/apt/archives/mongodb-org-tools_3.4.23_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

You did mention in one of your replies that I may first have to "remove the partially installed packages" How do I do that (is this the same suggestion as Impavidus mentioned above?)

Thx again to all of you for your help - I really appreaciate this!

---

### Post by rsteinmetz70112 on 2019-11-11
To remove a package 
```
sudo apt remove <packagename>
```
this will not remove dependencies or configuration data
```
sudo apt purge <package name> 
```
will remove the package and the configuration data but not the dependencies.
adding ```
--simulate
```
will execute the commands without changing anything.

You can then reinstall the packages. You can also list more than one package on the command lines, if you're brave.

As I mentioned earlier I'm not familiar with the packages you're trying to install. I would look a little deeper to find out if this will work especially if someone has already done exactly what you're trying to do (install these packages on this version of Ubuntu).
Since you installed these packages from a non standard repository, the standard Ubuntu packages may not be correct for your application. 
The nonstandard packages may have dependency problems with Ubuntu's standard packages.

---

### Post by gilhini on 2019-11-12
> **rsteinmetz70112 said:**
>  [...]

You can then reinstall the packages. [COLOR=#ff0000]You can also list more than one package on the command lines, if you're brave.[/COLOR]

As I mentioned earlier I'm not familiar with the packages you're trying to install. I would look a little deeper to find out if this will work especially if someone has already done exactly what your are trying to do (install these packages on this version of Ubuntu.
Since you installed these packages from a non standard repository, the standard Ubuntu packages may not be correct for your application. 
The nonstandard packages may have dependency problems with Ubuntu's standard packages.

You telling me that I can be brave did the trick :-)

For reference trying "sudo apt purge unifi-video" and "sudo apt purge mongodb-org" on its own produced the following error

```
mark@skynet:~$ sudo apt purge unifi-video 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 mongodb-org : Depends: mongodb-org-server but it is not going to be installed
               Depends: mongodb-org-mongos but it is not going to be installed
               Depends: mongodb-org-tools but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
mark@skynet:~$ sudo apt remove mongodb-org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 unifi-video : Depends: mongodb-10gen (>= 2.4.10) but it is not installable or
                        mongodb-org-server (>= 2.6.0) but it is not going to be installed or
                        mongodb-server (>= 2.4.9) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

but adding both packages in the same line (ergo being brave ;-) ) did the trick!

```
mark@skynet:~$ [COLOR=#ff0000]sudo apt purge mongodb-org unifi-video 
[/COLOR]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ca-certificates-java java-common jsvc libboost-filesystem1.67.0 libboost-iostreams1.67.0 libboost-program-options1.67.0 libcommons-daemon-java
  libgoogle-perftools4 libpcrecpp0v5 libtcmalloc-minimal4 libyaml-cpp0.6 mongo-tools mongodb-org-shell mongodb-server-core
  openjdk-8-jre-headless
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  mongodb-org* unifi-video*
0 upgraded, 0 newly installed, 2 to remove and 15 not upgraded.
2 not fully installed or removed.
After this operation, 202 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 168959 files and directories currently installed.)
Removing mongodb-org (3.4.23) ...
Removing unifi-video (3.10.10) ...
unifi-video: /var/lib/dpkg/info/unifi-video.postrm remove
(Reading database ... 168769 files and directories currently installed.)
Purging configuration files for unifi-video (3.10.10) ...
unifi-video: /var/lib/dpkg/info/unifi-video.postrm purge
Purging configuration files for mongodb-org (3.4.23) ...
Processing triggers for systemd (242-7ubuntu3) ...



```


Thank you to everyone who took the time to help me - I am now smarter than I was before :cool:

---

### Post by rsteinmetz70112 on 2019-11-12
Looks like you may still have a few problems with some packages:
> [B]15 not upgraded.
2 not fully installed or removed. [/B]

You should also run```
 sudo apt autoremove
``` to clean up unused packages.
Then:
```
sudo apt update
sudo apt full-upgrade
```

---

