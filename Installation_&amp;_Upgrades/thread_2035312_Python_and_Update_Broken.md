---
title: "Python and Update Broken?"
date: 2012-07-30
forum: Installation &amp; Upgrades
---

### Post by volos on 2012-07-30
I was trying to upgrade from 10.04 when the internet connection were I am went out (not power fail, satellite is my only internet option).  Trying to come back to it: 

```
do-release-upgrade
do-release-upgrade
bash: /usr/bin/do-release-upgrade: /usr/bin/python: bad interpreter: No such file or directory

```I have no idea how I lost python.

```

sudo apt-get install python2.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python2.7 is already the newest version.
python2.7 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up update-manager (1:0.152.25.12) ...
/var/lib/dpkg/info/update-manager.postinst: 7: pycompile: not found
dpkg: error processing update-manager (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

```So then the update-manager won't work (guessing because python jumped ship).  Just be sure I tried:

```

sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up update-manager (1:0.152.25.12) ...
/var/lib/dpkg/info/update-manager.postinst: 7: pycompile: not found
dpkg: error processing update-manager (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I didn't save the errors from the failed upgrade because I new the internet had failed, and was planning to come back to it, I don't know what they were.  I also can't understand how this ended with python deleted?  More confusing to me as that I seem to have gone into a partial upgrade that put me at 11.10 not 12.04.  I know this seems like a lot of problems.

Don't know if this will add any light:
```
sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sudo apt-get update
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release                                      
Get:3 http://dl.google.com stable/main amd64 Packages [766 B]                  
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Get:4 http://dl.google.com stable/main i386 Packages [770 B]                   
Ign http://dl.google.com stable/main TranslationIndex                          
Get:5 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Ign http://archive.canonical.com oneiric InRelease                             
Get:6 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://security.ubuntu.com oneiric-security InRelease                      
Get:7 http://us.archive.ubuntu.com oneiric Release [40.8 kB]                   
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Get:8 http://security.ubuntu.com oneiric-security Release.gpg [198 B]          
Get:9 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]           
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric Release                                   
Get:10 http://security.ubuntu.com oneiric-security Release [40.8 kB]           
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://extras.ubuntu.com oneiric/main Sources                              
Get:11 http://us.archive.ubuntu.com oneiric/main Sources [877 kB]              
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Get:12 http://security.ubuntu.com oneiric-security/main Sources [51.9 kB]      
Get:13 http://security.ubuntu.com oneiric-security/restricted Sources [1,959 B]
Get:14 http://security.ubuntu.com oneiric-security/universe Sources [18.9 kB]  
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Get:15 http://security.ubuntu.com oneiric-security/multiverse Sources [1,641 B]
Get:16 http://security.ubuntu.com oneiric-security/main amd64 Packages [190 kB]
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Get:17 http://security.ubuntu.com oneiric-security/restricted amd64 Packages [3,980 B]
Get:18 http://security.ubuntu.com oneiric-security/universe amd64 Packages [50.6 kB]
Get:19 http://security.ubuntu.com oneiric-security/multiverse amd64 Packages [3,218 B]
Get:20 http://security.ubuntu.com oneiric-security/main i386 Packages [190 kB]
Get:21 http://security.ubuntu.com oneiric-security/restricted i386 Packages [3,939 B]
Get:22 http://security.ubuntu.com oneiric-security/universe i386 Packages [50.7 kB]
Get:23 http://us.archive.ubuntu.com oneiric/restricted Sources [5,351 B]       
Get:24 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [3,380 B]
Get:25 http://us.archive.ubuntu.com oneiric/universe Sources [4,677 kB]        
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://security.ubuntu.com oneiric-security/main Translation-en
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Get:26 http://us.archive.ubuntu.com oneiric/multiverse Sources [149 kB]        
Get:27 http://us.archive.ubuntu.com oneiric/main amd64 Packages [1,226 kB]     
Get:28 http://us.archive.ubuntu.com oneiric/restricted amd64 Packages [8,261 B]
Get:29 http://us.archive.ubuntu.com oneiric/universe amd64 Packages [4,460 kB] 
Get:30 http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages [117 kB] 
Get:31 http://us.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]      
Get:32 http://us.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B] 
Get:33 http://us.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]  
Get:34 http://us.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]  
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Get:35 http://us.archive.ubuntu.com oneiric-updates/main Sources [148 kB]      
Get:36 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [3,347 B]
Get:37 http://us.archive.ubuntu.com oneiric-updates/universe Sources [57.6 kB] 
Get:38 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3,666 B]
Get:39 http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages [373 kB]
Get:40 http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages [6,656 B]
Get:41 http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages [123 kB]
Get:42 http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [6,200 B]
Get:43 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [373 kB]
Get:44 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [6,631 B]
Get:45 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [124 kB]
Get:46 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,371 B]
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en       
Fetched 19.3 MB in 55min 59s (46 kB/s)                                         
Reading package lists... Done
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up update-manager (1:0.152.25.12) ...
/var/lib/dpkg/info/update-manager.postinst: 7: pycompile: not found
dpkg: error processing update-manager (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up update-manager (1:0.152.25.12) ...
/var/lib/dpkg/info/update-manager.postinst: 7: pycompile: not found
dpkg: error processing update-manager (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Can someone tell me how to manually repair python/update-manager?  Downloading the new ISO for a re-install will be quite prohibitive, and I don't know if I can find my old one.  Several related items are of course also broken (software center etc).

~Thanks

---

### Post by oldfred on 2012-07-30
I do not know how it could get you to 11.10 from 10.04. You only mormal choice should have been 10.10, and after 12.04.1 is released then it will offer 12.04. But you can force the upgrade from 10.04 to 12.04 anytime. But it does not skip versions.

Do you have liveCD or USB of 12.04? You probably should anyway as I normally suggest having a repairCD or liveCD for the current version of every system installed.

The easiest at this point is probably backup /home and do a total clean install. If you installed any other special software that might save in system folders rather than /home then back that up also.

You may be able to chroot into your system and do major repairs that way.

The instructions from drs305 are just for grub2 reinstall, but you then can run any other update, repair or upgrade commands from the chroot.
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

Best command to reset apt sources to distro release defaults?
[http://ubuntuforums.org/showthread.php?t=1858451](http://ubuntuforums.org/showthread.php?t=1858451)

You can force changes (but understand not risk free)
This edits sources to change from one version to another.
sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list

Then this one:
sudo apt-get update && sudo apt-get dist-upgrade

latest stable release:
sudo do-release-upgrade
upgrade your system if possible to the latest unstable/beta, I think this takes you to 12.10 Quantal, not 12.04 Precise now, but may depend on what version it thinks it is?
sudo update-manager -d

---

### Post by volos on 2012-07-30
I'm working on downloading the full ISO now, as I figured that would be the best option.  My speeds are 45-60kbps with spotty connectivity to the ISP, so such a task takes considerable time.

I will try to chroot, and I've just cloned the HD as I can see this ending badly.

---

### Post by oldfred on 2012-07-30
Good backups are always the best idea. :)

---

