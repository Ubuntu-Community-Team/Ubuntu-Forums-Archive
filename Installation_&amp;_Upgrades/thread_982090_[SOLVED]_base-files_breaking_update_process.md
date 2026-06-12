---
title: "[SOLVED] base-files breaking update process"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by Little Blue on 2008-11-14
I tried to update my packages as one is generally asked to every now and then by the package manager, but something went wrong and it now aborts whenever it attempts to process the base-files update, something it tries to do regardless of which packages it tries to update from the list.

Attempting to update it in the terminal instead doesn't help, and using the synaptic package manager to try reinstalling the base-files has no success either...

I am running 8.04.

This is the output of dpkg --configure -a
```
blue@blue-laptop:~$ sudo dpkg --configure -a
[sudo] password for blue: 
Setting up base-files (4.0.1ubuntu5.8.04.3) ...
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
find: /var/cache/anthy: No such file or directory
Aborted
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 134
Errors were encountered while processing:
 base-files
```

aptitude update
```
blue@blue-laptop:~$ sudo aptitude update
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB            
Hit http://gb.archive.ubuntu.com hardy Release.gpg                              
Hit http://gb.archive.ubuntu.com hardy/main Translation-en_GB                   
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB      
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com hardy-security Release                
Hit http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB  
Hit http://gb.archive.ubuntu.com hardy/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy-updates Release.gpg
Ign http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
Hit http://wine.budgetdedicated.com hardy Release.gpg
Ign http://wine.budgetdedicated.com hardy/main Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy Release 
Hit http://gb.archive.ubuntu.com hardy-updates Release                          
Hit http://security.ubuntu.com hardy-security/main Packages          
Hit http://wine.budgetdedicated.com hardy Release                   
Hit http://gb.archive.ubuntu.com hardy/main Packages                
Hit http://gb.archive.ubuntu.com hardy/restricted Packages
Hit http://gb.archive.ubuntu.com hardy/main Sources
Hit http://gb.archive.ubuntu.com hardy/restricted Sources
Hit http://gb.archive.ubuntu.com hardy/universe Packages
Hit http://gb.archive.ubuntu.com hardy/universe Sources              
Hit http://gb.archive.ubuntu.com hardy/multiverse Packages           
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://security.ubuntu.com hardy-security/restricted Sources     
Hit http://gb.archive.ubuntu.com hardy/multiverse Sources            
Ign http://wine.budgetdedicated.com hardy/main Packages
Hit http://gb.archive.ubuntu.com hardy-updates/main Packages
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://gb.archive.ubuntu.com hardy-updates/main Sources
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Sources    
Hit http://security.ubuntu.com hardy-security/universe Packages      
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://gb.archive.ubuntu.com hardy-updates/universe Packages
Hit http://gb.archive.ubuntu.com hardy-updates/universe Sources
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://wine.budgetdedicated.com hardy/main Packages
Reading package lists... Done

```

aptitude upgrade
```
blue@blue-laptop:~$ sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic 
The following packages have been kept back:
  deluge-torrent 
The following packages will be upgraded:
  alacarte clamav clamav-base clamav-freshclam dbus dbus-x11 foo2zjs 
  libclamav3 libdbus-1-3 libsmbclient module-init-tools passwd samba-common 
  smbclient update-notifier update-notifier-common winbind 
The following partially installed packages will be configured:
  base-files 
17 packages upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
Need to get 28.1MB of archives. After unpacking 68.3MB will be freed.
Do you want to continue? [Y/n/?] y
Get:1 http://gb.archive.ubuntu.com hardy-updates/main passwd 1:4.0.18.2-1ubuntu2.1 [566kB]
Get:2 http://gb.archive.ubuntu.com hardy-updates/main libdbus-1-3 1.1.20-1ubuntu3.2 [124kB]
Get:3 http://gb.archive.ubuntu.com hardy-updates/main module-init-tools 3.3-pre11-4ubuntu5.8.04.1 [72.4kB]
Get:4 http://gb.archive.ubuntu.com hardy-updates/main alacarte 0.11.5-0ubuntu1.1 [73.2kB]
Get:5 http://gb.archive.ubuntu.com hardy-updates/universe clamav-base 0.92.1~dfsg2-1.1ubuntu0.3 [12.7MB]
Get:6 http://gb.archive.ubuntu.com hardy-updates/universe libclamav3 0.92.1~dfsg2-1.1ubuntu0.3 [444kB]
Get:7 http://gb.archive.ubuntu.com hardy-updates/universe clamav-freshclam 0.92.1~dfsg2-1.1ubuntu0.3 [218kB]
Get:8 http://gb.archive.ubuntu.com hardy-updates/universe clamav 0.92.1~dfsg2-1.1ubuntu0.3 [894kB]
Get:9 http://gb.archive.ubuntu.com hardy-updates/main dbus 1.1.20-1ubuntu3.2 [282kB]
Get:10 http://gb.archive.ubuntu.com hardy-updates/main dbus-x11 1.1.20-1ubuntu3.2 [43.0kB]
Get:11 http://gb.archive.ubuntu.com hardy-updates/main foo2zjs 20071205-0ubuntu3.1 [1782kB]
Get:12 http://gb.archive.ubuntu.com hardy-updates/main smbclient 3.0.28a-1ubuntu4.7 [4863kB]
Get:13 http://gb.archive.ubuntu.com hardy-updates/main winbind 3.0.28a-1ubuntu4.7 [2248kB]
82% [13 winbind 1033547/2248kB 45%]                                  253kB/s 19sGet:14 http://gb.archive.ubuntu.com hardy-updates/main samba-common 3.0.28a-1ubuntu4.7 [2840kB]
Get:15 http://gb.archive.ubuntu.com hardy-updates/main update-notifier-common 0.70.10 [14.0kB]
Get:16 http://gb.archive.ubuntu.com hardy-updates/main update-notifier 0.70.10 [58.2kB]
Get:17 http://gb.archive.ubuntu.com hardy-updates/main libsmbclient 3.0.28a-1ubuntu4.7 [887kB]
Fetched 28.1MB in 1min49s (257kB/s)                                             
Preconfiguring packages ...
Setting up base-files (4.0.1ubuntu5.8.04.3) ...
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted
find: /var/cache/anthy: No such file or directory
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 134
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up base-files (4.0.1ubuntu5.8.04.3) ...
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted
find: /var/cache/anthy: No such file or directory
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 134
Errors were encountered while processing:
 base-files
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      

```

