---
title: "no StartX after restart."
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by NCXA on 2012-11-25
Hi, 

After upgrading to 12.04 from 10.4 I have to restart a few times every time I reboot so I can startx. 
otherwise files are locked and I get no GUI. 
if anyone encountered this I would appreciate any input. 

Thanks,
NCXA

---

### Post by ibjsb4 on 2012-11-25
First, make sure everything got upgraded.  In terminal:

sudo apt-get update

Everything ok?  If so, maybe its the display manager.  10o4 used gdm and 12o4 uses lightdm.  Reinstall lightdm and see if that helps.  Could really use more input, are you getting any error messages at all?

---

### Post by NCXA on 2012-11-25
well it's running on a Citrix Xenserver 
could this be related ? 

after running the update command it goes through a list and then exits with 
"Reading package lists... Done"

no prompt for update.

---

### Post by ibjsb4 on 2012-11-25
Usually it spits out something like 0 to upgrade 0 to install at the end.  And yes, this could be related to Xenserver.  Something I have zero experience with.

My only thought now would be start a new thread with xenserver in the title and a link to this thread.  See if you can get some help that way.  I think the mod's in this forum will go for that.

Good luck

---

### Post by NCXA on 2012-11-25
```
gs2@gs2-desktop:~$ sudo apt-get update
[sudo] password for gs2: 
Ign http://il.archive.ubuntu.com precise InRelease
Ign http://il.archive.ubuntu.com precise-updates InRelease                     
Hit http://il.archive.ubuntu.com precise Release.gpg                           
Hit http://il.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://il.archive.ubuntu.com precise Release                               
Hit http://il.archive.ubuntu.com precise-updates Release                       
Hit http://il.archive.ubuntu.com precise/main Sources                 
Hit http://il.archive.ubuntu.com precise/restricted Sources          
Hit http://il.archive.ubuntu.com precise/universe Sources            
Hit http://il.archive.ubuntu.com precise/multiverse Sources          
Hit http://il.archive.ubuntu.com precise/main amd64 Packages         
Hit http://il.archive.ubuntu.com precise/restricted amd64 Packages   
Hit http://il.archive.ubuntu.com precise/universe amd64 Packages     
Hit http://il.archive.ubuntu.com precise/multiverse amd64 Packages   
Hit http://il.archive.ubuntu.com precise/main i386 Packages          
Hit http://il.archive.ubuntu.com precise/restricted i386 Packages    
Ign http://security.ubuntu.com precise-security InRelease            
Ign http://archive.canonical.com precise InRelease                   
Hit http://il.archive.ubuntu.com precise/universe i386 Packages
Hit http://il.archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://il.archive.ubuntu.com precise/main TranslationIndex       
Hit http://il.archive.ubuntu.com precise/multiverse TranslationIndex 
Hit http://il.archive.ubuntu.com precise/restricted TranslationIndex 
Hit http://il.archive.ubuntu.com precise/universe TranslationIndex   
Hit http://il.archive.ubuntu.com precise-updates/main Sources        
Hit http://il.archive.ubuntu.com precise-updates/restricted Sources  
Hit http://il.archive.ubuntu.com precise-updates/universe Sources    
Hit http://il.archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://il.archive.ubuntu.com precise-updates/main amd64 Packages 
Hit http://il.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://il.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://il.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://il.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://il.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://il.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://il.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://il.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://il.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://il.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://il.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://il.archive.ubuntu.com precise/main Translation-en         
Hit http://il.archive.ubuntu.com precise/multiverse Translation-en   
Hit http://il.archive.ubuntu.com precise/restricted Translation-en   
Hit http://archive.canonical.com precise Release.gpg                 
Hit http://security.ubuntu.com precise-security Release.gpg          
Hit http://il.archive.ubuntu.com precise/universe Translation-en
Hit http://il.archive.ubuntu.com precise-updates/main Translation-en
Hit http://il.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://il.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://il.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://security.ubuntu.com precise-security Release              
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://archive.canonical.com precise Release
Hit http://security.ubuntu.com precise-security/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://archive.canonical.com precise/partner amd64 Packages
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://archive.canonical.com precise/partner i386 Packages
Ign http://archive.canonical.com precise/partner TranslationIndex
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Ign http://archive.canonical.com precise/partner Translation-en_US
Ign http://archive.canonical.com precise/partner Translation-en
Reading package lists... Done
gs2@gs2-desktop:~$ 

```
I copied the entire output.
This is exactly what I'm getting.

