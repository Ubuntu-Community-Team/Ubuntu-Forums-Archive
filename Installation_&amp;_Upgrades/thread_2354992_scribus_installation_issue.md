---
title: "scribus installation issue"
date: 2017-03-08
forum: Installation &amp; Upgrades
---

### Post by shyspook on 2017-03-08
I can't install scribus desktop on ubuntu 16.04 properly. I'm a novice to ubuntu, sorry. But look at that please:
 scribus:
 Depends: python-tk  but it is not installable
 Depends: scribus-data but it is not going to be installed
 Depends: libpodofo0.9.3 but it is not going to be installed
 Recommends: icc-profiles-free  but it is not installable


What am I to do? thanks

---

### Post by howefield on 2017-03-08
How are you installing the scribus package, is it from the Ubuntu repositories ?

---

### Post by shyspook on 2017-03-08
yes. But i've also tried to install it from repositories through terminal, it does't work neither

---

### Post by howefield on 2017-03-08
Ok, a couple of things first.. it is better for those who might be able to offer some help if you put some detail into your posts, eg chronological details of what you did including the full output of terminal text between [noparse]```

```[/noparse] tags.

Can we see what repositories you have enabled ?

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by shyspook on 2017-03-08
sorry, wait a minute. let me see -

> **howefield said:**
> Ok, a couple of things first.. it is better for those who might be able to offer some help if you put some detail into your posts, eg chronological details of what you did including the full output of terminal text between [noparse]```

```[/noparse] tags.

Can we see what repositories you have enabled ?

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```


all I do is:
```
sudo add-apt-repository ppa:scribus/ppa
sudo apt update
sudo apt install scribus-ng
```

and all I get is this:

```
 Packages from the Scribus friends

scribus: current 1.4.x branch
scribus-ng: current 1.5.x branch
scribus-trunk: whatever inside the current svn repository, built daily.

scribus-trunk is not updated anymore in 14.04 LTS Trusty Tahr (and 14.10, 15.04 and 15.10) due to a too old Qt, please upgrade your system to a newer Ubuntu release (suggested: 16.04 LTS Xenial Xerus).

SCRIBUS FILES ARE NOT BACKWARDS COMPATIBLE!!
FILES SAVED WITH SCRIBUS-TRUNK OR SCRIBUS-NG CAN'T BE OPENED BY OLDER VERSIONS OF SCRIBUS ANYMORE!!

Back up all your project files before using the svn daily builds as you won't be able to use them with scribus or scribus-ng anymore!