Any help would be mighty appreciated thanks...

---

### Post by njparton on 2008-11-15
I'm having a similar problem but I get a dpkg error code (1) instead.

I've removed the offending .deb file from the apt cache and run sudo apt-get upgrade again but I get the same error.  I don't seem to be able to remove this package from dpkg as it's essential.

Does anyone have a solution?

---

### Post by njparton on 2008-11-15
Launchpad bug:

[https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/292116](https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/292116)

---

### Post by Little Blue on 2008-11-17
Well at least I ain't the only one this is screwing...

Yeah, I get an error code (1) as well, but I also get a code 134...
```
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 134
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Updating the package list as per the first suggestion in that bug report says works, but when I re-upgrade the same error happens!

So looking at the last comment in there, reinstallation, is that really the only option there is?

---

### Post by njparton on 2008-11-17
I sincerely hope a reinstall isn't required as I'm experiencing this on a production server!
 
I just need to winkle out the corrupted base-files package from dpkg somehow and then to a fresh upgrade.  I've removed the .deb file from the apt cache, but I need to do something with dpkg too, but I don't know what.
 
AARgh!!

---

### Post by Little Blue on 2008-11-17
hehe, I've got a solution, but it feels like a very dangerous and risky solution so use at your own risk. It worked for me at least!

if you have a look in /var/lib/dpkg there should be a status file. Make a backup of that and then open it.

Search for something like

```
Package: base-files
```

If its the same problem I had the status should be

```
Status: install ok half-configured
```

Change that to

```
Status: install ok not-installed
```

And delete everything pertaining to this package (should be the next dozen or so lines) after "Section: admin"

This should leave you with these five lines in the status file

```
Package: base-files
Essential: yes
Status: install ok not-installed
Priority: required
Section: admin
```

then run apt-get -f install

If you check your status file then it should be back to having a long entry for the package with the status: install ok installed

And everything should be fine then!

I hope this works for you as well as it did for me!

---

### Post by njparton on 2008-11-17
Thanks that's interesting, I'll give it a shot this evening.
 
Out of interest, did your error contain the following lines:
 
[B]Setting up base-files (4.0.1ubuntu5.8.04.3) ...
chown: invalid group: `root:utmp'[/B]
 
I think we may have different errors that lead to the same outcome, nevertheless I'll give your idea a shot later on.

---

### Post by Little Blue on 2008-11-17
Sorry, I don't recall getting any errors like that...

---

### Post by njparton on 2008-11-17
That solution didn't work for me, we definitely have different problems :(

---

### Post by Stratos01 on 2008-11-17
> **Little Blue said:**
> hehe, I've got a solution, but it feels like a very dangerous and risky solution so use at your own risk. It worked for me at least!

if you have a look in /var/lib/dpkg there should be a status file. Make a backup of that and then open it.

Search for something like

```
Package: base-files
```

If its the same problem I had the status should be

```
Status: install ok half-configured
```

Change that to

```
Status: install ok not-installed
```

And delete everything pertaining to this package (should be the next dozen or so lines) after "Section: admin"

This should leave you with these five lines in the status file

```
Package: base-files
Essential: yes
Status: install ok not-installed
Priority: required
Section: admin
```

then run apt-get -f install

If you check your status file then it should be back to having a long entry for the package with the status: install ok installed

And everything should be fine then!

I hope this works for you as well as it did for me!

Hi! I was advised to use this instruction for the current problem I have from the absolute beginners section. After I delete all the extra lines and try to save the file, it says that I do not have permission. How should I do that? Thank you!

---

### Post by Stratos01 on 2008-11-17
> **Stratos01 said:**
> Hi! I was advised to use this instruction for the current problem I have from the absolute beginners section. After I delete all the extra lines and try to save the file, it says that I do not have permission. How should I do that? Thank you!


Hi I managed to search and found how to run nautilus as root, thank you!

---

### Post by Little Blue on 2008-11-18
> **njparton said:**
> That solution didn't work for me, we definitely have different problems :(
Ah, sorry to hear that then... I'm not really sure what else to do for it then...

Stratos01, heh, sorry I forgot to mention to edit it as root. Glad you got it fixed though!

---

### Post by njparton on 2008-11-20
My issue was solved via the following thread if anyone's interested:

[https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/292116](https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/292116)

---