---

### Post by Bashing-om on 2012-11-25
NCXA; Hi !
Update looks good.
What is the result of:
```
sudo apt-get upgrade
``` which upgrades the installed packages.[INDENT][INDENT]one step at a time <== BDQ

[/INDENT][/INDENT]

---

### Post by NCXA on 2012-11-25
Hi
heres the upgrade : 

```
gs2@gs2-desktop:~$ sudo apt-get update
[sudo] password for gs2: 
Ign http://il.archive.ubuntu.com precise InRelease
Ign http://il.archive.ubuntu.com precise-updates InRelease                     
Hit http://il.archive.ubuntu.com precise Release.gpg                           
Hit http://il.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://il.archive.ubuntu.com precise Release                               
Hit http://il.archive.ubuntu.com precise-updates Release                       
Hit http://il.archive.ubuntu.com precise/main Sources                 
Hit http://il.archive.ubuntu.com precise/restricted Sources          
Hit http://il.archive.ubuntu.com precise/universe Sources            
Hit http://il.archive.ubuntu.com precise/multiverse Sources          
Hit http://il.archive.ubuntu.com precise/main amd64 Packages         
Hit http://il.archive.ubuntu.com precise/restricted amd64 Packages   
Hit http://il.archive.ubuntu.com precise/universe amd64 Packages     
Hit http://il.archive.ubuntu.com precise/multiverse amd64 Packages   
Hit http://il.archive.ubuntu.com precise/main i386 Packages          
Hit http://il.archive.ubuntu.com precise/restricted i386 Packages    
Ign http://security.ubuntu.com precise-security InRelease            
Ign http://archive.canonical.com precise InRelease                   
Hit http://il.archive.ubuntu.com precise/universe i386 Packages
Hit http://il.archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://il.archive.ubuntu.com precise/main TranslationIndex       
Hit http://il.archive.ubuntu.com precise/multiverse TranslationIndex 
Hit http://il.archive.ubuntu.com precise/restricted TranslationIndex 
Hit http://il.archive.ubuntu.com precise/universe TranslationIndex   
Hit http://il.archive.ubuntu.com precise-updates/main Sources        
Hit http://il.archive.ubuntu.com precise-updates/restricted Sources  
Hit http://il.archive.ubuntu.com precise-updates/universe Sources    
Hit http://il.archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://il.archive.ubuntu.com precise-updates/main amd64 Packages 
Hit http://il.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://il.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://il.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://il.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://il.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://il.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://il.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://il.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://il.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://il.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://il.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://il.archive.ubuntu.com precise/main Translation-en         
Hit http://il.archive.ubuntu.com precise/multiverse Translation-en   
Hit http://il.archive.ubuntu.com precise/restricted Translation-en   
Hit http://archive.canonical.com precise Release.gpg                 
Hit http://security.ubuntu.com precise-security Release.gpg          
Hit http://il.archive.ubuntu.com precise/universe Translation-en
Hit http://il.archive.ubuntu.com precise-updates/main Translation-en
Hit http://il.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://il.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://il.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://security.ubuntu.com precise-security Release              
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://archive.canonical.com precise Release
Hit http://security.ubuntu.com precise-security/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://archive.canonical.com precise/partner amd64 Packages
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://archive.canonical.com precise/partner i386 Packages
Ign http://archive.canonical.com precise/partner TranslationIndex
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Ign http://archive.canonical.com precise/partner Translation-en_US
Ign http://archive.canonical.com precise/partner Translation-en
Reading package lists... Done
gs2@gs2-desktop:~$ clear

gs2@gs2-desktop:~$ sudo apt-get upgrade
[sudo] password for gs2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libdirectfb-dev
The following packages will be upgraded:
  convirt
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/2,185 kB of archives.
After this operation, 7,840 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 299744 files and directories currently installed.)
Preparing to replace convirt 1.1-1 (using .../convirt_2.0.1-6_all.deb) ...
Unpacking replacement convirt ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up convirt (2.0.1-6) ...
dbconfig-common: writing config to /etc/dbconfig-common/convirt.conf

Creating config file /etc/dbconfig-common/convirt.conf with new version

Creating config file /etc/convirt/dbconfig.ini with new version
dbconfig-common: flushing administrative password
install common functions sourced.
Processing triggers for python-support ...
gs2@gs2-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libdirectfb-dev
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
gs2@gs2-desktop:~$ 

```

