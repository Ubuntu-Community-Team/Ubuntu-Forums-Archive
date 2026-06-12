---
title: "unmet dependencies - not able to upgrade to 12.04"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by namaster on 2012-06-04
```
The following packages have unmet dependencies:

firefox: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is installed
```

Now as suggested if I try to run apt-get install -f I get this:

```
hell@hell-laptop:~$ sudo apt-get install -f
[sudo] password for hell: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
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
hell@hell-laptop:~$ 

```

Can someone please help me to fix this issue?

---

### Post by dino99 on 2012-06-04
you might need to purge some ppa bringing that conflict

---

### Post by cortman on 2012-06-04
Try the suggestions given in the first answer to [this question]("http://askubuntu.com/questions/109994/dpkg-error-parsing-file-var-lib-dpkg-status-near-line-6449").

---

### Post by namaster on 2012-06-08
Well after trying autoremove same issue:

```
hell@hell-laptop:~$ sudo apt-get clean
hell@hell-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 firefox : Breaks: adobe-flashplugin (<= 11.1.102.63-0oneiric1) but 10.0.12.36-1hardy1 is installed
E: Unmet dependencies. Try using -f.
```

Which makes me go back to same step 1 which i posted in first topic.

---

### Post by namaster on 2012-06-08
> **dino99 said:**
> you might need to purge some ppa bringing that conflict

How to do that? Can u please guide?

Thanks

---

### Post by zombifier25 on 2012-06-08
Okay, this is the weirdest case I have ever seen. You are using Oneiric right? And why are there Hardy packages in it?

Did you change your software sources recently? e.g. add a PPA, etc.

---

### Post by namaster on 2012-06-08
I believe both this adobe reader and adobe flash are pain in da butt:

```
hell@hell-laptop:~$ sudo dpkg --configure -a
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 5380 package 'adobereader-enu':
 error in Version string '8.1.2_SU1': invalid character in version number

```

---

### Post by namaster on 2012-06-08
> **zombifier25 said:**
> Okay, this is the weirdest case I have ever seen. You are using Oneiric right? And why are there Hardy packages in it?

Did you change your software sources recently? e.g. add a PPA, etc.

Yes, I am on Oneiric. I am not sure why their is hardy package. I had updated from Hardy to Oneric while back. May be left over package? Not sure.

```
hell@hell-laptop:~$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:printing-3.2-ia32:printing-3.2-noarch:printing-4.0-ia32:printing-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

```

I think if i could remove adobe flasplugin and adobe reader completely issue can be fixed, no?

---

### Post by zombifier25 on 2012-06-08
Can you post the result of
```
less /etc/apt/sources.list.d/*-partner.list
```

---

### Post by namaster on 2012-06-08
> **zombifier25 said:**
> Can you post the result of
```
less /etc/apt/sources.list.d/*-partner.list
```

hrm..

```
hell@hell-laptop:~$ less /etc/apt/sources.list.d/*-partner.list
/etc/apt/sources.list.d/*-partner.list: No such file or directory

```

Something wrong with command?

---

### Post by namaster on 2012-06-08
Also when I try to remove adobe-flash from synaptics packet manager I get this:

```
E: adobe-flashplugin: subprocess installed pre-removal script returned error exit status 2

```

[http://imageshack.us/photo/my-images/442/adobeh.png/](http://imageshack.us/photo/my-images/442/adobeh.png/)

---

