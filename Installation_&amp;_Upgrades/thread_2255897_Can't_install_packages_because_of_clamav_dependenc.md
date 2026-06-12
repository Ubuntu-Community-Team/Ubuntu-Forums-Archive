---
title: "Can't install packages because of clamav dependencies?"
date: 2014-12-08
forum: Installation &amp; Upgrades
---

### Post by pokedadude on 2014-12-08
Turns out I can't install anything using aptitude and I also seem to be missing a few dependencies.
  **When I try to install a program:**
```

  mom@mom-Inspiron-1720:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 clamav-daemon : Depends: clamav-base (= 0.98.5+addedllvm-0ubuntu0.14.04.1) but it is not going to be installed
 clamav-freshclam : Depends: clamav-base (>= 0.98.5+addedllvm-0ubuntu0.14.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mom@mom-Inspiron-1720:~$

```
```

 **When I use apt-get -f install:**
  mom@mom-Inspiron-1720:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  clamav-base clamav-daemon
Suggested packages:
  daemon clamav-docs
The following NEW packages will be installed:
  clamav-base
The following packages will be upgraded:
  clamav-daemon
1 upgraded, 1 newly installed, 0 to remove and 106 not upgraded.
5 not fully installed or removed.
Need to get 0 B/244 kB of archives.
After this operation, 369 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
Can't exec "/tmp/clamav-base.config.0YwBEj": Permission denied at /usr/share/perl/5.18/IPC/Open3.pm line 173.
open2: exec of /tmp/clamav-base.config.0YwBEj configure  failed at /usr/share/perl5/Debconf/ConfModule.pm line 59.
(Reading database ... 304306 files and directories currently installed.)
Preparing to unpack .../clamav-daemon_0.98.5+addedllvm-0ubuntu0.14.04.1_i386.deb ...
/etc/init.d/clamav-daemon: 164: export: Default:: bad variable name
invoke-rc.d: initscript clamav-daemon, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg: trying script from the new package instead ...
/etc/init.d/clamav-daemon: 164: export: Default:: bad variable name
invoke-rc.d: initscript clamav-daemon, action "stop" failed.
dpkg: error processing archive /var/cache/apt/archives/clamav-daemon_0.98.5+addedllvm-0ubuntu0.14.04.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
/etc/init.d/clamav-daemon: 164: export: Default:: bad variable name
invoke-rc.d: initscript clamav-daemon, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Preparing to unpack .../clamav-base_0.98.5+addedllvm-0ubuntu0.14.04.1_all.deb ...
Unpacking clamav-base (0.98.5+addedllvm-0ubuntu0.14.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/clamav-base_0.98.5+addedllvm-0ubuntu0.14.04.1_all.deb (--unpack):
 trying to overwrite '/usr/share/man/man5/clamd.conf.5.gz', which is also in package clamav-daemon 0.98.4+dfsg-2~ubuntu14.04.1
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/clamav-daemon_0.98.5+addedllvm-0ubuntu0.14.04.1_i386.deb
 /var/cache/apt/archives/clamav-base_0.98.5+addedllvm-0ubuntu0.14.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mom@mom-Inspiron-1720:~$ 

```
[B]When I tried sudo apt-get purge clamav I got this:

[/B]```
mom@mom-Inspiron-1720:~$ sudo apt-get purge clamav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'clamav' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 clamav-daemon : Depends: clamav-base (= 0.98.5+addedllvm-0ubuntu0.14.04.1) but it is not going to be installed
                 Depends: clamav-freshclam but it is not going to be installed or
                          clamav-data
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mom@mom-Inspiron-1720:~$ 

```
[B]
Any suggestions would be appreciated![/B]

---

### Post by ian-weisser on 2014-12-08
'Purge' does not force removal of a package. It does something else.

Try:
```
sudo apt-get autoremove clamav-base clamav-freshclam clamav-data clamav-daemon clamav-docs
sudo apt-get update
sudo apt-get upgrade
```

If the final command gives you an error, please share it with us.
If the final command does not give you an error, your problem is likely fixed.

If you want to reinstall clamav, delete the clamav packages from your local cache - this will force the package manager to download fresh copies.
```
sudo apt-get clean clamav*
sudo apt-get install clamav
```

---

