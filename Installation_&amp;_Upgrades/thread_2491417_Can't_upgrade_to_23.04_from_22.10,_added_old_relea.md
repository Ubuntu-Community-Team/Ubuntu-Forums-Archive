---
title: "Can't upgrade to 23.04 from 22.10, added old releases to the sources.list"
date: 2023-10-07
forum: Installation &amp; Upgrades
---

### Post by sony_gamer on 2023-10-07
I'm on 22.10 and trying to upgrade to 23.04.  I've added the following to my sources.list
```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ kinetic main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ kinetic-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ kinetic-security main restricted universe multiverse

# Optional
deb http://old-releases.ubuntu.com/ubuntu/ kinetic-backports main restricted universe multiverse
```

I still get the following
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo do-release-upgrade
...
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libglibutil python3-gbinder
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

Please install all available updates for your release before upgrading.
[user]@workstation:~$ 

```

I'd rather not do a fresh install if I can avoid it.

---

### Post by MAFoElffen on 2023-10-07
Have you updated all packages to current at the end of life? Did you then disable all PPA's?

Why do you want to go to 23.04 instead of an LTS? <-- Just out of curiosity...

---

### Post by MAFoElffen on 2023-10-07
Do a very good backup to external media.

Prepare a bootable Installer LiveUSB, for the just in cases.

Recommended would be to do a fresh install and migrate the data to the new install. But having said that...

Then do:
```

# Just to ensure everything is up to date
sudo apt update
sudo apt upgrade
# Change the sources list to jammy's repo's
sudo cp /etc/apt/sources.list /etc/apt/sources.list.kenetic
sudo sed -i 's/old-releases/us\.archive/g' /etc/apt/sources.list
sudo sed -i 's/kenetic/jammy/g' /etc/apt/sources.list
grep . /etc/apt/sources.list

```
Check to ensure everything looks okay before preceding.
```

# Upgrade the release one step up to jammy
sudo apt update
sudo apt upgrade

```
Reboot. Test. Make sure everything is okay.

Then if you still want to upgrade to Lunar, then
```

sudo do-release-upgrade -d

```

---

### Post by sony_gamer on 2023-10-08
I'm wanting to update to something that works, but also a version that has decent Radeon graphics drivers.  I've tried to update everything ... will be rebooting and trying to update in a moment.

```
[user]@workstation:~$ sudo apt update
sudo apt upgrade
[sudo] password for [user]: 
Ign:1 http://security.ubuntu.com/ubuntu kinetic-security InRelease
Ign:2 http://ca.archive.ubuntu.com/ubuntu kinetic InRelease                    
Err:3 http://security.ubuntu.com/ubuntu kinetic-security Release               
  404  Not Found [IP: 91.189.91.81 80]
Ign:4 http://ca.archive.ubuntu.com/ubuntu kinetic-updates InRelease            
Hit:5 https://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:6 https://repo.radeon.com/amdgpu/5.4.1/ubuntu jammy InRelease              
Hit:7 https://deb.termius.com squeeze InRelease                                
Ign:8 http://ca.archive.ubuntu.com/ubuntu kinetic-backports InRelease          
Hit:9 https://repo.radeon.com/rocm/apt/5.4.1 jammy InRelease                   
Err:10 http://ca.archive.ubuntu.com/ubuntu kinetic Release                     
  404  Not Found [IP: 91.189.91.83 80]
Err:11 http://ca.archive.ubuntu.com/ubuntu kinetic-updates Release             
  404  Not Found [IP: 91.189.91.83 80]
Err:12 http://ca.archive.ubuntu.com/ubuntu kinetic-backports Release           
  404  Not Found [IP: 91.189.91.83 80]
