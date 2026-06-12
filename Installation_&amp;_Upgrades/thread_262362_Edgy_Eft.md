---
title: "Edgy Eft"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by Old Pink on 2006-09-21
Hi, 

I realise Edgy Eft will be available in October, just over a week away now, anticipation is rising, but I have a few questions:
[LIST=1]
[*]Will Ubuntu update to Edgy Eft smoothly without having to re-install etc?
[*]Is upgrading like this done with sudo apt-get update?
[*]What will I risk losing? (e.g drivers, etc)[/LIST]

---

### Post by Tuxman on 2006-09-21
Yeah, I'm also interested in this. I just installed Ubuntu 6.06 on my laptop, and I hope that the upgrade will be to complicated.

---

### Post by skymt on 2006-09-21
> **Matt.H said:**
> Hi, 

I realise Edgy Eft will be available in October, just over a week away now, anticipation is rising, but I have a few questions:
[LIST=1]
[*]Will Ubuntu update to Edgy Eft smoothly without having to re-install etc?
[*]Is upgrading like this done with sudo apt-get update?
[*]What will I risk losing? (e.g drivers, etc)[/LIST]

* It should. It doesn't always, but as long as you haven't done anything too crazy, it should work fairly well.
* I use:```
sudo aptitude update && sudo aptitude dist-upgrade
```aptitude has much better dependency handling than apt-get.
* You *risk* losing everything, but that's a small risk. Just back up. You aren't likely to lose anything, again, as long as you haven't changed it too far from stock Dapper.

---

### Post by kauf on 2006-09-21
I hope Edgy will work on my comp... [dapper hates me]("http://www.ubuntuforums.org/showthread.php?t=261678").

F-you dapper... f-you

---

### Post by wilcal on 2006-09-22
When I went from Ubuntu Breezy 5.10 to 6.06 Dapper
I fed my hard disk a good dose of this first from
first sector to last:

[http://www.killdisk.com](http://www.killdisk.com)

then this

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Then I installed 6.06, I'll do the same when I move
from 6.06 -> 6.10 Edgy Eft.

---

### Post by randell6564 on 2006-09-22
> **skymt said:**
> * It should. It doesn't always, but as long as you haven't done anything too crazy, it should work fairly well.
* I use:```
sudo aptitude update && sudo aptitude dist-upgrade
```aptitude has much better dependency handling than apt-get.
* You *risk* losing everything, but that's a small risk. Just back up. You aren't likely to lose anything, again, as long as you haven't changed it too far from stock Dapper.
Ok, I JUST did this upgrade command and I ended up with the following:

[B]bigboss@bigboss-desktop:~$ sudo aptitude update && sudo aptitude dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 60B in 2s (21B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.



[/B]
So.,I did not get to upgrade to 'Edgy'.  Any suggestions?

---

### Post by skymt on 2006-09-22
Sorry, I should have clarified. Just running that command won't do it. You need to change all instances of "dapper" to "edgy" in "/etc/apt/sources.list" before running that command. Otherwise, aptitude thinks you want to upgrade to dapper.

---

### Post by Dinerty on 2006-09-22
> **randell6564 said:**
> Ok, I JUST did this upgrade command and I ended up with the following:

[B]bigboss@bigboss-desktop:~$ sudo aptitude update && sudo aptitude dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 60B in 2s (21B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.



[/B]
So.,I did not get to upgrade to 'Edgy'.  Any suggestions?

It's important that you know Edgy is currently not finished and ready for general public release, if you have only the one system and want to see Edgy, then download the LiveCD and just run it that way.

If you install it now your system may crash and lose valuable data

---

### Post by randell6564 on 2006-09-22
> **skymt said:**
> Sorry, I should have clarified. Just running that command won't do it. You need to change all instances of "dapper" to "edgy" in "/etc/apt/sources.list" before running that command. Otherwise, aptitude thinks you want to upgrade to dapper.

Thats right! Duh! Forgot about my sources.list!

---