---

### Post by Bashing-om on 2012-11-25
NCXA;
Still lookin good, I suggest to force install of libdirectfb-dev and any others:  
```
sudo apt-get dist-upgrade
```uses smart installation to resolve package conflicts.

Reboot and see if you boot now to GUI environment.
[INDENT]Just try'n to help <== BDQ

[/INDENT]

---

### Post by NCXA on 2012-11-26
still no go : 
hard to copy it now. 
so I'll type it in : 
```
failed to add entry for user gs2.
/usr/lib/update-manager/release-upgrade-motd: 35: /usr/lib/update-manager/release-upgrade-motd: cannot create var/lib/update-notifier/release-upgrade-available : Read-only file system /usr/lib/update-notifier/update-motd-fsck-at-reboot :28 : /usr/lib/update-notifier/update-motd-fsck-at-reboot : Read-only file system 
run-parts : /etc/update-mot.d/98-fsck-at-reboot exited with return code 2 
```

Thats what shows up as soon as I Login. 
and it still goes to tty1 unless I reboot again and let it checkdisk again.

---

### Post by Bashing-om on 2012-11-26
sheesh, That result - to say the least - is a surprise ! Did not anticipate the system mounting in read only mode.
A separate issue all together ? 
Smart system, trying to protect and keep the data intact.
The question is why is the system mounting read-only ? It is my thoughts that this needs addressing rather than forcing the system to read-write to resolve install issues, at this time.
Need to look at the system logs and see if the issue can be determined, however, I am at a loss as to how to manipulate the log files to relay the relevant information to this post.(those files can be huge).
Do you feel comfortable reading your logs ?
That said, let's wait for wiser heads on this forum to advise a means to proceed.


not much help now, waiting ==> BDQ

---

### Post by NCXA on 2012-11-26
ok, Thanks for trying. :(

---

### Post by Bashing-om on 2012-11-27
NCXA;

I have thought about this all night; If this were my system, this is what I would do.
Firstly, as a matter of course, I would examint all my logs -> /var/log/dmesg, /var/log/syslog, /var/log/kern-log. and in the home directory is the hidden file -> .xsessions-errors.

Depending on what I found in the logs I would next boot up my liveCD, and run some file system checks )thus the partitions are not mounted and in use).

One has to be sure of the partitions being checked ( I want to check one partition at a time): terminal code:
```
sudo fdisk -l 
```Remember the "extended" partition is a container for the logical partitions ==> DO NOT run a check on it.
and start running some preliminary file system checks; turn swap off.
terminal code:
```
sudo e2fsck -C0 -p -f -v /dev/sda1
``` [depends on fdisk output's]
do each partition (less swap, no need & not able to check that type of partition),
depending on any errors I would conclude with this: 
```
sudo e2fsck -f -y -v /dev/sda1
```"y" auto answers yes for fixes needing response -see man e2fsck.
checking all my partitions. 

depending on results -> look further ...if all seems good -> reboot, see what haps.
[INDENT][INDENT]still think'n <== BDQ

[/INDENT][/INDENT]

---

### Post by NCXA on 2012-11-27
I'll look into this and post back
Thanks. 
sorry for taking your sleep time. better dream about sunshine and unicorns :P
:popcorn:

---

### Post by Bashing-om on 2012-11-27
Haw haw ... but awaiting what develops...
great success <== BDQ

---

