---
title: "Hardinfo install fails on 20.04.2 LTS"
date: 2021-04-05
forum: Installation &amp; Upgrades
---

### Post by fiscoking on 2021-04-05
Hi,

I've just completed a fresh install of Ubuntu 20.04.2 LTS and the hardinfo install fails. No other applications have been installed. I've tried installing from the GUI and from the command line - which gives a bit more information.

Any idea on what I have to do to get hardinfo to install?

I'm looking for a gui hardware reporting package, not a command line solution, hence hardinfo.

Thanks.

xxx@xxx-Latitude-5400:~$ sudo apt-get install hardinfo
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 hardinfo : Depends: zlib1g-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by TheFu on 2021-04-05
First thing after any install is to patch and lets the OS install any proprietary drivers needed

```
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall
```
May need to reboot if /var/run/reboot-required is created, so check that and reboot, if needed.

Then try to install packages. If they are in the Canonical repos, but won't install, check that you have all the Canonical repos enabled - perhaps Universe isn't on?

After that, run a backup, but that should be obvious.  Do all these things at least weekly for great happiness - that includes the backups. :P

---

### Post by fiscoking on 2021-04-05
Hello ThFu,

I've run the above commands with the same result, even after a reboot;

 xxx@xxx-Latitude-5400:~$ sudo apt update
 [sudo] password for xxx:  
 Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal InRelease
 Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 All packages are up-to-date.
 xxx@xxx-Latitude-5400:~$ sudo apt full-upgrade
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 Calculating upgrade... Done
 0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
 xxx@xxx-Latitude-5400:~$ sudo ubuntu-drivers autoinstall
 No drivers found for installation.
 xxx@xxx-Latitude-5400:~$ sudo apt-get install hardinfo
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 Some packages could not be installed. This may mean that you have
 requested an impossible situation or if you are using the unstable
 distribution that some required packages have not yet been created
 or been moved out of Incoming.
 The following information may help to resolve the situation:
 
 
 The following packages have unmet dependencies.
  hardinfo : Depends: zlib1g-dev but it is not going to be installed
 E: Unable to correct problems, you have held broken packages.
 xxx@xxx-Latitude-5400:~$

---

### Post by tea for one on 2021-04-05
> **fiscoking said:**
> 
 The following packages have unmet dependencies.
  hardinfo : Depends: zlib1g-dev but it is not going to be installed
 E: Unable to correct problems, you have held broken packages.
 xxx@xxx-Latitude-5400:~$

Have you tried to repair/remove/re-install the broken packages?

You could boot into recovery mode and try [COLOR="#0000FF"]Repair broken packages[/COLOR]?

---

### Post by TheFu on 2021-04-05
Try:
```
sudo apt install --reinstall zlib1g-dev
```

---

### Post by fiscoking on 2021-04-05
I googled '[COLOR=#0000FF]Repair broken packages[/COLOR]' and found an article that recommends the following commands, but none of them work. All produce errors.:

([http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/](http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/))

sudo apt-get update –fix-missing

sudo dpkg –configure -a

sudo apt-get install -f

