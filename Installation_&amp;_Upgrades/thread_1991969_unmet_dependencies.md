---
title: "unmet dependencies"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by namaster on 2012-05-31
While updating to 12.10 LTS version i am getting unmet dependencies  error. 

So i tried:

sudo apt-get -f install as suggested but still it didn't fixed the issue. 

Here is the output:
```
The following packages were automatically installed and are no longer required:
  libgmp3c2 wine1.2-gecko libblas3gf python-smartpm libgnome-desktop-2-17
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 10.1 MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 5380 package 'adobereader-enu':
 error in Version string '8.1.2_SU1': invalid character in version number
(Reading database ... 324015 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How can i resolve the issue? 

Thanks

---

### Post by namaster on 2012-05-31
The following packages have unmet dependencies:

firefox: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is installed

Edit: Also tried sudo apt-get upgrade

hell@hell-laptop:~$ sudo apt-get upgrade
[sudo] password for hell: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 firefox : Breaks: adobe-flashplugin (<= 11.1.102.63-0oneiric1) but 10.0.12.36-1hardy1 is installed
E: Unmet dependencies. Try using -f.
hell@hell-laptop:~$

Now with sudo apt-get upgrade -f
```

hell@hell-laptop:~$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 10.1 MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 5380 package 'adobereader-enu':
 error in Version string '8.1.2_SU1': invalid character in version number
(Reading database ... 324015 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

