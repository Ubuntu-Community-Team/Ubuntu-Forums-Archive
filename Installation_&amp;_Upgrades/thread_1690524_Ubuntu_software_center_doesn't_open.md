---
title: "Ubuntu software center doesn't open"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by Lacturu on 2011-02-18
Hi!

When I try to open Ubuntu software center, it appears on the process bar for about 10 seconds before it disappears. I can't get it to start.

I have tried alt+f2 and typing 'software-center', didn't help. I tried reinstalling ubuntu software center in Synoptic package manager, but I got this error message: "E: /var/cache/apt/archives/software-center_3.0.7_all.deb: subprocess new pre-removal script returned error exit status 1"

This started to happen after I reinstalled Ubuntu 10.10. After I did that, I got the 'modprobe: FATAL: Could not load /lib/modules/2.6.8.custem/modules.deb, no such
file or directory.' error. Could these two problems be related in any way?

Thanks :P

---

### Post by sikander3786 on 2011-02-18
Welcome to the forums :-)

From Applications > Accessories > Terminal, please post the complete output of these commands.

```
sudo apt-get update
```

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readibility purposes.

---

### Post by Lacturu on 2011-02-18
Thanks for the quick reply :)

For sudo apt-get update:
```
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en   
Hit http://security.ubuntu.com maverick-security Release.gpg        
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_DK
Hit http://extras.ubuntu.com maverick Release                       
Hit http://dk.archive.ubuntu.com maverick Release.gpg
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_DK
Hit http://dk.archive.ubuntu.com maverick-updates Release.gpg
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Hit http://extras.ubuntu.com maverick/main Sources                   
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_DK
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_DK
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_DK
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_DK
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_DK
Hit http://security.ubuntu.com maverick-security Release
Hit http://dk.archive.ubuntu.com maverick Release                    
Hit http://dk.archive.ubuntu.com maverick-updates Release            
Hit http://extras.ubuntu.com maverick/main amd64 Packages            
Hit http://security.ubuntu.com maverick-security/main Sources        
Hit http://dk.archive.ubuntu.com maverick/main Sources
Hit http://dk.archive.ubuntu.com maverick/restricted Sources
Hit http://dk.archive.ubuntu.com maverick/universe Sources
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://dk.archive.ubuntu.com maverick/multiverse Sources
Hit http://dk.archive.ubuntu.com maverick/main amd64 Packages
Hit http://dk.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://dk.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://dk.archive.ubuntu.com maverick/multiverse amd64 Packages
Hit http://dk.archive.ubuntu.com maverick-updates/main Sources
Hit http://dk.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://dk.archive.ubuntu.com maverick-updates/universe Sources
Hit http://dk.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://dk.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://dk.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://dk.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://dk.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main amd64 Packages
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages
Reading package lists... Done
nermin@nermin-EasyNote-TJ62:~$ ^C
nermin@nermin-EasyNote-TJ62:~$ clear

nermin@nermin-EasyNote-TJ62:~$ sudo apt-get update
Hit http://dk.archive.ubuntu.com maverick Release.gpg
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_DK       
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_DK
Hit http://dk.archive.ubuntu.com maverick-updates Release.gpg        
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_DK
Hit http://extras.ubuntu.com maverick Release.gpg                    
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en    
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_DK
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_DK
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_DK
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_DK
Hit http://security.ubuntu.com maverick-security Release
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_DK
Hit http://dk.archive.ubuntu.com maverick Release
Hit http://dk.archive.ubuntu.com maverick-updates Release
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://dk.archive.ubuntu.com maverick/main Sources               
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources  
Hit http://dk.archive.ubuntu.com maverick/restricted Sources         
Hit http://dk.archive.ubuntu.com maverick/universe Sources           
Hit http://dk.archive.ubuntu.com maverick/multiverse Sources         
Hit http://dk.archive.ubuntu.com maverick/main amd64 Packages        
Hit http://dk.archive.ubuntu.com maverick/restricted amd64 Packages  
Hit http://dk.archive.ubuntu.com maverick/universe amd64 Packages    
Hit http://dk.archive.ubuntu.com maverick/multiverse amd64 Packages  
Hit http://dk.archive.ubuntu.com maverick-updates/main Sources       
Hit http://dk.archive.ubuntu.com maverick-updates/restricted Sources 
Hit http://dk.archive.ubuntu.com maverick-updates/universe Sources   
Hit http://security.ubuntu.com maverick-security/main amd64 Packages 
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages
Hit http://dk.archive.ubuntu.com maverick-updates/multiverse Sources 
Hit http://dk.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://dk.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://dk.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://dk.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_DK
Hit http://extras.ubuntu.com maverick Release
Hit http://extras.ubuntu.com maverick/main Sources
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Reading package lists... Done
nermin@nermin-EasyNote-TJ62:~$ 

```For sudo dpkg --configure -a:
```
nermin@nermin-EasyNote-TJ62:~$ sudo dpkg --configure -a
dpkg: error processing software-center (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 software-center
nermin@nermin-EasyNote-TJ62:~$ 

```For sudo apt-get install -f:
```
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/434kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 
dpkg: warning: files list file for package `pptp-linux' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgee2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam-ck-connector' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libntfs-3g79' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pppoeconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-cupshelpers' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liborc-0.4-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdu0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `os-prober' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpanel-applet2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-libc-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `software-center' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssh-askpass-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `procps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openprinting-ppds' missing, assuming package has no files currently installed.
(Reading database ... 148296 files and directories currently installed.)
Preparing to replace software-center 3.0.7 (using .../software-center_3.0.7_all.deb) ...
pycentral: pycentral pkgremove: package software-center is not installed
pycentral pkgremove: package software-center is not installed
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package software-center is not installed
pycentral pkgremove: package software-center is not installed
dpkg: error processing /var/cache/apt/archives/software-center_3.0.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package software-center is not installed
pycentral pkginstall: package software-center is not installed
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_3.0.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
nermin@nermin-EasyNote-TJ62:~$ 