[COLOR=#ff0000]@TheFu[/COLOR]

xxx@xxx-Latitude-5400:~$ sudo apt install --reinstall zlib1g-dev
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 zlib1g-dev : Depends: zlib1g (= 1:1.2.11.dfsg-2ubuntu1) but 1:1.2.11.dfsg-2ubuntu1.2 is to be installed
              Depends: libc6-dev but it is not going to be installed or
                       libc-dev
E: Unable to correct problems, you have held broken packages.

Thanks.

---

### Post by tea for one on 2021-04-05
> **fiscoking said:**
> I googled '[COLOR=#0000FF]Repair broken packages[/COLOR]' and found an article that recommends the following commands, but none of them work. All produce errors.:

([http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/](http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/))

sudo apt-get update –fix-missing

sudo dpkg –configure -a

sudo apt-get install -f


You stated that all the commands produce errors but you have not included the errors in your reply?

Have you added any software from outside the official repositories?
e.g. ppa packages, other deb files or zipped files etc?

---

### Post by TheFu on 2021-04-05
This is when I'd turn to **aptitude** to resolve dependency issues. It provides options that we can reject, until it presents a solution we like.  Once it took until the 12th set of options before one I liked was offered.

---

### Post by deadflowr on 2021-04-05
You have the focal and security repositories, but I do not see the focal-updates repository.
See [https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab]("https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab")
to enable it.

---

### Post by fiscoking on 2021-04-06
> **tea for one said:**
> You stated that all the commands produce errors but you have not included the errors in your reply?

Have you added any software from outside the official repositories?
e.g. ppa packages, other deb files or zipped files etc?

No new software. This is a brand new Ubuntu installation with default options. I built the laptop a few days ago.

Command output is shown below:

 ```
xxx@xxx-Latitude-5400:~$ sudo apt-get update –fix-missing
 [sudo] password for xxx:  
 E: The update command takes no arguments
 xxx@xxx-Latitude-5400:~$ sudo dpkg –configure -a
 dpkg: error: need an action option
 
 
 Type dpkg --help for help about installing and uninstalling packages 
[*];
 Use 'apt' or 'aptitude' for user-friendly package management;
 Type dpkg -Dhelp for a list of dpkg debug flag values;
 Type dpkg --force-help for a list of forcing options;
 Type dpkg-deb --help for help about manipulating *.deb files;
 
 
 Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
 xxx@xxx-Latitude-5400:~$ sudo apt-get install -f
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 0 to upgrade, 0 to newly install, 0 to remove and 8 not to upgrade.
 xxx@xxx-Latitude-5400:~$
```

[QUOTE=deadflowr]You have the focal and security repositories, but I do not see the focal-updates repository.
See [https://help.ubuntu.com/community/Re...tu#Updates_Tab]("https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab")
to enable it.[/QUOTE]

Not sure what focal-updates means. The link you've kindly provided has nothing about an 'focal-updates repository' in it. Also, my updates tab does not have the three check boxes on it as shown in the example....so I; 

* Selected 'security and recommended updates' from the drop down list on the updates tab (changed from security only). 
* Selected 'Canonical Partners' on the Other Software tab.
* Selected 'Propietary Drivers' on the 'Ubuntu Software tab.

I then ran the commands (that didn't error) again and it appears to have worked. I now have a working installed copy of 'System Profiler' (hardinfo). Looking at the output below, it appears that the 'update' and 'upgrade' commands did something.
[COLOR=#ff0000]
Am I correct in thinking that 'sudo apt update' and 'sudo apt full-upgrade' only apply bug fix updates to applications and the kernel, and do not upgrade to the next software version number (which would add functionality to apps and the OS)? A bit like applying a security or bug patch in windows?[/COLOR]

Many Thanks.


 ```
xxx@xxx-Latitude-5400:~$ sudo apt update

 [sudo] password for xxx:  
 Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease
 Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal InRelease                       
 Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]      
 Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [109 kB]       
 Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
 Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [265 kB]
 Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main i386 Packages [210 kB]
 Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [303 kB]
 Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/universe DEP-11 48x48 Icons [200 kB]
 Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages [575 kB]
 Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [24.3 kB]
 Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [58.2 kB]
 Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 c-n-f Metadata [10.7 kB]
 Fetched 1,871 kB in 1s (2,341 kB/s)                              
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 8 packages can be upgraded. Run 'apt list --upgradable' to see them.
 
xxx@xxx-Latitude-5400:~$ sudo apt full-upgrade

 Reading package lists... Done

 Building dependency tree        
 Reading state information... Done
 Calculating upgrade... Done
 The following packages will be upgraded:
   libnss-systemd libpam-systemd libsystemd0 systemd systemd-sysv
   systemd-timesyncd update-notifier update-notifier-common
 8 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
 Need to get 4,586 kB of archives.
 After this operation, 9,216 B of additional disk space will be used.
 Do you want to continue? [Y/n] y
 Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 libnss-systemd amd64 245.4-4ubuntu3.5 [95.8 kB]
 Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 systemd-timesyncd amd64 245.4-4ubuntu3.5 [28.1 kB]
 Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 systemd-sysv amd64 245.4-4ubuntu3.5 [10.3 kB]
 Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 libpam-systemd amd64 245.4-4ubuntu3.5 [186 kB]
 Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 systemd amd64 245.4-4ubuntu3.5 [3,805 kB]
 Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 libsystemd0 amd64 245.4-4ubuntu3.5 [274 kB]
 Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 update-notifier amd64 3.192.30.6 [56.6 kB]
 Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 update-notifier-common all 3.192.30.6 [131 kB]
 Fetched 4,586 kB in 1s (4,255 kB/s)              
 (Reading database ... 186222 files and directories currently installed.)
 Preparing to unpack .../0-libnss-systemd_245.4-4ubuntu3.5_amd64.deb ...
 Unpacking libnss-systemd:amd64 (245.4-4ubuntu3.5) over (245.4-4ubuntu3.4) ...
 Preparing to unpack .../1-systemd-timesyncd_245.4-4ubuntu3.5_amd64.deb ...
 Unpacking systemd-timesyncd (245.4-4ubuntu3.5) over (245.4-4ubuntu3.4) ...
 Preparing to unpack .../2-systemd-sysv_245.4-4ubuntu3.5_amd64.deb ...
 Unpacking systemd-sysv (245.4-4ubuntu3.5) over (245.4-4ubuntu3.4) ...
 Preparing to unpack .../3-libpam-systemd_245.4-4ubuntu3.5_amd64.deb ...
 Unpacking libpam-systemd:amd64 (245.4-4ubuntu3.5) over (245.4-4ubuntu3.4) ...
 Preparing to unpack .../4-systemd_245.4-4ubuntu3.5_amd64.deb ...
 Unpacking systemd (245.4-4ubuntu3.5) over (245.4-4ubuntu3.4) ...
 Preparing to unpack .../5-libsystemd0_245.4-4ubuntu3.5_amd64.deb ...
 Unpacking libsystemd0:amd64 (245.4-4ubuntu3.5) over (245.4-4ubuntu3.4) ...
 Setting up libsystemd0:amd64 (245.4-4ubuntu3.5) ...
 (Reading database ... 186222 files and directories currently installed.)
 Preparing to unpack .../update-notifier_3.192.30.6_amd64.deb ...
 Unpacking update-notifier (3.192.30.6) over (3.192.30.5) ...
 Preparing to unpack .../update-notifier-common_3.192.30.6_all.deb ...
 Unpacking update-notifier-common (3.192.30.6) over (3.192.30.5) ...
 Setting up update-notifier-common (3.192.30.6) ...
 Setting up update-notifier (3.192.30.6) ...
 Setting up systemd (245.4-4ubuntu3.5) ...
 Setting up systemd-timesyncd (245.4-4ubuntu3.5) ...
 Setting up systemd-sysv (245.4-4ubuntu3.5) ...
 Setting up libnss-systemd:amd64 (245.4-4ubuntu3.5) ...
 Setting up libpam-systemd:amd64 (245.4-4ubuntu3.5) ...
 Processing triggers for hicolor-icon-theme (0.17-2) ...
 Processing triggers for libglib2.0-0:amd64 (2.64.6-1~ubuntu20.04.3) ...
 Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
 Processing triggers for man-db (2.9.1-1) ...
 Processing triggers for dbus (1.12.16-2ubuntu2.1) ...
 
xxx@xxx-Latitude-5400:~$ sudo ubuntu-drivers autoinstall

 No drivers found for installation.
 
xxx@xxx-Latitude-5400:~$ sudo apt-get install hardinfo

 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 The following additional packages will be installed:
   libc-dev-bin libc6-dev libcrypt-dev linux-libc-dev lm-sensors manpages-dev
   zlib1g-dev
 Suggested packages:

   mesa-utils glibc-doc fancontrol read-edid i2c-tools
 The following NEW packages will be installed
   hardinfo libc-dev-bin libc6-dev libcrypt-dev linux-libc-dev lm-sensors
   manpages-dev zlib1g-dev
 0 to upgrade, 8 to newly install, 0 to remove and 0 not to upgrade.
 Need to get 6,643 kB of archives.
 After this operation, 32.2 MB of additional disk space will be used.
 Do you want to continue? [Y/n] y
 Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 libc-dev-bin amd64 2.31-0ubuntu9.2 [71.8 kB]

 Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 linux-libc-dev amd64 5.4.0-70.78 [1,120 kB]
 Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal/main amd64 libcrypt-dev amd64 1:4.4.10-10ubuntu4 [104 kB]
 Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 libc6-dev amd64 2.31-0ubuntu9.2 [2,520 kB]
 Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 zlib1g-dev amd64 1:1.2.11.dfsg-2ubuntu1.2 [155 kB]
 Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal/universe amd64 hardinfo amd64 0.5.1+git20180227-2 [319 kB]
 Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal/main amd64 manpages-dev all 5.05-1 [2,266 kB]
 Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal/universe amd64 lm-sensors amd64 1:3.6.0-2ubuntu1 [87.4 kB]
 Fetched 6,643 kB in 2s (4,199 kB/s)   
 Selecting previously unselected package libc-dev-bin.
 (Reading database ... 186222 files and directories currently installed.)
 Preparing to unpack .../0-libc-dev-bin_2.31-0ubuntu9.2_amd64.deb ...
 Unpacking libc-dev-bin (2.31-0ubuntu9.2) ...
 Selecting previously unselected package linux-libc-dev:amd64.
 Preparing to unpack .../1-linux-libc-dev_5.4.0-70.78_amd64.deb ...
 Unpacking linux-libc-dev:amd64 (5.4.0-70.78) ...
 Selecting previously unselected package libcrypt-dev:amd64.
 Preparing to unpack .../2-libcrypt-dev_1%3a4.4.10-10ubuntu4_amd64.deb ...
 Unpacking libcrypt-dev:amd64 (1:4.4.10-10ubuntu4) ...
 Selecting previously unselected package libc6-dev:amd64.
 Preparing to unpack .../3-libc6-dev_2.31-0ubuntu9.2_amd64.deb ...
 Unpacking libc6-dev:amd64 (2.31-0ubuntu9.2) ...
 Selecting previously unselected package zlib1g-dev:amd64.
 Preparing to unpack .../4-zlib1g-dev_1%3a1.2.11.dfsg-2ubuntu1.2_amd64.deb ...
 Unpacking zlib1g-dev:amd64 (1:1.2.11.dfsg-2ubuntu1.2) ...
 Selecting previously unselected package hardinfo.
 Preparing to unpack .../5-hardinfo_0.5.1+git20180227-2_amd64.deb ...
 Unpacking hardinfo (0.5.1+git20180227-2) ...
 Selecting previously unselected package manpages-dev.
 Preparing to unpack .../6-manpages-dev_5.05-1_all.deb ...
 Unpacking manpages-dev (5.05-1) ...
 Selecting previously unselected package lm-sensors.
 Preparing to unpack .../7-lm-sensors_1%3a3.6.0-2ubuntu1_amd64.deb ...
 Unpacking lm-sensors (1:3.6.0-2ubuntu1) ...
 Setting up manpages-dev (5.05-1) ...
 Setting up linux-libc-dev:amd64 (5.4.0-70.78) ...
 Setting up lm-sensors (1:3.6.0-2ubuntu1) ...
 Created symlink /etc/systemd/system/multi-user.target.wants/lm-sensors.service &#8594; /lib/systemd/system/lm-sensors.service.
 Setting up libcrypt-dev:amd64 (1:4.4.10-10ubuntu4) ...
 Setting up libc-dev-bin (2.31-0ubuntu9.2) ...
 Setting up libc6-dev:amd64 (2.31-0ubuntu9.2) ...
 Setting up zlib1g-dev:amd64 (1:1.2.11.dfsg-2ubuntu1.2) ...
 Setting up hardinfo (0.5.1+git20180227-2) ...
 Processing triggers for man-db (2.9.1-1) ...
 Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
 Processing triggers for mime-support (3.64ubuntu1) ...
 Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
 Processing triggers for systemd (245.4-4ubuntu3.5) ...
 xxx@xxx-Latitude-5400:~$
```

---

### Post by tea for one on 2021-04-06
The website [http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/](http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/) where you found this terminal command 
```
sudo apt-get update –fix-missing[COLOR="#FF0000"] Produces an error[/COLOR]
```

```
sudo apt-get update --fix-missing [COLOR="#0000FF"]Try this[/COLOR]

```

Generally, if you find a terminal command which does not perform as expected, it is worth spending a bit of time to try and verify the command with other websites.

Anyway, you now have your desired package installed and it would be helpful to other users to mark the thread as solved.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by deadflowr on 2021-04-06
> Not sure what focal-updates means. The link you've kindly provided has nothing about an 'focal-updates repository' in it.
The link was to provide an overview of the update system and how to enable the various bits.

All updated software is in the updates repository. but only security updates are in both the security repository and the updates repository.
The packages you needed were updated, so the updated versions were in the -updates repository.
(But they were not security updates so they were never in the security repository.)

Hope that make more sense.

---

### Post by fiscoking on 2021-04-07
Marked as solved.

Thanks for your help.

---

### Post by gromovd on 2021-05-11
Maybe this is marked as resolved, but there is no real solution here.
I have exactly same issue - trying to install hardinfo in kbuntu 20.04 currently fails with error:
```
hardinfo : Depends: zlib1g-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
Looking at dependencies, I see that zlib1g-dev depends on libc6-dev which, in turn, depends on libc6 - and there is a conflict:
```
libc6-dev : Depends: libc6 (= 2.31-0ubuntu9.2) but 2.31-0ubuntu9.3 is to be installed
```
Basically, system has newer version of libc6 installed and libc6-dev won't install because it depends on previous version...

You can't really remove libc6, maybe there is a way to downgrade it, but the real issue is in libc6-dev broken dependency in 20.04 Ubuntu :(

---

### Post by deadflowr on 2021-05-11
> **gromovd said:**
> Maybe this is marked as resolved, but there is no real solution here.
I have exactly same issue - trying to install hardinfo in kbuntu 20.04 currently fails with error:
```
hardinfo : Depends: zlib1g-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
Looking at dependencies, I see that zlib1g-dev depends on libc6-dev which, in turn, depends on libc6 - and there is a conflict:
```
libc6-dev : Depends: libc6 (= 2.31-0ubuntu9.2) but 2.31-0ubuntu9.3 is to be installed
```
Basically, system has newer version of libc6 installed and libc6-dev won't install because it depends on previous version...

You can't really remove libc6, maybe there is a way to downgrade it, but the real issue is in libc6-dev broken dependency in 20.04 Ubuntu :(

The solution is the OP enabled the focal-updates repository, which had the proper packages.

---

