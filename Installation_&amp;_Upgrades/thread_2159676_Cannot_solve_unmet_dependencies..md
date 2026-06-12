---
title: "Cannot solve unmet dependencies."
date: 2013-07-04
forum: Installation &amp; Upgrades
---

### Post by kbslater on 2013-07-04
I have searched for an answer to my problem for several hours. Through both search engines as well as on this forum but cannot seem to find a solution.

I am trying to install 'git' but receive the following error when attempting the install.
```

~$ git clone git://github.com/citrus/iStat-Server-Installer.git
The program 'git' is currently not installed.  You can install it by typing:
sudo apt-get install git

```

So I try the install.
```

~$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 git : Depends: liberror-perl but it is not going to be installed
       Depends: git-man (> 1:1.7.9.5) but it is not going to be installed
       Depends: git-man (< 1:1.7.9.5-.) but it is not going to be installed
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.41.49) but 3.2.0.48.58 is to be installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-41-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

That fails, so lets try the suggestion from the installer.
```

~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic-pae linux-image-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-image-generic-pae
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4,084 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-41-generic-pae; however:
  Package linux-image-3.2.0-41-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.41.49); however:
  Package linux-image-generic-pae is not configured yet.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.41.49); however:
  Version of linux-headers-generic-pae on system is 3.2.0.48.58.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The same error is consistant  in reporting the following error.
```
Package linux-image-3.2.0-41-generic-pae is not installed.
```

So I also tried to install the package itself, this might not have been the correct thing to do but I was grasping at straws!
```
~$ sudo apt-get install linux-image-3.2.0-41-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.41.49) but 3.2.0.48.58 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

So I try to install linux headers.
```

$ sudo apt-get install linux-headers-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic-pae is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.41.49) but 3.2.0.48.58 is to be installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-41-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Here I tried 'apt-get update'
```

~$ sudo apt-get update
Hit http://archive.canonical.com precise Release.gpg
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://archive.canonical.com precise Release                           
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]
Hit http://archive.canonical.com precise/partner Sources                        
Hit http://archive.canonical.com precise/partner i386 Packages
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:3 http://security.ubuntu.com precise-security/main Sources [83.2 kB]       
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:4 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com precise Release                               
Get:5 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]                                  
Get:6 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]                       
Get:7 http://security.ubuntu.com precise-security/universe Sources [26.3 kB]             
Get:8 http://security.ubuntu.com precise-security/multiverse Sources [1,383 B]           
Get:9 http://security.ubuntu.com precise-security/main i386 Packages [310 kB]                        
Hit http://us.archive.ubuntu.com precise/main Sources                                                         
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:10 http://us.archive.ubuntu.com precise-updates/main Sources [400 kB]     
Ign http://archive.canonical.com precise/partner Translation-en_US                     
Get:11 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]  
Get:12 http://security.ubuntu.com precise-security/universe i386 Packages [79.8 kB]                         
Get:13 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,367 B]                       
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                       
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:14 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]
Get:15 http://us.archive.ubuntu.com precise-updates/universe Sources [91.3 kB]
Get:16 http://us.archive.ubuntu.com precise-updates/multiverse Sources [6,571 B]
Get:17 http://us.archive.ubuntu.com precise-updates/main i386 Packages [664 kB]
Hit http://security.ubuntu.com precise-security/universe Translation-en           
Get:18 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]
Get:19 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [211 kB]
Get:20 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Fetched 2,012 kB in 3s (586 kB/s)                
Reading package lists... Done

```

Now I'll  try 'apt-get upgrade'
```

~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.41.49) but 3.2.0.48.58 is installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-41-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

```

Now I'll try it with '-f'
```

~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be upgraded:
  linux-generic-pae linux-image-generic-pae
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4,084 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-41-generic-pae; however:
  Package linux-image-3.2.0-41-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.41.49); however:
  Package linux-image-generic-pae is not configured yet.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.41.49); however:
  Version of linux-headers-generic-pae on system is 3.2.0.48.58.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Seems to have come full circle.  Here is some more information if it might help diagnose my problem.

```
~$ uname -r
3.2.0-48-generic-pae

~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/enderhouse-root  915G  2.4G  866G   1% /
udev                         1.8G  4.0K  1.8G   1% /dev
tmpfs                        706M  508K  706M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.8G     0  1.8G   0% /run/shm
/dev/sdb1                    230G  4.5G  214G   3% /storage
/dev/sda1                    228M   93M  124M  43% /boot

~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

```

Any and all help is greatly appreciated.

Thanks,
Kevin

---

### Post by MikeCyber on 2013-07-04
I had something similar, but simply updating with the update manager solved it.

---

### Post by kbslater on 2013-07-04
Mike thanks for the quick response but looks like I failed to mention that this is a server.
  
Here is the same response when trying to do a dist-upgrage.
```
~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.41.49) but 3.2.0.48.58 is installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-41-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
```

Using the '-f' option results in similar output.
```
~$ sudo apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-generic-pae linux-image-generic-pae
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4,084 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-41-generic-pae; however:
  Package linux-image-3.2.0-41-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.41.49); however:
  Package linux-image-generic-pae is not configured yet.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.41.49); however:
  Version of linux-headers-generic-pae on system is 3.2.0.48.58.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks again for your quick response.