```

---

### Post by sikander3786 on 2011-02-18
Try,

```
sudo apt-get install --reinstall software-center
```

Keep posting the outputs ;-)

---

### Post by lisati on 2011-02-18
I might suggest the following:
```
sudo aptitude clean && sudo aptitude reinstall software-center
```
The first part will clean out the "apt cache", forcing the second part to redownload the necessaries.

---

### Post by Lacturu on 2011-02-18
For sudo apt-get install --reinstall software-center:
```
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get install --reinstall software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/434kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 
dpkg: warning: files list file for package `pptp-linux' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgee2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam-ck-connector' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libntfs-3g79' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pppoeconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-cupshelpers' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liborc-0.4-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdu0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `os-prober' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpanel-applet2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-libc-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `software-center' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssh-askpass-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `procps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openprinting-ppds' missing, assuming package has no files currently installed.
(Reading database ... 148296 files and directories currently installed.)
Preparing to replace software-center 3.0.7 (using .../software-center_3.0.7_all.deb) ...
pycentral: pycentral pkgremove: package software-center is not installed
pycentral pkgremove: package software-center is not installed
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package software-center is not installed
pycentral pkgremove: package software-center is not installed
dpkg: error processing /var/cache/apt/archives/software-center_3.0.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package software-center is not installed
pycentral pkginstall: package software-center is not installed
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_3.0.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
nermin@nermin-EasyNote-TJ62:~$ 

```Didn't work :(.

sudo aptitude clean && sudo aptitude reinstall software-center didn't work, because it can't find the command 'aptitude'

---

### Post by sikander3786 on 2011-02-18
> **lisati said:**
> I might suggest the following:
```
sudo aptitude clean && sudo aptitude reinstall software-center
```
The first part will clean out the "apt cache", forcing the second part to redownload the necessaries.
+1 for cache cleaning but i think aptitude is not installed by default in Maverick so,

