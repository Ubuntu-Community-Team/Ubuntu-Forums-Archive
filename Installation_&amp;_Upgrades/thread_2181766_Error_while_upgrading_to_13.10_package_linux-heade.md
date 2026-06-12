---
title: "Error while upgrading to 13.10 package linux-headers-3.8.0-30 needs to be reinstalled"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by LYJ7trm on 2013-10-19
[COLOR=#000000]Using Lubuntu I get this error with sudo apt-get dist-upgrade[/COLOR]



[COLOR=#000000]E: The package linux-headers-3.8.0-30 needs to be reinstalled, but I can't find an archive for it.[/COLOR]

[COLOR=#000000]What can I do?[/COLOR]

---

### Post by heir4c on 2013-10-19
Open a terminal and type:
```
sudo apt-get install --reinstall linux-headers-3.8.0-30
```
Or install first synaptic and then look for linux-headers-3.8.0-30, click on the little square at the left of the packages and choose to reinstall the packages.

---

### Post by LYJ7trm on 2013-10-21
Result:
sudo apt-get install --reinstall linux-headers-3.8.0-30
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-headers-3.8.0-30 needs to be reinstalled, but I can't find an archive for it.



When I open Synaptic I get a popup window with the same error.  I can't get to any of the functions of Synaptic (it closes when I click on the error window)

---

### Post by ian-weisser on 2013-10-22
What version of Ubuntu are you running?
That package is available only for 12.04 and 13.04.  See [http://packages.ubuntu.com/search?keywords=linux-headers-3.8.0-30](http://packages.ubuntu.com/search?keywords=linux-headers-3.8.0-30)

---

### Post by LYJ7trm on 2013-11-12
I am running Lubuntu 13.04 and I'm trying to upgrade to 13.10.

---

### Post by ian-weisser on 2013-11-12
Is there a reason you need that specific set of kernel headers?
13.04 and 13.10 run different kernels.
Wouldn't you want a set of 13.10's kernel headers?

Here, you can see that an updated 13.04 runs 3.8.0-33 (your -30 has been superseded)
And an updated 13.10 runs 3.11.0-13
And 14.04 will run something different from both of those.
```
$ rmadison -u ubuntu linux-image
[...]
linux-image | 3.8.0.19.35 |        raring | amd64, armhf, i386
linux-image | 3.8.0.33.51 | raring-updates | amd64, armhf, i386
linux-image | 3.11.0.12.13 |         saucy | amd64, armhf, i386
linux-image | 3.11.0.13.14 | saucy-updates | amd64, armhf, i386
linux-image | 3.12.0.2.4 |        trusty | amd64, armhf, i386

```

---

### Post by fantab on 2013-11-12
> **LYJ7trm said:**
> [COLOR=#000000]Using Lubuntu I get this error with sudo apt-get dist-upgrade[/COLOR]

[COLOR=#000000]E: The package linux-headers-3.8.0-30 needs to be reinstalled, but I can't find an archive for it.[/COLOR]

[COLOR=#000000]What can I do?[/COLOR]

You have remove that package. Try the following:
```
sudo -i
dpkg --purge [COLOR=#000000]linux-headers-3.8.0-30[/COLOR]
apt-get remove --purge [COLOR=#000000]linux-headers-3.8.0-30[/COLOR]
apt-get clean 
apt-get update 
apt-get upgrade
exit
```

If you get errors after 'apt-get update' then post them here.
If no errors then you are good to go.

---

### Post by robiitb on 2013-11-19
I too have the same problem but I can not help help meee please

---

### Post by robiitb on 2013-11-19
this only after I tried to update to version 13.10

---

### Post by fantab on 2013-11-19
> **robiitb said:**
> I too have the same problem but I can not help help meee please

> **robiitb said:**
> this only after I tried to update to version 13.10

Please start a new thread and describe in detail what the problem is.
Post the output of:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by robiitb on 2013-11-19
the problem started when I tried I was asked to approve a new software update to version 10.13
at the end of all downlod born this error: The package linux-headers-3.8.0-30 needs to be reinstalled, but I can not find an archive for it.


robert @ robert- 1015BX 1015BX - : ~ $ sudo apt- get update
[ sudo ] password for robert :
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy Release.gpg
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg
Found [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg
Get: 1 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release.gpg [ 933 B]
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) saucy -security Release.gpg [ 933 B]
Downloading : 3 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg [ 72 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -backports Release.gpg
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://archive.canonical.com](http://archive.canonical.com) saucy Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy Release
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) saucy -security Release [ 49.6 kB ]
Found [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release
Downloading : 5 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release [ 49.6 kB ]
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -backports Release
Found [http://archive.canonical.com](http://archive.canonical.com) saucy / partner i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Sources
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release
  
Found [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Sources
Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources [ 10.8 kB ]
Found [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Sources
Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources [14 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main i386 Packages
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources [ 5271 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted i386 Packages
Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources [ 688 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe i386 Packages
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages [ 36.8 kB ]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en
Get: 12 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages [ 11.8 kB ]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en_US
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en
Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages [ 1389 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en
Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation- en [ 15.4 kB ]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en_US
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse i386 Packages
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse Translation- en
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe Translation- en
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en_US
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe
Fetched 134 kB in 4s (28.0 kB / s)
Reading package lists ... done
W : There was an error in verifying the signature . The repository is not updated and the previous index files will be used . GPG  error : [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release: The  following signatures were invalid : BADSIG 40976EAF437D05B5 Ubuntu  Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release](http://it.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release)

W: Some index files failed to download they have been ignored , or old ones will be used .
robert @ robert- 1015BX 1015BX - : ~ $ sudo apt- get dist -upgrade
Reading package lists ... done
Building dependency tree
Reading state information ... done
E: Package linux- headers- 3.8.0- 30 must be reinstalled, but I can not find an archive

---

### Post by robiitb on 2013-11-19
since the terminal command does not take any more thus responding: The package linux-headers-3.8.0-30 needs to be reinstalled, but I can not find an archive for it.

---

### Post by ian-weisser on 2013-11-19
Of course you can't find an archive for it. It's *old*. It's been replaced be a newer version.

Did you follow Fantab's advice in Post #7 of this thread?

---

### Post by robiitb on 2013-11-20
yess I tried everything but  it does not work




   I apologize if I express myself badly wrapped but I'm using google translation services because I write from italy

---

### Post by ian-weisser on 2013-11-20
(withdrawn)

---

### Post by fantab on 2013-11-20
Post the output of:

```
sudo update-grub
sudo uname -r
sudo uname -a
```

Also you are showing 'raring' Launchpad repository.  You can change it to 'saucy' from 'Software Center' -> EDIT -> Software Sources-> Other Sofware-> Select Lauchpad repo and Edit. Change 'raring' to 'saucy'. 

Then run 'apt-get update'.

---

### Post by robiitb on 2013-11-20
robert @ robert- 1015BX 1015BX - : ~ $ sudo update -grub
[ sudo ] password for robert :
Sorry, try again .
[ sudo ] password for robert :
Creating grub.cfg ...
Found linux image : / boot/vmlinuz-3.8.0-32-generic
Found initrd image : / boot/initrd.img-3.8.0-32-generic
Found linux image : / boot/vmlinuz-3.8.0-31-generic
Found initrd image : / boot/initrd.img-3.8.0-31-generic
Found linux image : / boot/vmlinuz-3.8.0-30-generic
Found initrd image : / boot/initrd.img-3.8.0-30-generic
Found linux image : / boot/vmlinuz-3.8.0-29-generic
Found initrd image : / boot/initrd.img-3.8.0-29-generic
Found linux image : / boot/vmlinuz-3.8.0-27-generic
Found initrd image : / boot/initrd.img-3.8.0-27-generic
Found linux image : / boot/vmlinuz-3.8.0-26-generic
Found initrd image : / boot/initrd.img-3.8.0-26-generic
Found memtest86 + image : / boot/memtest86 + . Bin
fact
robert @ robert- 1015BX 1015BX - : ~ $ sudo uname -r
3.8.0 -32 -generic
robert @ robert- 1015BX 1015BX - : ~ $ sudo uname-a
Robert- 1015BX 1015BX linux - 3.8.0 -32 -generic # 47 - Ubuntu SMP Tue Oct 1 21:36:40 UTC 2013 i686 athlon i686 GNU / Linux



what can i do? I do not even open ubuntu software center
help me pleasee

---

### Post by robiitb on 2013-11-20
I do not know what to do

---

### Post by fantab on 2013-11-20
The output shows that you are currently running "3.8.0 -**32** -generic" and that you FIVE older unused kernels.
Lets remove all the other 'unused' kernels which are listed by 'update-grub', including the problematic 'linux- headers- 3.8.0- 30', with the following:

```
sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```

Report Errors, if any. Then run:

```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
```

Report Errors, if any.

---

### Post by robiitb on 2013-11-21
yes the are :(



robert  @ robert- 1015BX - 1015BX : ~ $ sudo dpkg-l linux- * | awk ' / ^ ii / {  print $ 2 } ' | grep -v -e ` uname -r | cut- f1, 2 -d " - " `| grep -e [ 0-9] | xargs sudo apt-get -y purge
[ sudo ] password for robert :
Reading package lists ... fact
Building dependency tree
Reading state information ... fact
E: Package linux -headers- 3.8.0 -30 needs to be reinstalled , but I can not find an archive.
robert @ robert- 1015BX 1015BX - : ~ $ sudo apt -get clean
robert @ robert- 1015BX 1015BX - : ~ $ sudo apt- get autoremove
Reading package lists ... fact
Building dependency tree
Reading state information ... fact
E: Package linux -headers- 3.8.0 -30 needs to be reinstalled , but I can not find an archive.
robert @ robert- 1015BX 1015BX - : ~ $ sudo apt-get- f install
Reading package lists ... fact
Building dependency tree
Reading state information ... fact
E: Package linux -headers- 3.8.0 -30 needs to be reinstalled , but I can not find an archive.
robert @ robert- 1015BX 1015BX - : ~ $ sudo apt- get update
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy Release.gpg
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg
Download : 1 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release.gpg [ 933 B]
Downloading : 2 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg [72 B]
Found [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg
Downloading : 3 [http://security.ubuntu.com](http://security.ubuntu.com) saucy -security Release.gpg [ 933 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -backports Release.gpg
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy Release
Found [http://archive.canonical.com](http://archive.canonical.com) saucy Release
Found [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release
Downloading : 4 [http://security.ubuntu.com](http://security.ubuntu.com) saucy -security Release [ 49.6 kB ]
Downloading : 5 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release [ 49.6 kB ]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -backports Release
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Sources
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release
  
Found [http://archive.canonical.com](http://archive.canonical.com) saucy / partner i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Sources
Found [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Sources
Downloading : 6 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources [ 10.8 kB ]
Found [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main i386 Packages
Downloading : 7 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources [14 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted i386 Packages
Downloading : 8 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources [ 5271 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse i386 Packages
Downloading : 9 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources [ 688 B]
Download : 10 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages [ 36.7 kB ]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en
Downloading : 11 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en
Downloading : 12 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages [ 11.8 kB ]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en_US
Downloading : 13 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages [ 1389 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en_US
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en_US
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe Sources
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse i386 Packages
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse Translation- en
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe Translation- en
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en_US
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe
Recovered 118 kB in 4s ( 24.1 kB / s)
Reading package lists ... fact
W : There was an error in verifying the signature . The repository is not updated and the previous index files will be used . GPG  error : [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release: The  following signatures were invalid : BADSIG 40976EAF437D05B5 Ubuntu  Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W : Failed to retrieve [http://it.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release](http://it.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release)

W: Some index files failed to download they have been ignored , or old ones will be used .
robert @ robert- 1015BX 1015BX - : ~ $ sudo apt- get dist -upgrade
Reading package lists ... fact
Building dependency tree
Reading state information ... fact
E: Package linux -headers- 3.8.0 -30 needs to be reinstalled , but I can not find an archive.
robert @ robert- 1015BX 1015BX - : ~ $ ^ C
robert @ robert- 1015BX 1015BX - : ~ $

---

### Post by robiitb on 2013-11-21
I'm going crazy I do not know what to do

---

### Post by fantab on 2013-11-21
Well, I don't know what else to suggest. If I were you, I'd reinstall Ubuntu and save me anymore pain and ache.

---

### Post by robiitb on 2013-11-25
please help meee

---

### Post by ian-weisser on 2013-11-25
Tryyy thisss. If there are errors, show us the complete output. Use ```
 tags.
[CODE]sudo apt-get remove linux-headers-3.8.0-30
```

---

### Post by robiitb on 2013-11-26
the output are there 

robert @ robert-1015BX 1015BX-: ~ $ sudo apt-get remove linux-headers-3.8.0-30
[sudo] password for robert:
Reading package lists ... fact
Building dependency tree
Reading state information ... fact
E: Package linux-headers-3.8.0-30 needs to be reinstalled, but I can not find an archive.
robert @ robert-1015BX 1015BX-: ~ $

---

### Post by ian-weisser on 2013-11-26
Well, it was worth a try.

Next, try **sudo dpkg --force-remove-reinstreq --remove linux-headers-3.8.0-30**
If that works, then **sudo apt-get update && sudo apt-get upgrade**

---

### Post by robiitb on 2013-11-26
this is the output
robert @ robert-1015BX 1015BX-: ~ $ sudo dpkg - force-remove-reinstreq - remove linux-headers-3.8.0-30
[sudo] password for robert:
dpkg: warning: the problem is ignored because it is used the - force option:
  Package is in a very bad inconsistent state - is
  must reinstall it before removing it.
(Reading database ... 332 441 files and directories currently installed.)
robert @ robert- 1015BX 1015BX - : ~ $ sudo apt- get update
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy Release.gpg
Download : 1 [http://security.ubuntu.com](http://security.ubuntu.com) saucy -security Release.gpg [ 933 B]
Found [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg
Found [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg
Downloading : 2 [http://security.ubuntu.com](http://security.ubuntu.com) saucy -security Release [ 49.6 kB ]
Downloading : 3 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release.gpg [ 933 B]
Found [http://archive.canonical.com](http://archive.canonical.com) saucy Release
Found [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -backports Release.gpg
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy Release
Found [http://archive.canonical.com](http://archive.canonical.com) saucy / partner i386 Packages
Found [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Sources
Downloading : 4 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release [ 49.6 kB ]
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -backports Release
Downloading : 5 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources [ 11.5 kB ]
Found [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main i386 Packages
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release
  
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Sources
Downloading : 6 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources [14 B]
Downloading : 7 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources [ 6871 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Sources
Downloading : 8 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources [ 688 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Sources
Downloading : 9 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages [ 37.3 kB ]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main i386 Packages
Download : 10 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Downloading : 11 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages [ 15.8 kB ]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted i386 Packages
Downloading : 12 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages [ 1389 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en_US
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation- en
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation- en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en_US
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation- en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse i386 Packages
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main Translation- en
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse Translation- en
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted Translation- en
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe Translation- en
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en_US
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe
Recovered 125 kB in 6s ( 18.5 kB / s)
Reading package lists ... fact
W : There was an error in verifying the signature . The repository is not updated and the previous index files will be used . GPG  error : [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release: The  following signatures were invalid : BADSIG 40976EAF437D05B5 Ubuntu  Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W : Failed to retrieve [http://it.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release](http://it.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release)

W: Some index files failed to download they have been ignored , or old ones will be used .
robert @ robert- 1015BX 1015BX - : ~ $ sudo apt- get upgrade
Reading package lists ... fact
Building dependency tree
Reading state information ... fact
It is useful to run "apt -get- f install ' to correct this.
The following packages have unmet dependencies:
 linux- headers- 3.8.0 -30 -generic : Depends: linux- headers- 3.8.0 -30 but it is not installable
E: Unmet dependencies . Try using- f .
robert @ robert- 1015BX 1015BX - : ~ $

---

### Post by fantab on 2013-11-26
Try again the suggestions from my earlier post [#7]("http://ubuntuforums.org/showthread.php?t=2181766&p=12845929#post12845929").

---

### Post by robiitb on 2013-11-27
i try evrythink but now the error is this:
linux-headers-3.8.0-30-generic: Depends: linux-headers-3.8.0-30 but it is not installable

---

### Post by ian-weisser on 2013-11-27
Try:
```
sudo dpkg --remove --force-remove-reinstreq linux-headers-3.8.0-30
```
Apologies, I had the command order reversed before.

Then update and upgrade to see if the package manager error has changed.


Please use [code] tags for output. It makes the output much easier to read.

---

### Post by robiitb on 2013-11-27
there are the output


dpkg: attenzione: viene ignorata la richiesta di rimuovere linux-headers-3.8.0-30 poiché non è installato
robert@robert-1015BX-1015BX:~$ sudo dpkg reinstall linux-headers-3.8.0-30
dpkg: errore: necessaria un'opzione che indichi un'azione

Usare dpkg --help per un aiuto sull'installazione e la rimozione dei pacchetti 
[*].
Usare "dselect" o "aptitude" per un'interfaccia alla gestione dei pacchetti.
Usare dpkg -Dhelp per l'elenco delle opzioni di debug per dpkg.
Usare dpkg --force-help per l'elenco delle opzioni di forzatura.
Usare dpkg-deb --help per un aiuto sulla manipolazione dei file *.deb.

Le opzioni indicate con 
[*] producono output prolisso - creare una pipe con "less" o "more".
robert@robert-1015BX-1015BX:~$ sudo dpkg --remove --force-remove-reinstreq linux-headers-3.8.0-30
dpkg: attenzione: viene ignorata la richiesta di rimuovere linux-headers-3.8.0-30 poiché non è installato
robert@robert-1015BX-1015BX:~$

---

### Post by ian-weisser on 2013-11-27
> **robiitb said:**
> robert@robert-1015BX-1015BX:~$ sudo dpkg --remove --force-remove-reinstreq linux-headers-3.8.0-30
dpkg: attenzione: viene ignorata la richiesta di rimuovere linux-headers-3.8.0-30 poiché non è installato

That's exactly what we want it to say!
Remember, we're trying to uninstall it. Looks like we uninstalled it.
DON'T reinstall it.

**sudo apt-get update && sudo apt-get upgrade**

---

### Post by robiitb on 2013-11-27
this is the output


Downloading : 5 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources [ 11.5 kB ]
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / restricted Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Sources
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / multiverse Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Sources
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / universe i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Sources
Downloading : 6 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources [14 B]
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / main i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Sources
Downloading : 7 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources [ 6871 B]
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main i386 Packages
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / restricted i386 Packages
Downloading : 8 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources [ 688 B]
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted i386 Packages
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / multiverse i386 Packages
Downloading : 9 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages [ 37.3 kB ]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe i386 Packages
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse i386 Packages
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / main Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en_US
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / main Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en
Saucy Release.gpg Ign [http://ppa.launchpad.net](http://ppa.launchpad.net)
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg
Download : 10 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / multiverse Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en
Downloading : 11 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages [ 15.8 kB ]
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / multiverse Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en_US
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en
Downloading : 12 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages [ 1389 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en
Release Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / restricted Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main Sources
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / restricted Translation- en
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe Sources
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / universe Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse Sources
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / universe Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main i386 Packages
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted i386 Packages
Release Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse i386 Packages
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Release Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe Translation- en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / main Translation- en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / multiverse Translation- en_US
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / restricted Translation- en_US
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / universe Translation- en_US
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en_US
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en_US
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en_US
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en_US
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages
Found [http://archive.getdeb.net](http://archive.getdeb.net) raring - getdeb Release.gpg
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
Found [http://archive.getdeb.net](http://archive.getdeb.net) raring - getdeb Release
Found [http://archive.getdeb.net](http://archive.getdeb.net) raring-getdeb/games i386 Packages
Translation- en_US Ign [http://archive.getdeb.net](http://archive.getdeb.net) raring-getdeb/games
Translation- en Ign [http://archive.getdeb.net](http://archive.getdeb.net) raring-getdeb/games
Translation- en Ign [http://archive.getdeb.net](http://archive.getdeb.net) raring-getdeb/games
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages
  404 Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages
  404 Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages
  404 Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Recovered 125 kB in 14s ( 8353 B / s )
Reading package lists ... fact
W : There was an error in verifying the signature . The repository is not updated and the previous index files will be used . GPG  error : [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release: The  following signatures were invalid : BADSIG 40976EAF437D05B5 Ubuntu  Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W : Failed to retrieve [http://it.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release](http://it.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release)

W : Failed to retrieve [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/saucy/main/binary-i386/Packages) 404 Not Found

W : Failed to retrieve [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/raring/main/source/Sources](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/raring/main/source/Sources) 404 Not Found

W : Failed to retrieve [http://ppa.launchpad.net/m-gehre/ppa/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/m-gehre/ppa/ubuntu/dists/saucy/main/binary-i386/Packages) 404 Not Found

W : Failed to retrieve [http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/saucy/main/binary-i386/Packages) 404 Not Found

W: Some index files failed to download they have been ignored , or old ones will be used .
robert @ robert- 1015BX 1015BX - : ~ $ sudo apt- get upgrade
Reading package lists ... fact
Building dependency tree
Reading state information ... fact
The following packages have been kept at their current version :
  account -plugin -aim account -plugin- account -plugin- facebook flickr
  account -plugin- google accounts -plugin- jabber account -plugin- salut
  account -plugin -twitter account -plugin -windows- live account -plugin- yahoo
  accountsservice activity -log -manager- control-center
  adobe -flash -properties- gtk adobe - flashplugin alsa- utils apparmor aptdaemon
  apturl apturl -common bamfdaemon baobab bind9-host brasero brasero - cdrkit
  brasero -common brltty checkbox checkbox -qt compiz clementines colord
  compiz -core compiz -gnome compiz -plugins -default cups cups- bsd cups-client
  cups cups -filters dbus -daemon -tools dconf deja- dup dnsutils empathy
  empathy -common eog shows clear -common evolution- data-server
  evolution- data-server -common file-roller firefox -common folks
  friends- dispatcher gcr gdb gedit gedit -common gir1.2 - ebook -1.2
  gir1.2 - edataserver -1.2 gir1.2 - gdata -0.0 gir1.2 - goa -1.0 gir1.2 -gtk -3.0
  gir1.2 - gtksource -3.0 gir1.2 - packagekitglib -1.0 gir1.2 - pango -1.0
  gir1.2 -rb -3.0 gir1.2 -unity -5.0 gir1.2 wnck -3.0 - gnome -calculator
  gnome -contacts gnome- control-center gnome- control-center -data
  gnome- control-center - signon gnome- control-center -unity gnome- disk-utility
  gnome- font -viewer gnome -keyring gnome -mines gnome -screensaver gnome-session
  gnome -session- bin gnome-session -common gnome-settings -daemon
  gnome-system -log gnome- system-monitor gnome-terminal gstreamer1.0 -clutter
  gstreamer1.0 gstreamer1.0 -plugins -bad -plugins -good - gstreamer1.0 x gucharmap
  guile -2.0 -libs gvfs gvfs -backends gvfs -bin gvfs -common gvfs - daemons
  gvfs-fuse gvfs -libs hplip hplip -data hud ibus ibus -gtk ibus -pinyin ibus- GTK3
  ibus -pinyin -db -android -table ibus icedtea -7- jre- jamvm ifupdown
  appmenu bluetooth - indicator indicator- indicator- datetime indicator- power
  indicator -sound indicator- sync iproute iptables iputils -ping isc- dhcp-client
  isc- dhcp -common libaccount -plugin -1.0 -0 libasound2 libaccountsservice0
  libbind9 libbrasero -90 -1 - media3 libclutter libclutter -1.0 -0 - gst -2.0 -0
  libclutter -gtk -1.0 -0 libcmis -0.3 -3 - libcogl pango12 libcolord1
  libcompizconfig0 libcups2 libcupscgi1 libcupsfilters1 libcupsimage2
  libcupsmime1 libcupsppdc1 libdbusmenu - GTK3 -4 - libdbusmenu gtk4 libdecoration0
  libebook libecal -1.2 -14 -1.2 -15 -1.2 -17 libedataserver libegl1 - mesa
  libegl1 - mesa -drivers libevdocument3 libevview3 -4 -3 libfm -gtk -bin - libfm GTK3
  libfm3 libfolks - eds25 libfolks - telepathy25 libfolks25 libgail - 3-0
  libgail -common libgail18 libgbm1 libgcr -3-1 -GD2 libgd -perl libgdata13
  libgl1 - mesa-dri libgl1 - mesa- glx libglade2 -0 libglapi - mesa mesa - libgles2
  libgnome -control- Center1 libgoa -1.0 -0 -1.0 -common libgoa libgpgme11
  libgpod4 libgpod -common libgstreamer -plugins- bad1.0 -0
  libgstreamer -plugins- good1.0 -0 libgtk - 3-0 libgtk -3- bin libgtk -3 -common
  libgtk2.0 -0 libgtk2.0 -bin libgtkmm -3.0- 1 -3.0 -common libgtksourceview
  libgucharmap -2 90-7 libhpmud0 libhttp libido3 -message- perl -0.1 -0 libisccc90
  libisccfg90 libjavascriptcoregtk -3.0 -0 libjson - glib -1.0 -0 libjson0
  liblwres90 libmagickcore5 libmailtools -extra -perl - libmetacity private0a
  libnetfilter - conntrack3 libnss - winbind libnux -4.0- 0 - 4.0 -common libnux
  libosmesa6 libpam- winbind libpangomm libpango1.0 -0 - 1.4 -1 libplymouth2
  libpolkit -backend -1-0 libpolkit - gobject -1-0 libpoppler - glib8 libpulse0
  libpwquality1 libpython3 - stdlib libquvi7 libreoffice -base- core
  libreoffice -calc libreoffice -common libreoffice -core libreoffice -draw
  libreoffice -gnome libreoffice -gtk libreoffice -help- en-us libreoffice -help- en
  libreoffice -impress libreoffice -l10n- en libreoffice -math
  libreoffice - ogltrans libreoffice - pdfimport
  libreoffice - presentation- minimizer libreoffice -style- human
  libreoffice -writer libsane libsane libsane -common - hpaio libsasl2 -2
  libsignon - extension1 libsignon -plugins- base - common1 libsmbclient libsnmp
  libunity -protocol - private0 libunity - webapps0 libunity9 libvte - 2.90 -9
  libvte libwbclient0 libwebkitgtk -common - 2.90 -3.0 -0 - libwnck 3-0 libwnck22
  libwxgtk2.8 -0 libxfixes3 libxi6 lintian linux -generic linux-headers -generic
  linux- image-generic mcp - account -manager- UOA metacity -common Mousetweaks
  nautilus nautilus -data nautilus- sendto - empathy network-manager
  neverball -common -data neverball notify-osd onboard openjdk -7- jre
  openjdk -7- jre- headless openjdk -7- jre- lib pcmanfm plymouth plymouth -label
  pm- utils policykit poppler -utils -1 printer- driver - hpcups
  printer- driver - postscript -hp pulseaudio python- ibus python3 python3 - apport
  python3 - aptdaemon - aptdaemon.gtk3widgets python3 python3 - aptdaemon.pkcompat
  python3 python3 - brlapi - dirspec python3 python3 -gi - distupgrade
  python3 -gi- cairo python3 python3 -minimal -problem -report
  python3 python3 - software -properties - one samba -common samba -common -bin
  sessioninstaller seahorse shotwell signon -keyring -extension
  oauth2 - signon - plugins -plugin- signon password signon -ui signond smbclient
  software -properties -common software -properties- gtk ttf- dejavu -core
  dejavu -extra ttf- ubuntu- desktop ubuntu -minimal ubuntu- release- upgrader -core
  ubuntu- release- upgrader -gtk ubuntu -wallpapers unity unity- greeter
  unity -lens -applications unity -lens -files unity -lens -friends unity -lens -music
  unity -lens -photos gdrive unity unity- scope- one -services - libs3
  update-notifier update-notifier -common upower upstart ure virtualbox
  virtualbox- dkms virtualbox -qt winbind wine1.6 wine1.6 -i386 xdiagnose
  xserver -xorg -core xserver -xorg -input- evdev xserver -xorg -input- mouse
  xserver -xorg -input- synaptics xserver -xorg -input- vmmouse
  xserver -xorg -input- wacom xserver -xorg -video-ati xserver -xorg -video- cirrus
  xserver -xorg -video- fbdev xserver -xorg- video -intel xserver -xorg -video- mach64
  xserver -xorg -video- mga xserver -xorg -video- modesetting
  xserver -xorg -video- NeoMagic xserver -xorg -video- nouveau
  xserver -xorg -video- openchrome xserver -xorg -video- qxl xserver -xorg -video- r128
  xserver -xorg -video- radeon xserver -xorg- video -s3 xserver -xorg -video- savage
  xserver -xorg -video- siliconmotion xserver -xorg -video- sis
  xserver -xorg -video- sisusb xserver -xorg -video- tdfx xserver -xorg -video- trident
  xserver -xorg -video- vesa xserver -xorg -video- vmware zeitgeist -core
  zeitgeist - datahub zenity zenity -common
The following packages will be upgraded:
  acl acpi-support acpid adduser Aisleriot app- install-data -qt appmenu
  appmenu - apport - QT5 Symptoms apt apt -transport- https apt- utils
  apt- xapian -index aptdaemon -data at- SPI2 -core avahi -daemon avahi - autoipd
  avahi -utils base-files bc binfmt -support bleachbit bsdmainutils bsdutils
  busybox -static busybox -initramfs ca-certificates ca-certificates -java
  command-not -found command-not -found- date cpio cpp cracklib -runtime - 4.7
  crrcsim - date cryptsetup -bin browsed cups- cups -common cups- pk -helper
  PPDC - cups curl dbus -x11 dc dconf - gsettings -backend dconf -service debconf
  debconf -i18n debianutils default- jre default- jre- headless
  deja- dup - backends gvfs - desktop-file -utils dictionaries-common dialog diffstat
  dkms dmidecode dmsetup dmz -cursor -theme dnsmasq -base doc-base dosfstools
  dpkg e2fsprogs e2fslibs duplicity and enchant esound -common -data espeak
  example- content execstack fakeroot findutils firefox-locale -en
  firefox-locale - en fontconfig fontconfig -config fonts- droid
  Horai umefont - fonts- fonts- lao fonts- liberation - fonts- sinhala lklug
  fonts- nanum opensymbol fonts- fonts- sil - abyssinica fonts- sil - padauk
  PGothic fonts- takao - fonts- thai- tlwg fonts- fonts- tibetan -machine - tlwg garuda
  tlwg kinnari - fonts- fonts- tlwg loma - fonts- tlwg -mono - fonts- tlwg norasi
  tlwg purisa - fonts- fonts- tlwg sawasdee - typewriter - fonts- tlwg
  tlwg - fonts- fonts- typist typo tlwg - fonts- fonts- tlwg - umpush tlwg - Waree
  foomatic -db -compressed - ppds freeglut3 freerdp -x11 -facebook friends friends
  friends- twitter fslint merged gcc- 4.7 gcc- 4.7 -base geoclue
  geoclue - ubuntu- geoip geoip - database ghostscript ghostscript - x
  gir1.2 -accounts -1.0 gir1.2 - appindicator3 -0.1 gir1.2 - atk -1.0 gir1.2 - atspi -2.0
  dbusmenu - gir1.2 - glib -0.4 gir1.2 -dee -1.0 gir1.2 - freedesktop
  gir1.2 - GdkPixbuf -2.0 gir1.2 - glib -2.0 -3.0 gir1.2 - gmenu
  gir1.2 - gnomebluetooth -1.0 -1.0 gir1.2 - gnomekeyring
  gir1.2 - gst -plugins -base- 1.0 gir1.2 - gstreamer- 0:10 gir1.2 - gstreamer -1.0
  gir1.2 - gudev -1.0 gir1.2 - javascriptcoregtk -3.0 -1.0 gir1.2 - messagingmenu
  gir1.2 - networkmanager -1.0 gir1.2 -notify- 0.7 gir1.2 -peas -1.0
  gir1.2 - signon -1.0 gir1.2 -soup -2.4 gir1.2 - syncmenu -0.1 gir1.2 - totem -1.0
  gir1.2 - totem- plparser -1.0 gir1.2 - vte - 2.90 gir1.2 -webkit -3.0 glib- networking
  glib- networking -common glib- networking -services gnome- accessibility-themes
  gnome-bluetooth gnome- desktop3 - date gnome- icon-theme
  gnome- icon-theme - symbolic gnome- mahjongg gnome-menus gnome- power-manager
  gnome -screenshot gnome- sudoku gnome-terminal -data gnome- user-guide gnomine
  gparted gpgv gnupg grep groff- base grub -common grub -pc grub -pc- bin
  grub2 -common gsettings -desktop- schemas gstreamer0.10- gconf
  gstreamer0.10 -nice gstreamer0.10 -plugins -good gstreamer0.10- pulseaudio
  gstreamer0.10 - alsa -tools gstreamer1.0 gstreamer1.0 -nice
  gstreamer1.0 gstreamer1.0 -plugins- base -plugins- base -apps
  gstreamer1.0 - pulseaudio -tools gstreamer1.0 GTK3 - engines- only gzip
  hardening -includes hdparm hostname humanity - icon-theme hyphen -en -us icoutils
  im -config imagemagick imagemagick -common indicator -messages
  indicator- session info initramfs-tools initramfs -tools- bin initscripts
  inputattach insserv install-info iputils - arping iputils - tracepath irqbalance
  iso -codes jackd2 jackd2 firewire - java-common klibc -utils krb5 -locales
  landscape -client- ui -install language- pack -en language- pack -en- base
  language- pack -gnome -en language- pack -gnome -en- base language -pack- gnome- en
  language -pack- gnome- en -base language -pack- en language -pack- en -base
  language- selector - common language -selector -gnome less libaa1 libaacs0
  libaccounts - glib0 libaccounts - Qt1 libacl1 libappindicator1
  libappindicator3 -1 libapr1 libaprutil1 libapt - inst1.5 libapt -pkg -perl
  libapt - pkg4.12 libarchive -zip- perl libasn1 -8- heimdal libasound2 -plugins
  libass4 libasyncns0 libatasmart4 libatk - adapter - libatk bridge2.0 -0
  libatk1.0 -0 libatk1.0 -data libatkmm -1.6 -1 -0 libatspi2.0 libattr1 libaudio2
  libaudiofile1 libavahi - client3 libavahi -common -data libavahi - common3
  libavahi - Core7 libavahi - glib1 libavahi - gobject0 libavcodec53 libavformat53
  libavutil51 libbit -vector -perl libblkid1 libbonobo2 -0 libbonobo2 -common
  libboost -date- time1.49.0 libboost - thread1.49.0 libbsd0 libburn4 libc- bin
  libc -dev- bin libc6 libc6 -dev - gobject2 libcaca0 libcairo libcairo -perl
  libcairo2 - libcap - cdda1 ng0 libcdio libcdio - paranoia1 libcdio13 libcdr -0.0 -0
  libchromaprint0 libclass libclass -c3 -perl -data- inheritable -perl
  libclone -perl - libcloog ppl1 libclucene - contribs1 libclucene - Core1
  libclutter -1.0 -common -common libcogl libcogl12 libcolorhug1 libcrack2
  libcroco3 libcrypt - openssl- bignum -perl libcurl3 libcryptsetup4
  libcurl3 - gnutls libdatrie1 libdb5.1 libdbus -1-3 - libdbusmenu glib4
  libdbusmenu - QT2 libdbusmenu - QT5 libdca0 libdconf1 libdee -1.0 -4
  libdevmapper - event1.02.1 libdevmapper1.02.1 libdjvulibre -text libdjvulibre21
  libdmapsharing -3.0 -2 libdpkg -perl - intel1 libdrm libdrm - nouveau2
  libdrm - radeon1 libdrm2 libdvdnav4 libdvdread4 libedit2 libelf1 libenca0
  libenchant1c2a libesd0 libespeak1 libevent -2.0 -5 -12 libexempi3 libexiv2
  libexttextcat libexpat1 -2.0 -0 - libexttextcat date libextutils - pkgconfig -perl
  libfarstream -0.1 - 0 -0.2 -2 libfarstream libffi6 libfftw3 -3 - libfftw3 double3
  libfftw3 - single3 mimeinfo -perl libfile - libflac8 libflite1 libfm - date
  libfm -gtk - date libfontconfig1 libfontembed1 libfontenc1 libframe6
  libfreerdp -plugins- standard libfreerdp1 libfribidi0 libfriends0 libfs6
  libftgl2 libfuse2 libgck libgcc - 4.7 -dev -1-0 -3 -common libgcrypt11 libgcr
  libgdata -common libgdbm3 libgdk - pixbuf2.0 -0 libgdk - pixbuf2.0 -common libgee2
  libgeis1 libgeoclue0 libgeoip1 libgexiv2 libgirepository -2 -1.0- 1 -0 libgksu2
  libglew1.8 libglewmx1.8 libglib -perl libglib2.0 -0 libglib2.0 -bin
  libglibmm libglib2.0 -data -2.4- 1c2a libglu1 - mesa -2.6 -0 libgmime libgmp10
  libgmpxx4ldbl - bluetooth11 libgnome libgnome -keyring -common libgnome - keyring0
  libgnome -menu- 3-0 libgnomevfs2 -0 libgnomevfs2 -common libgnomevfs2 -extra
  libgnutls26 libgpg - error0 libgphoto2 -l10n libgpm2 libgrail6 libgrip0 libgs9
  libgs9 libgssapi3 -common - 1.0 -3 - heimdal libgssdp
  libgstreamer -plugins- base1.0 libgstreamer0.10 -0 -0 -0 libgstreamer1.0
  libgtk2 -perl libgtk2.0 -common -2.4- 1c2a libgtkmm libgudev -1.0 -0
  libgupnp -1.0 -4 libgupnp - igd -1.0 -4 -common libgutenprint2 libgweather
  libhcrypto4 - libheimbase1 - heimdal heimdal heimdal - libheimntlm0
  libhtml -parser -perl libhx509 -5- heimdal libhyphen0 libicu48 libidn11
  libieee1284 libindicator3 -3 -7 - libindicator7 libisofs6 libjack jackd2 - 0
  libjpeg - turbo8 libjpeg8 libjson libjson -perl - xs -perl libjte1 libkeyutils1
  libklibc libkpathsea6 libkrb5 -26- heimdal liblangtag -common liblangtag1
  liblastfm1 liblcms1 liblcms2 -2 libldap -2.4 -2 liblightdm - gobject -1-0
  libllvm3.2 liblockfile -bin liblockfile1 liblouis - date liblouis2 libltdl7
  liblua5.1 -0 liblvm2app2.2 liblwp -protocol - https -perl liblzo2 -2
  libmagickcore5 libmagickwand5 libmeanwhile1 libmessaging - menu0 libmhash2
  libmission -control- plugins0 libmms0 libmodplug1 - cil libmono - accessibility2.0
  libmono - corlib2.0 - cil libmono - corlib4.0 - cil libmono -data- tds2.0 - cyl
  libmono -i18n- west2.0 - cil libmono -i18n- west4.0 - cil libmono - cil - i18n4.0
  libmono - cil libmono - messaging2.0 - posix2.0 - cil libmono - cil - security2.0
  libmono - cil libmono - security4.0 - sharpzip2.84 - cil libmono - cil - sqlite2.0
  libmono -system- configuration4.0 - cil libmono -system- data- linq2.0 - cyl
  libmono -system- data2.0 - cil libmono -system- messaging2.0 - cyl
  libmono -system- security4.0 - cil libmono -system- web2.0 - cil
  libmono -system- xml4.0 - cil libmono - system2.0 - cil libmono - system4.0 - cil
  libmono - cil libmono - wcf3.0 - webbrowser2.0 - cil libmono - cil - winforms2.0
  libmono2.0 - cyl libmount1 libmouse -perl libmpfr4 libmpg123 libmspub -0.0 -0 -0
  libmtdev1 libmtp -common libmtp -runtime -1.2 -0 libmtp9 libmythes
  libnautilus extension1a libncurses5 - libncursesw5 libnet -dns -perl
  libnet - dropbox -api -perl libnet -http -perl libnet - SSLeay perl - libnettle4
  libnewt0.52 libnfnetlink0 libnice10 libnm - glib libnm - vpn1 - glib4
  libnm -gtk -common libnm - gtk0 libnm - util2 libnotify -bin libnotify4 libnss - mdns
  libnss3 libnss3 - 1d libnuma1 liboauth0 libogg0 libopencc1 libopenobex1
  libopenvg1 libopus0 liborbit2 liborc - mesa -0.4 -0 libp11 -kit- gnome -keyring
  libp11 - kit0 libpam- freerdp libpam -gnome -keyring libpam -modules
  libpam -modules- bin libpam -runtime libpam0g libparted0debian1
  libpath -class- perl libpcap0.8 libpci3 libpciaccess0 libpeas -1.0 -0
  libpeas libperl5.14 libphysfs1 libpipeline1 -common libpixman -1-0 libpng12 -0
  libpolkit -agent -1-0 - c4 libpostproc52 libppl libppl12
  libproc - processtable -perl libprocps0 libprotobuf - lite7 libprotobuf7
  libprotoc7 libproxy1 libproxy1 -plugin- gsettings
  libproxy1 -plugin- networkmanager libpth20 libpulse - mainloop - glib0 libpulsedsp
  libpython - stdlib libpython2.7 libpython2.7 -minimal libpython2.7 - stdlib
  libpython3.3 libpython3.3 -minimal libpython3.3 - stdlib libqjson0 libqpdf10
  libqt4 -dbus libqt4 - declarative libqt4 -designer libqt4 -help libqt4 -network
  libqt4 - opengl libqt4 -script libqt4 - scripttools libqt4 -sql libqt4 -sql - sqlite
  libqt4 - svg libqt4 -test libqt4 -xml libqt4 - xmlpatterns libqtassistantclient4
  libqtcore4 libqtgui4 libqtwebkit4 libquvi -scripts libraptor2 -0 librasqal3
  libraw1394 -11 - heimdal libreadline5 libroken18 librsvg2 -2 librsvg2 -common
  librsync1 librtmp0 libsamplerate0 libsbc1 libsasl2 -modules -0 libsdl - ttf2.0
  libsdl1.2debian - libsecret 1-0 libsecret -common libselinux1
  libsemanage -common libsemanage1 libsensors4 libsepol1 libserd - 0-0 libserf1
  libsgutils2 -2 libshout3 libsidplay1 libsigc + + -2.0- 0c2a - libsignon glib1
  libsignon - Qt1 libsndfile1 libsord - 0-0 libsoundtouch0 libsoup - gnome2.4 - 1
  libsoup2.4 - 1 libspandsp2 libspeechd2 libspeex1 libspeexdsp1 libsqlite3 - 0
  libsratom - 0-0 libss2 libssh -4 - libstartup notification0 libsuil - 0-0 libsvn1
  libswscale2 libsync - menu1 libsysfs2 libsystemd - daemon0 libtag1 -vanilla
  libtag1c2a libtalloc2 libtasn1 -3 - libtdb1 libtelepathy glib0
  libtelepathy - logger3 libthai - date libthai0 libtie - IxHash -perl libtiff4
  libtiff5 libtimezonemap1 libtinfo5 libtotem - plparser17 libtotem0 libudev1
  libudisks2 - 0 - libufe xidgetter0 libunistring0 libunity - misc4 libupower - glib1
  libusb -0.1 -4 libusb -1.0 -0 -0 libv4l libuuid1 libv4lconvert0 libva1
  libvamp - hostsdk3 libvamp - sdk2 libvdpau1 libvisio -0.0 -0 libvpx1
  libwacom libwacom2 libwebkitgtk -common -3.0 -common libwhoopsie0
  libwind0 - heimdal libwnck -3 -common libwpd libwnck -common -0.9 -9 -0.2 -2 libwpg
  libwps -0.2 -2 -0 libwxbase2.8 libwww -perl libx11 -data libx11 - xcb1 libx264 -123
  libxapian22 libxatracker1 libXaw7 libxcb - dri2 -0 libxcb - glx0 libxcb - render0
  libxcb - shape0 libxcb - shm0 libxcb - xfixes0 libxcomposite1 libxcursor1
  libxdamage1 libxext6 libxfont1 libxinerama1 libxkbcommon0 libxml + +2.6-2
  libxp6 libxml2 libxrandr2 libxrender1 libxt6 libxres1 libxslt1.1 libxtst6
  libxv1 libxvidcore4 libxvmc1 libxxf86dga1 libxxf86vm1 libyajl2
  libyaml -tiny -perl libyelp0 libzbar0 libzephyr4 light -themes lightdm
  linux- firmware linux- libc -dev localepurge login lsb -base lsb -release lshw
  make makedev man-db manpages manpages- dev media-player -info memtest86 +
  mesa- utils mime-support -installer minecraft mlocate
  mobile- broadband -provider- info modemmanager mono -4.0- gac mono- gac
  mono -runtime mount mountall mscompress mtools mtr -tiny multiarch -support
  myspell -en -au nautilus -share ncurses -base ncurses -bin net-tools netbase
  network-manager -gnome network-manager - pptp network-manager - pptp -gnome
  ntfs -3g ntpdate obexd nux -tools -client -common oneconf oneconf
  openoffice.org- hyphenation - ppds OpenPrinting openssh-client openssl
  os -prober - overlay overlay - scrollbar scrollbar- gtk2 overlay - scrollbar- GTK3
  patchutils parted passwd patch pciutils perl perl-base perl -modules
  PerlMagick pkg -config plymouth -theme- ubuntu- logo plymouth -theme- ubuntu -text
  policykit -desktop -privileges poppler -data popularity-contest prelink
  c2esp printer- driver - printer- driver - foo2zjs printer- driver - gutenprint
  pnm2ppa printer- driver - printer- driver - ptouch printer- driver - pxljr
  printer- driver - splix procps protobuf -compiler pulseaudio -module- bluetooth
  pulseaudio -module- x11 pulseaudio -utils python python- apt python- AppIndicator
  python- apt -common python- aptdaemon python- aptdaemon.gtk3widgets
  configglue python- python- crypto python -cups python- dbus python- cupshelpers
  dbus- python- dev python- dirspec python- gconf python -gi python -gi- cairo
  gnomekeyring python- python- gobject python- gobject -2 python- httplib2
  python- imaging python- imaging -compat python- libxml2 python- lxml python- mako
  python -minimal python- oauthlib oneconf python- python- openssl python- pam
  python- pkg -resources python- protobuf python- qt4 python- pyinotify
  python- qt4 -dbus python -sip python -six python- twisted python- twisted- bin
  python- twisted- conch python- twisted- core python- twisted- lore
  python- twisted -mail python- twisted -names python- twisted -news
  python- twisted- runner python- twisted- web python- twisted- words
  python- ubuntu- sso- client python- python- wxgtk2.8 wxversion python- xapian
  python- xdg python- zeitgeist python- zope.interface python2.7
  python2.7 -minimal python3 python3 - cairo python3 -apt - commandnotfound
  python3 python3 -crypto -dbus - httplib2 python3 python3 python3 - lxml -louis
  python3 python3 - oauthlib - oneconf python3 python3 -pkg -resources - pyatspi
  python3 -six - speechd python3 python3 - update-manager - xdg python3.3 python3
  python3.3 -minimal qdbus qjackctl qpdf qt- at-spi qtchooser rar remmina
  remmina remmina -common -plugin- rdp remmina rhythmbox -plugin- vnc - date rsync
  rsyslog rtkit sane- utils sed sensible- utils shared-mime -info shutter
  simple- scan software - center software -center- aptdaemon -plugins
  sound -theme- freedesktop speech-dispatcher ssh- askpass -gnome ssl -cert strace
  syslinux syslinux -common system-config -printer -common
  system-config -printer- gnome system-config -printer- udev - systemd services
  shim systemd - sysv -rc sysvinit -utils tar tcpdump t1utils telepathy- gabble
  telepathy -idle telepathy- logger telepathy- indicator
  telepathy- mission -control- 5 totem totem -common totem -mozilla totem -plugins
  transmission -common ttf- ubuntu- font-family tzdata tzdata -java ubuntu -artwork
  ubuntu- docs ubuntu -drivers -common ubuntu ubuntu -mono -settings
  ubuntu- sso- client ubuntu- standard ubuntu -system- service
  ubuntu- wallpapers- raring ucf udev udisks udisks2 ufw unattended-upgrades
  unity- asset- pool unity- webapps -service unzip update-manager
  update- manager-core usb-creator -common usb-creator -gtk usbutils util -linux
  uuid -runtime vim -common vim -tiny webaccounts wine -extension -common wget
  whiptail whoopsie wine wine - mono0.0.8 wine1.5 wpasupplicant wireless - regdb
  x11 -apps x11-common x11 -session- utils x11- utils x11- xfs -utils x11- xkb -utils
  x11- xserver- utils xdg -user- dirs xdg -user- dirs -gtk xfonts -utils xkb-data xorg
  xorg -docs -core xserver-common xserver -xorg xserver- xorg-input -all
  xserver -xorg- video -all xterm xul -ext- ubufox xul -ext -websites -integration
  yelp yelp -xsl zip zeitgeist
984 upgraded, 0 newly installed, 0 to remove and 364 not upgraded.
sOnly kB/406 need to download 255 MB of archives.
After this operation, will be occupied 21.3 MB of disk space .
Continue [Y / n] ? s
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) saucy-updates/main libprocps0 i386 1:3.3.3 - 2ubuntu8
  404 Not Found [IP : 193.206.139.45 80]
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) saucy-updates/main procps i386 1:3.3.3 - 2ubuntu8
  404 Not Found [IP : 193.206.139.45 80]
Unable  to retrieve  [http://it.archive.ubuntu.com/ubuntu/pool/main/p/procps/libprocps0_3.3.3-2ubuntu8_i386.deb](http://it.archive.ubuntu.com/ubuntu/pool/main/p/procps/libprocps0_3.3.3-2ubuntu8_i386.deb)  404 Not Found [IP : 193.206.139.45 80]
Unable  to retrieve  [http://it.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.3.3-2ubuntu8_i386.deb](http://it.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.3.3-2ubuntu8_i386.deb)  404 Not Found [IP : 193.206.139.45 80]
E: Unable to download some packages . It might be useful to run "apt -get update " or try the option " - fix- missing" .
robert @ robert- 1015BX 1015BX - : ~ $

---

### Post by ian-weisser on 2013-11-27
That's progress!
984 packages? You have had this problem for some time.

[B]
1) Disable *all* your PPAs.[/B]

Do the command **software-properties-gtk** . It will bring up the Software Sources control panel.
Disable (uncheck) all PPAs and other non-Ubuntu software.
Close the control panel.

Many of those 404-not-found errors are from old PPAs.


**2) Update your package index.**

Do the command [B]sudo apt-get update

[/B]Look for the warning "W: Some index files failed to download they have been ignored , or old ones will be used ."

If you get that warning, do the command again.
If you get that warning again, stop and post the output here.



**3) Upgrade the Ubuntu packages on your system**

Do the command [B]sudo apt-get upgrade
[/B]This may take 20-30 minutes. Do not interrupt it.
If you get any error messages, stop and post the output here.[B]




4) Upgrade your Ubuntu kernel packages on your system[/B]

Do the command **sudo apt-get dist-upgrade**
This may take a few minutes. Do not interrupt it.
If you get any error messages, stop and post the output here.[B]



5) Re-enable your PPAs[/B]

Do the command **software-properties-gtk** . It will bring up the Software Sources control panel.
Enable (check) *only* the PPAs that you still want to use.
Remember that PPAs are not community-supported software, may not be maintained to Ubuntu repository standards, and are not tested for stability with Ubuntu.
Close the control panel.



**6) Update your package index again**

Do the command [B]sudo apt-get update

[/B]Look for 404 warnings.
Disable all PPAs that return a 404 warning. That PPA is no longer valid.

Redo the command, and keep eliminating PPAs, until you do not receive the final warning "W: Some index files failed to download they have been ignored , or old ones will be used ."
If you don't do this, you may break your system again.

If you need help, post the output here.



**7) Upgrade the PPA packages on your system**

Do the command [B]sudo apt-get upgrade
[/B]If you get any error messages, stop and post the output here.

---

### Post by fantab on 2013-11-27
Also remove all those 'raring' sources in the /etc/apt/sources.list.

---

### Post by robiitb on 2013-11-27
ther are output 

```
Found [http://archive.canonical.com](http://archive.canonical.com) saucy / partner i386 Packages
Found [http://archive.getdeb.net](http://archive.getdeb.net) raring - getdeb Release
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release
  
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Sources
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release
Downloading : 5 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg [ 316 B]
Downloading : 6 [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg [ 316 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Sources
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Sources
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Sources
Saucy Release.gpg Ign [http://ppa.launchpad.net](http://ppa.launchpad.net)
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main i386 Packages
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe i386 Packages
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy / main Translation- en
Release Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en
Downloading : 7 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources [ 12.5 kB ]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en_US
Release Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / universe Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release
Found [http://archive.getdeb.net](http://archive.getdeb.net) raring-getdeb/games i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy / partner Translation- en
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / main Sources
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en
Downloading : 8 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release [ 11.9 kB ]
Downloading : 9 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources [14 B]
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / restricted Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main Sources
Download : 10 [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release [ 9745 B]
Downloading : 11 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources [ 6871 B]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted Sources
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / multiverse Sources
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe Sources
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse Sources
Downloading : 12 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources [ 688 B]
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main i386 Packages
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / universe i386 Packages
Release Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted i386 Packages
Downloading : 13 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages [ 39.3 kB ]
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe i386 Packages
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse i386 Packages
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / main i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main Translation- en
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / restricted i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse Translation- en
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / multiverse i386 Packages
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted Translation- en
Downloading : 14 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / main Translation- en
Found [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages
Downloading : 15 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages [ 17.0 kB ]
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / main Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / multiverse Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
Downloading : 16 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages [ 1389 B]
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main i386 Packages
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / multiverse Translation- en
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation- en
Translation- en_US Ign [http://archive.getdeb.net](http://archive.getdeb.net) raring-getdeb/games
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / restricted Translation- en
Translation- en Ign [http://archive.getdeb.net](http://archive.getdeb.net) raring-getdeb/games
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / main Translation- en_US
Translation- en Ign [http://archive.getdeb.net](http://archive.getdeb.net) raring-getdeb/games
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / multiverse Translation- en_US
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / restricted Translation- en
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / restricted Translation- en_US
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation- en
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy / universe Translation- en_US
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/main
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/multiverse
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/restricted
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / universe Translation- en
Downloading : 17 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages [ 8610 B]
Translation- en_US Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe
Translation- en Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy-backports/universe
Found [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / universe Translation- en
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation- en
Downloading : 18 [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources [ 17.8 kB ]
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages
Found [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation- en
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
Found [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / main Translation- en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / multiverse Translation- en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / restricted Translation- en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring / universe Translation- en_US
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted
Translation- en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe
Translation- en Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages
  404 Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Sources
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages
  404 Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main i386 Packages
  404 Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy / main Translation- en
Recovered 178 kB in 16s (11.1 kB / s)
Reading package lists ... fact
W : There was an error in verifying the signature . The repository is not updated and the previous index files will be used . GPG  error : [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release: The  Following signatures were invalid : BADSIG 40976EAF437D05B5 Ubuntu  Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

---

### Post by ian-weisser on 2013-11-27
Seems like you skipped step 1.
Do the steps in the correct order.

---

### Post by fantab on 2013-11-27
> W : There was an error in verifying the signature . The repository is not updated and the previous index files will be used . GPG  error : [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) saucy -updates Release: The  Following signatures were invalid : BADSIG 40976EAF437D05B5 Ubuntu  Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update && sudo apt-get dist-upgrade
```

But first, like I said earlier, remove all those 'raring' repos from /etc/apt/sources.list

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo gedit /etc/apt/sources.list
```
Select and delete all lines which mention 'raring' compltely. Then save the file and only then run 'update'.

---

### Post by robiitb on 2013-12-01
thanke you

---