Hit:13 https://ppa.launchpadcontent.net/obsproject/obs-studio/ubuntu kinetic InRelease
Hit:14 http://old-releases.ubuntu.com/ubuntu kinetic InRelease                 
Ign:15 https://repo.waydro.id ubuntu-devel InRelease
Hit:16 http://old-releases.ubuntu.com/ubuntu kinetic-updates InRelease
Hit:17 http://old-releases.ubuntu.com/ubuntu kinetic-security InRelease
Hit:18 http://old-releases.ubuntu.com/ubuntu kinetic-backports InRelease
Err:19 https://repo.waydro.id ubuntu-devel Release
  404  Not Found [IP: 205.185.118.53 443]
Reading package lists... Done
E: The repository 'http://security.ubuntu.com/ubuntu kinetic-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ca.archive.ubuntu.com/ubuntu kinetic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ca.archive.ubuntu.com/ubuntu kinetic-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ca.archive.ubuntu.com/ubuntu kinetic-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://repo.radeon.com/rocm/apt/5.4.1 jammy InRelease' doesn't support architecture 'i386'
E: The repository 'https://repo.waydro.id ubuntu-devel Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libglibutil python3-gbinder
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
[user]@workstation:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.kenetic
[user]@workstation:~$ sudo sed -i 's/old-releases/us\.archive/g' /etc/apt/sources.list
[user]@workstation:~$ sudo sed -i 's/kenetic/jammy/g' /etc/apt/sources.list
[user]@workstation:~$ grep . /etc/apt/sources.list
# deb cdrom:[Ubuntu 22.10 _Kinetic Kudu_ - Release amd64 (20221020)]/ kinetic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic-updates main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic universe
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic-updates universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic-updates multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic-updates multiverse
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu kinetic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu kinetic-security main restricted
deb http://security.ubuntu.com/ubuntu kinetic-security universe
# deb-src http://security.ubuntu.com/ubuntu kinetic-security universe
deb http://security.ubuntu.com/ubuntu kinetic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu kinetic-security multiverse
# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
## EOL upgrade sources.list
# Required
deb http://us.archive.ubuntu.com/ubuntu/ kinetic main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ kinetic-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ kinetic-security main restricted universe multiverse
# Optional
deb http://us.archive.ubuntu.com/ubuntu/ kinetic-backports main restricted universe multiverse
[user]@workstation:~$ sudo apt update
sudo apt upgrade
Ign:1 http://us.archive.ubuntu.com/ubuntu kinetic InRelease
Ign:2 http://us.archive.ubuntu.com/ubuntu kinetic-updates InRelease                                                                                                     
Ign:3 http://ca.archive.ubuntu.com/ubuntu kinetic InRelease                                                                                                             
Ign:4 http://us.archive.ubuntu.com/ubuntu kinetic-security InRelease                                                                                                    
Ign:5 http://ca.archive.ubuntu.com/ubuntu kinetic-updates InRelease                                                                                                     
Ign:6 http://us.archive.ubuntu.com/ubuntu kinetic-backports InRelease                                                                                                   
Ign:7 http://ca.archive.ubuntu.com/ubuntu kinetic-backports InRelease                                                                                                   
Err:8 http://us.archive.ubuntu.com/ubuntu kinetic Release                                                                                                               
  404  Not Found [IP: 91.189.91.39 80]
Ign:9 http://security.ubuntu.com/ubuntu kinetic-security InRelease                                                                                                      
Hit:10 https://repo.radeon.com/amdgpu/5.4.1/ubuntu jammy InRelease                                                                                                      
Hit:11 https://dl.google.com/linux/chrome/deb stable InRelease                                                                                                          
Err:12 http://us.archive.ubuntu.com/ubuntu kinetic-updates Release                                                                                                      
  404  Not Found [IP: 91.189.91.39 80]
Err:13 http://ca.archive.ubuntu.com/ubuntu kinetic Release                                                                                                              
  404  Not Found [IP: 91.189.91.82 80]
Hit:14 https://deb.termius.com squeeze InRelease                                                                                                                        
Hit:15 https://repo.radeon.com/rocm/apt/5.4.1 jammy InRelease                                                                                                           
Err:16 http://us.archive.ubuntu.com/ubuntu kinetic-security Release                                                                                                     
  404  Not Found [IP: 91.189.91.39 80]