```
sudo apt-get clean && sudo apt-get install --reinstall software-center
```

---

### Post by Lacturu on 2011-02-18
For the code you posted (The long one, but without the aptitude command):
```
nermin@nermin-EasyNote-TJ62:~$ sudo aptitude clean && sudo aptitude reinstall software-center
sudo: aptitude: command not found
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get clean && sudo apt-get install --reinstall software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 434kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/main software-center all 3.0.7 [434kB]
Fetched 434kB in 1s (322kB/s)          
(Reading database ... 
dpkg: warning: files list file for package `pptp-linux' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgee2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam-ck-connector' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libntfs-3g79' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pppoeconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-cupshelpers' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liborc-0.4-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdu0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `os-prober' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpanel-applet2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-libc-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `software-center' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssh-askpass-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `procps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openprinting-ppds' missing, assuming package has no files currently installed.
(Reading database ... 148296 files and directories currently installed.)
Preparing to replace software-center 3.0.7 (using .../software-center_3.0.7_all.deb) ...
pycentral: pycentral pkgremove: package software-center is not installed
pycentral pkgremove: package software-center is not installed
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package software-center is not installed
pycentral pkgremove: package software-center is not installed
dpkg: error processing /var/cache/apt/archives/software-center_3.0.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package software-center is not installed
pycentral pkginstall: package software-center is not installed
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_3.0.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
nermin@nermin-EasyNote-TJ62:~$ 