### Post by pokedadude on 2014-12-08
**This is what I got when I tried to reinstall it:**
```

mom@mom-Inspiron-1720:~$ sudo apt-get clean clamav*
mom@mom-Inspiron-1720:~$ sudo apt-get install clamav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 clamav : Depends: clamav-freshclam but it is not going to be installed or
                   clamav-data
          Recommends: clamav-base but it is not going to be installed
 clamav-daemon : Depends: clamav-base (= 0.98.5+addedllvm-0ubuntu0.14.04.1) but it is not going to be installed
                 Depends: clamav-freshclam but it is not going to be installed or
                          clamav-data
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mom@mom-Inspiron-1720:~$ 

[B]
And this is what happened when I tried to delete it:
[/B]
mom@mom-Inspiron-1720:~$ sudo apt-get autoremove clamav-base clamav-freshclam clamav-data clamav-daemon clamav-docs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'clamav-freshclam' instead of 'clamav-data'
Package 'clamav-base' is not installed, so not removed
Package 'clamav-docs' is not installed, so not removed
Package 'clamav-freshclam' is not installed, so not removed
The following packages will be REMOVED:
  clamav-daemon
0 upgraded, 0 newly installed, 1 to remove and 106 not upgraded.
3 not fully installed or removed.
After this operation, 1,083 kB disk space will be freed.
Do you want to continue? [Y/n] y
dpkg: error processing package clamav-daemon (--remove):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 clamav-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
mom@mom-Inspiron-1720:~$ 


**Running the update and upgrade command:**

mom@mom-Inspiron-1720:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [62.0 kB]             
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [160 kB]   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [73.2 kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,389 B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [82.7 kB] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [40.2 kB]
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease                             
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                         
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages                  
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty InRelease                              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release.gpg                            
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release [62.0 kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Sources                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_CA               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Sources                     
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main i386 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted i386 Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en_CA                 
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [15.1 kB]                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty InRelease                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en_CA             
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release.gpg                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en                
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main i386 Packages [363 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [3,001 B]            
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main i386 Packages                
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [1,397 B]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe i386 Packages [222 kB]
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [9,567 B]
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Translation-en [171 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Translation-en  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Translation-en [112 kB]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en_CA           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en_CA            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en_CA           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en               
Fetched 1,387 kB in 13s (106 kB/s)                                             
Reading package lists... Done

mom@mom-Inspiron-1720:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 clamav-daemon : Depends: clamav-base (= 0.98.4+dfsg-2~ubuntu14.04.1) but it is not installed
                 Depends: clamav-freshclam but it is not installed or
                          clamav-data
E: Unmet dependencies. Try using -f.
mom@mom-Inspiron-1720:~$ 

```

Thanks for the suggestions I feel we'll have this solved in a day at most :)

---

### Post by ian-weisser on 2014-12-08
> **pokedadude said:**
> dpkg: error processing package clamav-daemon (--remove):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal

I recommend trying the action suggested by dpkg:
```
sudo apt-get install --reinstall clamav-daemon
```

If it does not work, the error message will give us a clue toward the next step.

---

### Post by pokedadude on 2014-12-08
**This is what I got when I ran the command:**
```

mom@mom-Inspiron-1720:~$ sudo apt-get install --reinstall clamav-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 clamav-daemon : Depends: clamav-base (= 0.98.5+addedllvm-0ubuntu0.14.04.1) but it is not going to be installed
                 Depends: clamav-freshclam but it is not going to be installed or
                          clamav-data
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mom@mom-Inspiron-1720:~$

```

---

### Post by ian-weisser on 2014-12-08
Okay, let's work down that chain of dependencies until we discover the underlying reason:
```
sudo apt-get install clamav-base
```

---

### Post by pokedadude on 2014-12-08
**That's what I got:**
```

mom@mom-Inspiron-1720:~$ sudo apt-get install clamav-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 clamav-daemon : Depends: clamav-freshclam but it is not going to be installed or
                          clamav-data
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mom@mom-Inspiron-1720:~$

```

---

### Post by ian-weisser on 2014-12-08
Keep following the trail...
```
sudo apt-get install clamav-freshclam
```

---

### Post by pokedadude on 2014-12-08
**Results were:**
```

mom@mom-Inspiron-1720:~$ sudo apt-get install clamav-freshclam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 clamav-daemon : Depends: clamav-base (= 0.98.5+addedllvm-0ubuntu0.14.04.1) but it is not going to be installed
 clamav-freshclam : Depends: clamav-base (>= 0.98.5+addedllvm-0ubuntu0.14.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mom@mom-Inspiron-1720:~$ 

mom@mom-Inspiron-1720:~$ sudo apt-get install clamav-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 clamav-daemon : Depends: clamav-freshclam but it is not going to be installed or
                          clamav-data
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mom@mom-Inspiron-1720:~$ 
mom@mom-Inspiron-1720:~$ sudo apt-get install clamav-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 clamav-daemon : Depends: clamav-base (= 0.98.5+addedllvm-0ubuntu0.14.04.1) but it is not going to be installed
                 Depends: clamav-freshclam but it is not going to be installed or
                          clamav-data
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mom@mom-Inspiron-1720:~$ 


mom@mom-Inspiron-1720:~$ sudo apt-get install clamav-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 clamav-daemon : Depends: clamav-base (= 0.98.5+addedllvm-0ubuntu0.14.04.1) but it is not going to be installed
                 Depends: clamav-freshclam but it is not going to be installed or
                          clamav-data
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mom@mom-Inspiron-1720:~$ 


mom@mom-Inspiron-1720:~$ sudo apt-get install clamav-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'clamav-freshclam' instead of 'clamav-data'
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 clamav-daemon : Depends: clamav-base (= 0.98.5+addedllvm-0ubuntu0.14.04.1) but it is not going to be installed
 clamav-freshclam : Depends: clamav-base (>= 0.98.5+addedllvm-0ubuntu0.14.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mom@mom-Inspiron-1720:~$

```