Err:17 http://ca.archive.ubuntu.com/ubuntu kinetic-updates Release                                                                                                      
  404  Not Found [IP: 91.189.91.82 80]
Err:18 http://us.archive.ubuntu.com/ubuntu kinetic-backports Release                                                                                                    
  404  Not Found [IP: 91.189.91.39 80]
Err:19 http://security.ubuntu.com/ubuntu kinetic-security Release                                                                                     
  404  Not Found [IP: 185.125.190.39 80]
Err:20 http://ca.archive.ubuntu.com/ubuntu kinetic-backports Release                                                                                  
  404  Not Found [IP: 91.189.91.82 80]
Hit:21 https://ppa.launchpadcontent.net/obsproject/obs-studio/ubuntu kinetic InRelease                 
Ign:22 https://repo.waydro.id ubuntu-devel InRelease
Err:23 https://repo.waydro.id ubuntu-devel Release
  404  Not Found [IP: 205.185.118.53 443]
Reading package lists... Done
E: The repository 'http://us.archive.ubuntu.com/ubuntu kinetic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu kinetic-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ca.archive.ubuntu.com/ubuntu kinetic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu kinetic-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ca.archive.ubuntu.com/ubuntu kinetic-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu kinetic-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu kinetic-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ca.archive.ubuntu.com/ubuntu kinetic-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://repo.radeon.com/rocm/apt/5.4.1 jammy InRelease' doesn't support architecture 'i386'
E: The repository 'https://repo.waydro.id ubuntu-devel Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libglibutil python3-gbinder
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
[user]@workstation:~$ 
```

---

### Post by MAFoElffen on 2023-10-08
If you got error updating... when you started out... You should have stopped right there. It never updated/upgraded from your original sources.list.

This is out-of-the-box kind of stuff. Any problem, stop and ask. Do not just continue. That is potentially risking causing problems on top of problems. Understood?

Please post the contents of /etc/apt/sources.list.kinetic (the backup copy I had you make, for the just-in-cases.)

You did take a good backup before that right? Something to fall back to?

---

### Post by sony_gamer on 2023-10-13
The backup of the sources file

```

/etc/apt$ cat sources.list.kenetic 
# deb cdrom:[Ubuntu 22.10 _Kinetic Kudu_ - Release amd64 (20221020)]/ kinetic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic-updates main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic universe
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic-updates universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic-updates multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ kinetic-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ kinetic-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu kinetic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu kinetic-security main restricted
deb http://security.ubuntu.com/ubuntu kinetic-security universe
# deb-src http://security.ubuntu.com/ubuntu kinetic-security universe
deb http://security.ubuntu.com/ubuntu kinetic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu kinetic-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.

## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ kinetic main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ kinetic-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ kinetic-security main restricted universe multiverse

# Optional
deb http://old-releases.ubuntu.com/ubuntu/ kinetic-backports main restricted universe multiverse

```

---

### Post by MAFoElffen on 2023-10-13
Your sources.list started out as invalid, and had duplicate entries pointing to different places.

Here is how I suggest you fix that. First copy the contents of this into a file and name it ~/Documents/sources.list.2210-old
```

deb http://old-releases.ubuntu.com/ubuntu/ kinetic main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ kinetic-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ kinetic-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ kinetic-backports main restricted universe multiverse

```
Then copy this into another file called ~/Documents/sources.list.2204-new
```

deb http://ca.archive.ubuntu.com/ubuntu/ jammy main restricted universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ jammy-updates main restricted universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
deb http://ca.security.ubuntu.com/ubuntu jammy-security main restricted universe muitiverse

```
Then from a terminal do this
```

sudo cp ~/Documents/sources.list.2210-old /etc/apt/sources.list
sudo apt update
# If there are any error with that, stop here...
# If successful, then
sudo apt upgrade

```
If successful at this point, then do
```

sudo cp ~/Documents/sources.list.2204-new /etc/apt/sources.list
sudo apt update
sudo apt upgrade

