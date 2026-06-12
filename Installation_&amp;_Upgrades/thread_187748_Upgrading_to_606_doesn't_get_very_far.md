---
title: "Upgrading to 606 doesn't get very far"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by punkybouy on 2006-06-03
Using the Update Manager I barely get into an upgrade. It starts to collect informatioin and then I get the following errors:

Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found
Any ideas?  Thanks for your help

---

### Post by John.Michael.Kane on 2006-06-03
punkybouy are you trying to upgrade to dapper from brezzy? if you are you need to change  you source.list

```
[B]1) sudo gedit /etc/apt/sources.list
2) copy paste this 
[/B]
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse 

[B]3)sudo apt-get update
4)sudo apt-get dist-upgrade
```[/B]

Hope this helps..

---

### Post by punkybouy on 2006-06-03
Thanks for the quick reply.  Do you want me to replace my sources.list with one that only contains what you posted or do I add your post to what I already have?

---

### Post by John.Michael.Kane on 2006-06-03
punkybouy yes replace your source.list with the one posted.

---

### Post by punkybouy on 2006-06-03
Thanks for your help.  Sorry for the delay in responding but I was upgrading.  Here is what happened.  I replaced my sources file with yours and ran the commands you posted.  About 650 MB of files were downloaded (took about an hour) and at the end of the download there were some messages indicating that not all the files were downloaded.  Shortly after that up on the taskbar the red ball appeared indicating there were updates available.  Opening the update tool showed me there were hundreds of updates available but some programs would not be updated.  Abiword was the only one I noticed but there were many many others not on the list for updates.  Also in the update manager window there was a button to Upgrade to 6.06 I clicked the button and after some analysis of my system I was told  I needed another 74MB of files.  I went ahead and upgraded from there and that took another hour.  The system rebooted just fine although Mozilla ( I like it better than Firefox) was gone.  I was able to reinstall Mozilla without any issues and my bookmarks were there as well.  I haven't checked out much else yet but everything appears in order.  Thanks again!

---

### Post by punkybouy on 2006-06-03
Now if they would just come out with an updated version of Flash Player.

---

### Post by John.Michael.Kane on 2006-06-03
punkybouy I'm glad it worked for you. enjoy your time with ubuntu. please post if you have any more problems.

---

