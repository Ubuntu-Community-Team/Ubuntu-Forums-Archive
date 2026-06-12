---
title: "The package system is broken"
date: 2017-04-18
forum: Installation &amp; Upgrades
---

### Post by Gnutron on 2017-04-18
This is a problem I have not been able to resolve.
<The package system is broken -
The following packages have unmet dependencies:
linux-headers-generic-pae: linux-headers-3.2.0-101-generic-pae but it is not installed>
Release 12.04 (precise) 32-bit kernel Linux 3.2.0-101-generic
I have reviewed similar issues of other users but have made no progress.
It would be appreciated for any assistance.

---

### Post by Bashing-om on 2017-04-18
Gnutron; Hello;

Release 12.04 is very close to End_Of_Life and will soon have no more support . Consider a fresh clean install of the current LTS release 16.04.

If it is your desire,however, to fix this present install,- then upgrade - show us what the package manager thinks:
post back - Between code tags- the outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
dpkg -l | grep linux-

```
See here what we need to do.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2017-04-18
It might be useful to know which Linux kernel the system is running on. There can be more than one kernel on the system. They are there as a fall back option. To find out the kernel being used

```
uname -a
```

It might be that the kernel that has unmet dependencies is an older kernel that can be removed. Perhaps you have tried to remove old kernels and not removed all the packages related to that kernel and now you are getting that error.

Regards.

---

### Post by Gnutron on 2017-04-18
Hello Bashing-Om,

I tried to respond but was hit with this message:

              ```