```

---

### Post by sony_gamer on 2023-10-13
Did that, ran into an issue with the radeon repo

```

[user]@workstation:~$ sudo cp ~/Documents/sources.list.2210-old /etc/apt/sources.list
[user]@workstation:~$ sudo apt update
Hit:1 https://repo.radeon.com/amdgpu/5.4.1/ubuntu jammy InRelease
Hit:2 https://repo.radeon.com/rocm/apt/5.4.1 jammy InRelease                                                                                                                                               
Hit:3 https://deb.termius.com squeeze InRelease                                                                                                                                                            
Hit:4 https://dl.google.com/linux/chrome/deb stable InRelease                                                                                                               
Hit:5 http://old-releases.ubuntu.com/ubuntu kinetic InRelease                                                                                         
Hit:6 http://old-releases.ubuntu.com/ubuntu kinetic-updates InRelease                                                           
Hit:7 https://ppa.launchpadcontent.net/obsproject/obs-studio/ubuntu kinetic InRelease                  
Hit:8 http://old-releases.ubuntu.com/ubuntu kinetic-security InRelease
Hit:9 http://old-releases.ubuntu.com/ubuntu kinetic-backports InRelease
Ign:10 https://repo.waydro.id ubuntu-devel InRelease
Err:11 https://repo.waydro.id ubuntu-devel Release
  404  Not Found [IP: 205.185.118.53 443]
Reading package lists... Done
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://repo.radeon.com/rocm/apt/5.4.1 jammy InRelease' doesn't support architecture 'i386'
E: The repository 'https://repo.waydro.id ubuntu-devel Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

There are more repos then just the sources.list
```

[user]@workstation:/etc/apt/sources.list.d$ ll
total 56
drwxr-xr-x 2 root root 4096 Oct  7 20:54 ./
drwxr-xr-x 8 root root 4096 Oct  8 20:01 ../
-rw-r--r-- 1 root root  124 Oct  7 20:54 amdgpu.list
-rw-r--r-- 1 root root  123 Dec  6  2022 amdgpu.list.dpkg-dist
-rw-r--r-- 1 root root  124 Feb 14  2023 amdgpu.list.save
-rw-r--r-- 1 root root  181 Oct  7 20:54 amdgpu-proprietary.list
-rw-r--r-- 1 root root  183 Feb 14  2023 amdgpu-proprietary.list.save
-rw-r--r-- 1 root root  190 Oct  7 20:54 google-chrome.list
-rw-r--r-- 1 root root  166 Oct  7 20:54 obsproject-ubuntu-obs-studio-kinetic.list
-rw-r--r-- 1 root root   54 Oct  7 20:54 rocm.list
-rw-r--r-- 1 root root   67 Dec  6  2022 rocm.list.dpkg-dist
-rw-r--r-- 1 root root   54 Feb 14  2023 rocm.list.save
-rw-r--r-- 1 root root  259 Oct  7 20:54 termius.list
-rw-r--r-- 1 root root   91 Oct  7 20:54 waydroid.list

```

---

### Post by MAFoElffen on 2023-10-13
As when you are going to do any release upgrades, go into the "Software & Upgrades" app and disable all the external third party repo's. 

22.04 and 23.04 have amdgpu opensource drivers in the kernel. Do you really need the third party binary driver? Maybe you should plan on uninstalling the driver and reinstalling if you need to later(?)

---

### Post by sony_gamer on 2023-10-22
I upgraded to 23.04 then 23.10.  Unfortunately I've run into a different issue, which may need a post in a different topic.  I've got large black borders around the file browser, settings, gnome extension manager, but not firefox, terminal, or chrome.  I've checked the extensions but I don't think there's anything causing this.

[ATTACH=CONFIG]292914[/ATTACH]

---

### Post by MAFoElffen on 2023-10-22
Yes. Please select the "Thread Tools" link in the upper right of the first page of this thread, to mark this thread as "Solved"... and open a new thread on this new UI issue.

Happy that things worked out for you on getting to a currently supported release. Now just minor details in comparison to that. LOL

---