```

Isn't it just the same errors?

---

### Post by lisati on 2011-02-18
> **sikander3786 said:**
> +1 for cache cleaning but i think aptitude is not installed by default in Maverick so,

```
sudo apt-get clean && sudo apt-get install --reinstall software-center
```

Thanks for that. I'm still on Lucid here.

---

### Post by sikander3786 on 2011-02-18
Try using an older dpkg status file.

Backup your existing one.

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

Use the older one.

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Then one-by-one,

```
sudo apt-get clean
sudo apt-get autoclean
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get install --reinstall software-center
```

It takes some time to sort out an issue like this so we need you to be patient :-)

---

### Post by Lacturu on 2011-02-18
For all the codes you posted (without the one where you removed the aptitude command):
```
nermin@nermin-EasyNote-TJ62:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
nermin@nermin-EasyNote-TJ62:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get clean
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nermin@nermin-EasyNote-TJ62:~$ sudo dpkg --configure -a
dpkg: error processing software-center (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 software-center
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 434kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/main software-center all 3.0.7 [434kB]
Fetched 434kB in 1s (228kB/s)          
(Reading database ... 
dpkg: warning: files list file for package `pptp-linux' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgee2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam-ck-connector' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libntfs-3g79' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pppoeconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-cupshelpers' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liborc-0.4-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdu0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `os-prober' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpanel-applet2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-libc-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `software-center' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssh-askpass-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `procps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openprinting-ppds' missing, assuming package has no files currently installed.
(Reading database ... 148296 files and directories currently installed.)
Preparing to replace software-center 3.0.7 (using .../software-center_3.0.7_all.deb) ...
pycentral: pycentral pkgremove: package software-center is not installed
pycentral pkgremove: package software-center is not installed
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package software-center is not installed
pycentral pkgremove: package software-center is not installed
dpkg: error processing /var/cache/apt/archives/software-center_3.0.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package software-center is not installed
pycentral pkginstall: package software-center is not installed
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_3.0.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get install --reinstall software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/434kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 
dpkg: warning: files list file for package `pptp-linux' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgee2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam-ck-connector' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libntfs-3g79' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pppoeconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-cupshelpers' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liborc-0.4-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdu0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `os-prober' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpanel-applet2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-libc-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `software-center' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssh-askpass-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `procps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openprinting-ppds' missing, assuming package has no files currently installed.
(Reading database ... 148296 files and directories currently installed.)
Preparing to replace software-center 3.0.7 (using .../software-center_3.0.7_all.deb) ...
pycentral: pycentral pkgremove: package software-center is not installed
pycentral pkgremove: package software-center is not installed
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package software-center is not installed
pycentral pkgremove: package software-center is not installed
dpkg: error processing /var/cache/apt/archives/software-center_3.0.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package software-center is not installed
pycentral pkginstall: package software-center is not installed
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_3.0.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
nermin@nermin-EasyNote-TJ62:~$ 

```

It still doesn't seem to work.

---

### Post by sikander3786 on 2011-02-18
Try manually deleting the .deb file and try installation again.

```
sudo rm /var/cache/apt/archives/software-center_3.0.7_all.deb
sudo apt-get remove --purge software-center
sudo apt-get install software-center
```

---

### Post by Lacturu on 2011-02-18
For the codes you posted:
```
nermin@nermin-EasyNote-TJ62:~$ sudo rm /var/cache/apt/archives/software-center_3.0.7_all.deb
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get remove --purge software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  software-center*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2.036kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing software-center (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 software-center
E: Sub-process /usr/bin/dpkg returned an error code (1)
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
software-center is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 434kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/main software-center all 3.0.7 [434kB]
Fetched 434kB in 0s (470kB/s)          
Selecting previously deselected package software-center.
(Reading database ... 
dpkg: warning: files list file for package `pptp-linux' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgee2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam-ck-connector' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libntfs-3g79' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pppoeconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-cupshelpers' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liborc-0.4-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdu0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `os-prober' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpanel-applet2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-libc-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `software-center' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssh-askpass-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `procps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openprinting-ppds' missing, assuming package has no files currently installed.
(Reading database ... 148296 files and directories currently installed.)
Preparing to replace software-center 3.0.7 (using .../software-center_3.0.7_all.deb) ...
pycentral: pycentral pkgremove: package software-center is not installed
pycentral pkgremove: package software-center is not installed
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package software-center is not installed
pycentral pkgremove: package software-center is not installed
dpkg: error processing /var/cache/apt/archives/software-center_3.0.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package software-center is not installed
pycentral pkginstall: package software-center is not installed
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_3.0.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
nermin@nermin-EasyNote-TJ62:~$ 

```

I was wondering, I keep seeing the last error line (also when I tried to remove and then reinstall Software-center in Synoptic package manager). What does it mean? :)

---

### Post by sikander3786 on 2011-02-18
Which last line were you talking about? The error code one?

Try these for now.

```
sudo rm /var/lib/dpkg/info/software-center.prerm
```

```
sudo dpkg --remove --force-remove-reinstreq software-center
```

I hope these will be successful. Then,

```
sudo apt-get install -f
sudo dpkg --configure -a
```

We'll later install Software Center.

---

### Post by Lacturu on 2011-02-18
Yes, that was the one I was thinking about.

As for the codes:
```
nermin@nermin-EasyNote-TJ62:~$ sudo rm /var/lib/dpkg/info/software-center.prerm
nermin@nermin-EasyNote-TJ62:~$ sudo dpkg --remove --force-remove-reinstreq software-center
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: warning: files list file for package `pptp-linux' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgee2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam-ck-connector' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libntfs-3g79' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pppoeconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-cupshelpers' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liborc-0.4-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdu0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `os-prober' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpanel-applet2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-libc-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `software-center' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssh-askpass-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `procps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openprinting-ppds' missing, assuming package has no files currently installed.
(Reading database ... 148295 files and directories currently installed.)
Removing software-center ...
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nermin@nermin-EasyNote-TJ62:~$ sudo dpkg --configure -a
nermin@nermin-EasyNote-TJ62:~$ 

```

---

### Post by sikander3786 on 2011-02-18
Seems ok for now.

Now try,

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install software-center
```

---

### Post by sikander3786 on 2011-02-18
Regarding your query for the error code, the most informative line in that error is this one.

> Errors were encountered while processing:
 /var/cache/apt/archives/software-center_3.0.7_all.deb


Most of us don't remember error codes and references. And another informative line in your error was

>  Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.


---

### Post by Lacturu on 2011-02-18
Here's the code:
```
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get update && sudo apt-get upgrade
Hit http://dk.archive.ubuntu.com maverick Release.gpg
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_DK
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_DK
Hit http://dk.archive.ubuntu.com maverick-updates Release.gpg
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Hit http://extras.ubuntu.com maverick Release                        
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_DK
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_DK
Hit http://extras.ubuntu.com maverick/main Sources                   
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_DK
Hit http://dk.archive.ubuntu.com maverick Release
Hit http://dk.archive.ubuntu.com maverick-updates Release
Hit http://extras.ubuntu.com maverick/main amd64 Packages                      
Hit http://dk.archive.ubuntu.com maverick/main Sources               
Hit http://dk.archive.ubuntu.com maverick/restricted Sources
Hit http://dk.archive.ubuntu.com maverick/universe Sources
Hit http://security.ubuntu.com maverick-security Release.gpg
Hit http://dk.archive.ubuntu.com maverick/multiverse Sources
Hit http://dk.archive.ubuntu.com maverick/main amd64 Packages
Hit http://dk.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://dk.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://dk.archive.ubuntu.com maverick/multiverse amd64 Packages
Hit http://dk.archive.ubuntu.com maverick-updates/main Sources
Hit http://dk.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://dk.archive.ubuntu.com maverick-updates/universe Sources
Hit http://dk.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://dk.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://dk.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://dk.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://dk.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_DK
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_DK
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_DK
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_DK
Hit http://security.ubuntu.com maverick-security Release
Hit http://security.ubuntu.com maverick-security/main Sources
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main amd64 Packages
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  software-center
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/434kB of archives.
After this operation, 2.036kB of additional disk space will be used.
Selecting previously deselected package software-center.
(Reading database ... 
dpkg: warning: files list file for package `pptp-linux' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgee2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam-ck-connector' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libntfs-3g79' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pppoeconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-cupshelpers' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liborc-0.4-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdu0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `os-prober' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpanel-applet2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-libc-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssh-askpass-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `procps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openprinting-ppds' missing, assuming package has no files currently installed.
(Reading database ... 148296 files and directories currently installed.)
Unpacking software-center (from .../software-center_3.0.7_all.deb) ...
Setting up software-center (3.0.7) ...
Processing triggers for python-central ...
nermin@nermin-EasyNote-TJ62:~$ 

```

---

### Post by sikander3786 on 2011-02-18
There are still a few errors but can you use Software Center now? And what about the output of these commands now.

```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by Lacturu on 2011-02-18
Same old story. Doesn't work, just shows in the progress bar for about 10 seconds.

```
nermin@nermin-EasyNote-TJ62:~$ sudo dpkg --configure -a
nermin@nermin-EasyNote-TJ62:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nermin@nermin-EasyNote-TJ62:~$ 

```

---

### Post by sikander3786 on 2011-02-18
Ok. Revert to your original status file.

```
sudo rm /var/lib/dpkg/status
sudo mv /var/lib/dpkg/status.bad /var/lib/dpkg/status
```

```
sudo apt-get install -f
sudo apt-get install --reinstall software-center
```

I'll have to do some work on those other errors (and those are causing Software Center problem I think). I will post a solution as soon I find one. In the mean time, some other member might jump in and help you on that.

Please hang in there.

---

### Post by Lacturu on 2011-02-18
Alright, and good luck :).

I'm assuming you don't need me to post the code I got from the last codes you gave me.

Don't worry, if you can't find any solution, I'll just go back to Lucix Lynx. It works much better than 10.10 - It doesn't crash at all. 10.10 does :S.

---