Kevin

---

### Post by grahammechanical on 2013-07-04
I am no expert but this is how I see things. You are trying to install a package that needs Linux kernel 3.2.0.41.49. What is wrong with that? You are using Ubuntu 12.04.2. Ubuntu LTS versions get four point releases in 2 years that bring in updated code to run on newer hardware. Ubuntu 12.04.2 installs with the Linux kernel 3.5.0 series. In trying to install a Linux 3.2.0 series kernel you are taking the OS backwards and apt-get is not going to let you do that. Too many other packages are connected to kernel 3.5.0.

I may be wrong but I do know that 12.04.2 has the 3.5.0 kernel. I tested it before 12.04.2 was released.

UPDATE:  I have just installed git. and this is what I got.

> graham@sda9-X-saucy-btrfs:~$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run git-daemon-sysvinit git-doc git-el git-email git-gui gitk gitweb git-arch git-bzr git-cvs git-svn
The following NEW packages will be installed
  git git-man liberror-perl
0 upgraded, 3 newly installed, 0 to remove and 22 not upgraded.
Need to get 8,729 kB of archives.
After this operation, 19.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy/main liberror-perl all 0.17-1 [23.8 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy/main git-man all 1:1.8.3.2-1 [670 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy/main git amd64 1:1.8.3.2-1 [8,035 kB]
Fetched 8,729 kB in 6s (1,251 kB/s)                                                                                                                                                                           
Selecting previously unselected package liberror-perl.
(Reading database ... 165392 files and directories currently installed.)
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously unselected package git-man.
Unpacking git-man (from .../git-man_1%3a1.8.3.2-1_all.deb) ...
Selecting previously unselected package git.
Unpacking git (from .../git_1%3a1.8.3.2-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up liberror-perl (0.17-1) ...
Setting up git-man (1:1.8.3.2-1) ...
Setting up git (1:1.8.3.2-1) ...

I am using Saucy Salamamder Xubuntu and it has a much newer kernel - 3.10-.0. And I had no problems.

Some on in an other post had an update issue and the Update Manager was recommending

```
sudo apt-get install -f
```

you were advised tor un

```
sudo apt-get -f install
```

which is correct?

Regards.

---

### Post by Cheesehead on 2013-07-04
> **kbslater said:**
> 
```

~$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 git : Depends: liberror-perl but it is not going to be installed
       Depends: git-man (> 1:1.7.9.5) but it is not going to be installed
       Depends: git-man (< 1:1.7.9.5-.) but it is not going to be installed
 linux-generic-pae : Depends: [COLOR="#FF0000"]linux-headers-generic-pae (= 3.2.0.41.49)[/COLOR] but [COLOR="#FF0000"]3.2.0.48.58[/COLOR] is to be installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-41-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


There are two possibilities.
Either you have a PPA installed that requires a specific kernel version, or your system is not updated.

```
$ rmadison linux-headers-generic-pae
linux-headers-generic-pae is currently in the Ubuntu repositories
linux-headers-generic-pae | 2.6.32.21.22 |         lucid | i386
linux-headers-generic-pae | 2.6.32.49.56 | lucid-security | i386
linux-headers-generic-pae | 2.6.32.49.56 | lucid-proposed | i386
linux-headers-generic-pae | 2.6.32.49.56 | lucid-updates | i386
linux-headers-generic-pae | 3.2.0.23.25 |       precise | i386
linux-headers-generic-pae | [COLOR="#FF0000"]3.2.0.48.58[/COLOR] | precise-security | i386
linux-headers-generic-pae | 3.2.0.49.59 | precise-proposed | i386
linux-headers-generic-pae | 3.2.0.49.59 | precise-updates | i386
linux-headers-generic-pae | 3.5.0.17.19 |       quantal | i386
linux-headers-generic-pae | 3.5.0.34.50 | quantal-security | i386
linux-headers-generic-pae | 3.5.0.36.52 | quantal-proposed | i386
linux-headers-generic-pae | 3.5.0.36.52 | quantal-updates | i386
linux-headers-generic-pae | 3.8.0.19.35 |        raring | i386
linux-headers-generic-pae | 3.8.0.23.39 | raring-security | i386
linux-headers-generic-pae | 3.8.0.26.44 | raring-proposed | i386
linux-headers-generic-pae | 3.8.0.26.44 | raring-updates | i386
linux-headers-generic-pae | 3.10.0.2.11 |         saucy | i386

```

See how the kernel you have is not on the list, but the kernel that cannot be installed is on the list?
Your system cannot properly update, and that is usually due to a PPA dependency.
If you do have PPAs installed, look at those dependencies, and uninstall the one that requires that particular kernel version.

---