**vBulletin Message**

                                       Your submission could not be processed because a security token was missing.

 If this occurred unexpectedly, please [inform the administrator]("https://ubuntuforums.org/sendmessage.php")  and describe the action you performed before you received this error.  If possible, please include the error page URL plus the date and time  the error occured. 

 Tip : Please shorten long posts by using [https://paste.ubuntu.com/](https://paste.ubuntu.com/) for terminal and log output and link to it in your posts.

             
             Ubuntu Forums
```
               

Security token? Paste bin?

Let me try this again.

```
Linux family 3.2.0-101-generic #141-Ubuntu SMP Thu Mar 10 21:43:55 UTC 2016 i686 i686 i386 GNU/Linux
```

Terminal output for sudo apt-get update

```
Get:27 http://security.ubuntu.com precise-security/universe Translation-en [93.2 kB]
Get:28 http://ca.archive.ubuntu.com precise-updates/multiverse i386 Packages [17.3 kB]
Get:29 http://ca.archive.ubuntu.com precise-updates/main TranslationIndex [208 B]
Get:30 http://ca.archive.ubuntu.com precise-updates/multiverse TranslationIndex [202 B]
Get:31 http://ca.archive.ubuntu.com precise-updates/restricted TranslationIndex [202 B]
Get:32 http://ca.archive.ubuntu.com precise-updates/universe TranslationIndex [205 B]
Hit http://ca.archive.ubuntu.com precise/main Translation-en_CA               
Hit http://ca.archive.ubuntu.com precise/main Translation-en                  
Hit http://ca.archive.ubuntu.com precise/multiverse Translation-en            
Hit http://ca.archive.ubuntu.com precise/restricted Translation-en            
Hit http://ca.archive.ubuntu.com precise/universe Translation-en_CA           
Hit http://ca.archive.ubuntu.com precise/universe Translation-en 
Get:33 http://ca.archive.ubuntu.com precise-updates/main Translation-en [442 kB]
Hit https://private-ppa.launchpad.net precise Release.gpg                     
Hit https://private-ppa.launchpad.net precise Release                         
Hit https://private-ppa.launchpad.net precise/main i386 Packages              
Get:34 https://private-ppa.launchpad.net precise/main TranslationIndex [278 B]
Ign https://private-ppa.launchpad.net precise/main TranslationIndex           
Get:35 http://ca.archive.ubuntu.com precise-updates/multiverse Translation-en [10.1 kB]
Get:36 http://ca.archive.ubuntu.com precise-updates/restricted Translation-en [3,686 B]
Get:37 http://ca.archive.ubuntu.com precise-updates/universe Translation-en [174 kB]
Ign https://private-ppa.launchpad.net precise/main Translation-en_CA          
Ign https://private-ppa.launchpad.net precise/main Translation-en             
Fetched 4,440 kB in 23s (187 kB/s)                                            
W: There is no public key available for the following key IDs:
1397BC53640DB551
W: There is no public key available for the following key IDs:
1397BC53640DB551
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

```
Reading package lists... Done
Building dependency tree      
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-101-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
```

Terminal output for sudo apt-get upgrade

```
Reading package lists... Done
Building dependency tree      
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-101-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
```

Terminal output for dpkg -l | grep linux-

 [https://paste.ubuntu.com/24409458/](https://paste.ubuntu.com/24409458/)

---

### Post by Bashing-om on 2017-04-18
Gnutron; Ho Kay !

We have a target:
> 
Depends: linux-headers-3.2.0-101-generic-pae but it is not installed

Before we directly address getting it installed; make sure we have the operating head room !
show:
```

df -h
df -i

```

once we have a stable system we will address:
> 
no public key available


[INDENT][INDENT]ain't nothhing but a thing
[/INDENT][/INDENT]

---

### Post by Gnutron on 2017-04-18
Terminal output for df -h

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        36G   31G  2.7G  93% /
udev            238M  4.0K  238M   1% /dev
tmpfs            50M  828K   49M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none            248M  156K  248M   1% /run/shm
```

Terminal output for df -i

```
Filesystem      Inodes   IUsed  IFree IUse% Mounted on
/dev/sda1      2351104 2092657 258447   90% /
udev             60859     490  60369    1% /dev
tmpfs            63409     415  62994    1% /run
none             63409       3  63406    1% /run/lock
none             63409       7  63402    1% /run/shm
```

---

### Post by Bashing-om on 2017-04-18
Gnutron; Well ..

You are above a safe threshold on / . but we do have the operating head room .
what now does the package manager relate when we try and install what it wants ?
```

sudo apt-get install linux-headers-3.2.0-101-generic-pae

```

see where
[INDENT][INDENT]we go from here
[/INDENT][/INDENT]

---

### Post by Gnutron on 2017-04-18
Terminal output for df -h

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        36G   31G  2.7G  93% /
udev            238M  4.0K  238M   1% /dev
tmpfs            50M  828K   49M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none            248M  156K  248M   1% /run/shm
```

Terminal output for df -i

```
Filesystem      Inodes   IUsed  IFree IUse% Mounted on
/dev/sda1      2351104 2092657 258447   90% /
udev             60859     490  60369    1% /dev
tmpfs            63409     415  62994    1% /run
none             63409       3  63406    1% /run/lock
none             63409       7  63402    1% /run/shm
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdb4.8++ libunity6 linux-headers-3.2.0-89-generic python-pywapi
  gir1.2-ubuntuoneui-3.0 libconfig8 libqrencode3 libubuntuoneui-3.0-1
  libqt4-gui libdee-1.0-1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-3.2.0-101-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 262 not upgraded.
1 not fully installed or removed.
Need to get 970 kB of archives.
After this operation, 11.4 MB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-101-generic-pae i386 3.2.0-101.141 [970 kB]
Fetched 970 kB in 2s (443 kB/s)                                
(Reading database ... 2007425 files and directories currently installed.)
Unpacking linux-headers-3.2.0-101-generic-pae (from .../linux-headers-3.2.0-101-generic-pae_3.2.0-101.141_i386.deb) ...
Setting up linux-headers-3.2.0-101-generic-pae (3.2.0-101.141) ...
Examining /etc/kernel/header_postinst.d.
Setting up linux-headers-generic-pae (3.2.0.101.117) ...
```

This may have done the trick.
The glaring red eye in the toolbar has gone away.
However there are over 200 updates that will not load (still Waiting ...)
Is it advisable to upgrade without those updates?
And is there an easy and fast way to clear so many of those old Linux kernels and headers?

Finally updated and much thanks for the help.
But what are the options for cleaning out the needless Linux kernels and headers?
This information has been helpful for me 
[https://askubuntu.com/questions/2793/how-do-i-remove-old-kernel-versions-to-clean-up-the-boot-menu](https://askubuntu.com/questions/2793/how-do-i-remove-old-kernel-versions-to-clean-up-the-boot-menu)

---

### Post by Bashing-om on 2017-04-18
Gnutron; Well ..

This is linux ,,, there are many paths to an end .
I do not want nor intend to confuse you further in a means to remove old kernels from that older distro.
Me being terminal minded like I am ,,, and a staunch supporter of KISS =>
I do it like so:
As an example only ! Make sure you know the booting kernel (uname -r) DO NOT mess with it !
```

sudo dpkg -P linux-signed-image-3.13.0-{36,37,39,40,41,43,44}-generic
sudo dpkg -P linux-image-extra-3.13.0-{36,37,39,40,41,43,44}-generic
sudo dpkg -P linux-image-3.13.0-{36,37,39,40,41,43,44}-generic
sudo dpkg -P linux-headers-3.13.0-{36,37,39,40,41,43,44}

```

Where I am dropping down to what apt is build on - dpkg - that operates at an even lower level and 'P" to purge all the targets .
Here I use bash's brace expansion to deal with a bunch at one time ,
These commands are in-line with what my little mind can keep track of .

If you have ANY doubts or fears about removing old kernels . Please share so we can address them ,
You do need to get that disk usage way down to less than 85% capacity , At this level of usage linux has it's issues in allocating file space and keeping track , We try and keep all file data in contiguous blocks . When the system can not, performance suffers greatly .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Impavidus on 2017-04-19
You had a problem with linux-headers-3.2.0-101-generic-pae. The latest version is linux-headers-3.2.0-126-generic-pae. You may have quite a lot to uninstall. Either use dpkg or synaptic, whatever you find best.

In your messages I also found```
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
```Google no longer supports a 32-bit version of Chrome. Uninstall Chrome (if you still have it) and disable that repository. Don't run unsupported software, especially web browsers.

Support for Ubuntu 12.04 will end a week from now. Upgrading is most likely to succeed on a clean and fully updated system. You can either upgrade to 14.04, which has 2 years of support left, or run 2 upgrades to get to 16.04, which has 4 years of support left. But a clean install may be faster than a single upgrade and much faster (and more reliable) than a double upgrade. And you can first test it on a live disk, to make sure it's still compatible with your hardware. If you decide to do a clean install, there's no need to clean up 12.04.

---