To install the debug symbols you need to add this to your sources.list:
'deb [http://ppa.launchpad.net/scribus/ppa/ubuntu](http://ppa.launchpad.net/scribus/ppa/ubuntu) xenial main/debug'
 More info: [https://launchpad.net/~scribus/+archive/ubuntu/ppa](https://launchpad.net/~scribus/+archive/ubuntu/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpwar9kwzh/secring.gpg' created
gpg: keyring `/tmp/tmpwar9kwzh/pubring.gpg' created
gpg: requesting key 64B6EE15 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpwar9kwzh/trustdb.gpg: trustdb created
gpg: key 64B6EE15: public key "Launchpad PPA for Scribus friends" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
```
```
robert@123:~$ sudo apt update
Hit:1 [http://ppa.launchpad.net/canonical-chromium-builds/stage/ubuntu](http://ppa.launchpad.net/canonical-chromium-builds/stage/ubuntu) xenial InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Ign:3 [http://ppa.launchpad.net/chromium-daily/beta/ubuntu](http://ppa.launchpad.net/chromium-daily/beta/ubuntu) xenial InRelease     
Ign:4 [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) xenial InRelease      
Hit:5 [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) xenial InRelease      
Ign:6 [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) xenial InRelease              
Hit:7 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial InRelease    
Hit:8 [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) xenial InRelease 
Ign:9 [http://ppa.launchpad.net/s-lagui/ppa/ubuntu](http://ppa.launchpad.net/s-lagui/ppa/ubuntu) xenial InRelease      
Ign:10 [http://dl.maxthon.com/linux/deb](http://dl.maxthon.com/linux/deb) stable InRelease
Hit:11 [http://ppa.launchpad.net/scribus/ppa/ubuntu](http://ppa.launchpad.net/scribus/ppa/ubuntu) xenial InRelease
Hit:12 [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) xenial InRelease
Hit:14 [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) xenial InRelease
Ign:15 [http://ppa.launchpad.net/ubuntuhandbook1/ppa/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/ppa/ubuntu) xenial InRelease
Hit:16 [http://ppa.launchpad.net/unit193/xombrero/ubuntu](http://ppa.launchpad.net/unit193/xombrero/ubuntu) xenial InRelease
Get:13 [http://dl.maxthon.com/linux/deb](http://dl.maxthon.com/linux/deb) stable Release [512 B]
Err:17 [http://ppa.launchpad.net/chromium-daily/beta/ubuntu](http://ppa.launchpad.net/chromium-daily/beta/ubuntu) xenial Release
  404  Not Found
Err:18 [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) xenial Release 
  404  Not Found
Err:19 [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) xenial Release         
  404  Not Found
Get:20 [http://dl.maxthon.com/linux/deb](http://dl.maxthon.com/linux/deb) stable Release.gpg [836 B]        
Err:21 [http://ppa.launchpad.net/s-lagui/ppa/ubuntu](http://ppa.launchpad.net/s-lagui/ppa/ubuntu) xenial Release              
  404  Not Found
Err:22 [http://ppa.launchpad.net/ubuntuhandbook1/ppa/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/ppa/ubuntu) xenial Release
  404  Not Found
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/chromium-daily/beta/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/chromium-daily/ppa/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/midori/ppa/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/s-lagui/ppa/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/ubuntuhandbook1/ppa/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: [http://dl.maxthon.com/linux/deb/dists/stable/Release.gpg:](http://dl.maxthon.com/linux/deb/dists/stable/Release.gpg:) Signature by key 95E109DBE9716A84AF6393463189CF97F8D030EC uses weak digest algorithm (SHA1)
robert@123:~$ sudo apt install scribus-ng
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 scribus-ng : Depends: python-tk but it is not installable
              Depends: scribus-ng-data (= 1.5.2-0ubuntu16.04.0~ppa0) but it is not going to be installed
              Recommends: icc-profiles-free but it is not installable
E: Unable to correct problems, you have held broken packages.
```

Or - does anybody know some other publishing tools? I installed "sisu" but it's too weird for me, it runs from terminal only

and I've tried to follow a video tutorial/ the result is zero. only with slight differences:
```
 ~ sudo apt-get install scribus-trunkReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 scribus-trunk : Depends: python-tk but it is not installable
                 Depends: scribus-trunk-data (= 1.5.3svn~r21814~20170307~ppa65~ubuntu16.04.1) but it is not going to be installed
                 Recommends: icc-profiles-free but it is not installable
E: Unable to correct problems, you have held broken packages.
```

---

### Post by ajgreeny on 2017-03-08
I note you have some ppa repos enabled which are causing you problems as well as your scribus installation, so you should disable them as they have no xenial version.
```
Err:17 http://ppa.launchpad.net/chromium-daily/beta/ubuntu xenial Release
  404  Not Found
Err:18 http://ppa.launchpad.net/chromium-daily/ppa/ubuntu xenial Release 
  404  Not Found
Err:19 http://ppa.launchpad.net/midori/ppa/ubuntu xenial Release         
  404  Not Found
Get:20 http://dl.maxthon.com/linux/deb stable Release.gpg [836 B]        
Err:21 http://ppa.launchpad.net/s-lagui/ppa/ubuntu xenial Release              
  404  Not Found
Err:22 http://ppa.launchpad.net/ubuntuhandbook1/ppa/ubuntu xenial Release
  404  Not Found
```

---

### Post by howefield on 2017-03-08
In the absence of the requested information, I'd just add that your packaging system is in a bit of a mess due to adding PPAs, one or more of which is conflicting with the Ubuntu package versions, and also several non existent repositories.

You probably have to take your system back to as close to default as you can. Then a simple

```
sudo apt install scribus
``` 

will work.

You have a choice of going through the "easy" enough but tedious process of ridding your system of the errant repository sources or cutting your losses and reinstalling, time wise there is probably not much between those options ;)

---