---

### Post by ian-weisser on 2014-12-08
Feel like we're eating our tail? And going in circles?
Well, it was worth a try. Most problems really can get resolved that way.

Let's get out a bigger hammer and try the removal with dpkg.
```
sudo dpkg --remove clamav-daemon
```

If it doesn't work, stop and show us the output.
If it does work, we can move back to apt.
```
sudo apt-get upgrade
```

---

### Post by pokedadude on 2014-12-08
**Unfortunately nothing really happened and this is what I got: **
```

mom@mom-Inspiron-1720:~$ sudo dpkg --remove clamav-daemon
dpkg: error processing package clamav-daemon (--remove):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 clamav-daemon
mom@mom-Inspiron-1720:~$ 

```

Thanks for the suggestions

---

### Post by ian-weisser on 2014-12-08
I expected that, but it was worth a try.
Let's increment up to the next bigger hammer:
```
sudo dpkg --remove --force-remove-reinstreq clamav-daemon
```
The --force-* commands in dpkg are _really_ powerful and should not be used lightly.

---

### Post by pokedadude on 2014-12-08
**This was the output:**
```

mom@mom-Inspiron-1720:~$ sudo dpkg --remove --force-remove-reinstreq clamav-daemon
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
(Reading database ... 304255 files and directories currently installed.)
Removing clamav-daemon (0.98.4+dfsg-2~ubuntu14.04.1) ...
/etc/init.d/clamav-daemon: 164: export: Default:: bad variable name
invoke-rc.d: initscript clamav-daemon, action "stop" failed.
dpkg: error processing package clamav-daemon (--remove):
 subprocess installed pre-removal script returned error exit status 2
/etc/init.d/clamav-daemon: 164: export: Default:: bad variable name
invoke-rc.d: initscript clamav-daemon, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 clamav-daemon
mom@mom-Inspiron-1720:~$ 

```

---

### Post by ian-weisser on 2014-12-08
Try the same command again. See if the error message is the same or different.
--force-remove-reinstreq should have removed the package from the dpkg database, regardless of whatever files it left littered and inert around your system.

---

### Post by pokedadude on 2014-12-08
Nope it's still the same error, also do you think I should delete this file ```
 /etc/init.d/clamav-daemon 
```

---

### Post by ian-weisser on 2014-12-08
Don't delete it. That will cause a different error (File Not Found).
However, you can replace it with an empty file. That won't cause an error.

---

### Post by pokedadude on 2014-12-08
**I cant seem to replace the file even with elevated privledges, although I opened up the clamav-daemon file and this was the part that had a "bad variable" name:**

```

{
  CLAMAVCONF="$1"
  
  if [ -e "$CLAMAVCONF" ]; then
    for variable in `egrep -v '^[[:space:]]*(#|$)' "$CLAMAVCONF" | awk '{print $1}'`; do
      case "$variable" in
        DatabaseMirror)
        if [ -z "$DatabaseMirror" ]; then
          for i in `grep ^$variable $CLAMAVCONF | awk '{print $2}'`; do
            value="$value $i"
          done
        else
          continue
        fi
        ;;
        DatabaseCustomURL)
        if [ -z "$DatabaseCustomURL" ]; then
          for i in `grep ^$variable $CLAMAVCONF | awk '{print $2}'`; do
            value="$value $i"
          done
        else
          continue
        fi
        ;;
        IncludePUA)
        if [ -z "$IncludePUA" ]; then
          for i in `grep ^$variable $CLAMAVCONF | awk '{print $2}'`; do
            value="$i $value"
          done
        else
          continue
        fi
        ;;
        ExcludePUA)
        if [ -z "$ExcludePUA" ]; then
          for i in `grep ^$variable $CLAMAVCONF | awk '{print $2}'`; do
            value="$i $value"
          done
        else
          continue
        fi
        ;;
        ExtraDatabase)
        if [ -z "$ExtraDatabase" ]; then
          for i in `grep ^$variable $CLAMAVCONF | awk '{print $2}'`; do
            value="$value $i"
          done
        else
          continue
        fi
        ;;
        VirusEvent|OnUpdateExecute|OnErrorExecute|RejectMsg)
        value=`grep ^$variable $CLAMAVCONF | head -n1 | sed -e s/$variable\ //`
        ;;
        *)
        value=`grep "^$variable[[:space:]]" $CLAMAVCONF | head -n1 | awk '{print $2}'`
        ;;
      esac
      if [ -z "$value" ]; then 
        export "$variable"="true"
      elif [ "$value" != "$variable" ]; then
      **  export "$variable"="$value"**
      else
        export "$variable"="true"
      fi
      unset value
    done
  fi
}


```

**I bolded the specific line that had the bad variable**

---

### Post by ian-weisser on 2014-12-09
> **pokedadude said:**
> **I cant seem to replace the file**

Error?
Permission?
No feedback at all?

---

