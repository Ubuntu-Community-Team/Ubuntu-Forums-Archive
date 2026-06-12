---
title: "Media Change: Please insert the disc labelled"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by coolboarderguy on 2008-04-04
Hi All,

why am I getting prompted for a CD every time I try to install a new app? I didn't use a CD to upgrade. Confused.

Media Change: Please insert the disc labelled
 ‘Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)’
in the drive ‘/cdrom/’ and press enter

---

### Post by mizar001 on 2008-04-04
Hi. You must go to System->Administration->Software Source 

Here you have an option where to select/deselct the media(cdrom/dvd) repository from being detected when you want an update.

---

### Post by zvacet on 2008-04-04
In terminal

```
gksudo gedit /etc/apt/sources.list
```

Put # in front of line deb cdrom

Save file and close it.

```
sudo apt-get update
```

---

### Post by coolboarderguy on 2008-04-04
Hi All,

thanx for that. What do you make of this?

p:~$ sudo apt-get install talk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  openbsd-inetd
Suggested packages:
  talkd
The following packages will be REMOVED
  netkit-inetd
The following NEW packages will be installed
  openbsd-inetd talk
0 upgraded, 2 newly installed, 1 to remove and 81 not upgraded.
1 not fully installed or removed.
Need to get 56.3kB of archives.
After unpacking 69.6kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main openbsd-inetd 0.20050402-3 [34.7kB]
Get: 2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/universe talk 0.17-11ubuntu1 [21.6kB]
Fetched 34.7kB in 27s (1244B/s)
(Reading database ... ^[166947 files and directories currently installed.)
Removing netkit-inetd ...
 * Stopping internet superserver...                                                                                                                   [ OK ] 
Selecting previously deselected package openbsd-inetd.
(Reading database ... 166939 files and directories currently installed.)
Unpacking openbsd-inetd (from .../openbsd-inetd_0.20050402-3_i386.deb) ...
Selecting previously deselected package talk.
Unpacking talk (from .../talk_0.17-11ubuntu1_i386.deb) ...
Setting up openbsd-inetd (0.20050402-3) ...
 * Starting internet superserver inetd                                                                                                                [ OK ] 

Setting up vmware-server (1.0.4-1feisty3) ...
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-server, action "start" failed.
dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Setting up talk (0.17-11ubuntu1) ...

Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can I confirm my suspicion that perhaps vmware is not properly installed, hence the related error? Really lost on this one.

---

### Post by zvacet on 2008-04-04
> Can I confirm my suspicion that perhaps vmware is not properly installed, hence the related error?

Yes,that is what the message is telling you.

---

