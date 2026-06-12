---
title: "Upgrade Breezy to Edgy"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by gravediggers on 2006-12-03
I have not been  keeping up with the new releases, and decided to go from Breezy to Edgy (Kubuntu). Now I did read the Edgy upgrade, and it said you can only upgrade to edgy from Dapper. Ok so used the community DapperUpgrages guide and did the Dapper upgrade. I didn't have the update manager installed, so I used the step that said
```
sudo apt-get udate && sudo apt-get dist-upgrade
```I got some errors
```
      gravediggers@gandalf:~$ sudo apt-get update && sudo apt-get dist-upgrade
Ign http://wine.sourceforge.net binary/ Release.gpg
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://wine.sourceforge.net binary/ Release
Ign http://ubuntu-backports.mirrormax.net dapper-extras Release.gpg
Get:4 http://security.ubuntu.com dapper-security Release [30.9kB]
Get:5 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Ign http://ubuntu-backports.mirrormax.net dapper-extras Release
Get:6 http://archive.ubuntu.com dapper Release [34.8kB]
Ign http://wine.sourceforge.net binary/ Packages
Ign http://ubuntu-backports.mirrormax.net dapper-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net dapper-extras/restricted Packages
Ign http://ubuntu-backports.mirrormax.net dapper-extras/universe Packages
Hit http://wine.sourceforge.net binary/ Packages
Ign http://ubuntu-backports.mirrormax.net dapper-extras/multiverse Packages
Err http://ubuntu-backports.mirrormax.net dapper-extras/main Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net dapper-extras/restricted Packages
  404 Not Found
Get:7 http://archive.ubuntu.com dapper-updates Release [30.9kB]
Err http://ubuntu-backports.mirrormax.net dapper-extras/universe Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net dapper-extras/multiverse Packages
  404 Not Found
Get:8 http://security.ubuntu.com dapper-security/main Packages [81.2kB]
Get:9 http://archive.ubuntu.com dapper-backports Release [23.3kB]
Get:10 ftp://ftp.free.fr dapper Release.gpg
Get:11 http://archive.ubuntu.com dapper/main Sources [255kB]
Get:12 http://security.ubuntu.com dapper-security/restricted Packages [6460B]
Get:13 http://security.ubuntu.com dapper-security/main Sources [15.7kB]
Ign ftp://ftp.free.fr dapper Release.gpg
Get:14 http://deb.opera.com etch Release.gpg [189B]
Get:15 http://security.ubuntu.com dapper-security/restricted Sources [968B]
Get:16 http://security.ubuntu.com dapper-security/universe Packages [43.0kB]
Get:17 http://archive.ubuntu.com dapper/restricted Sources [1478B]
Get:18 http://archive.ubuntu.com dapper/universe Sources [975kB]
Hit http://deb.opera.com etch Release
Ign http://deb.opera.com etch Release
Get:19 ftp://ftp.free.fr dapper Release
Get:20 http://security.ubuntu.com dapper-security/universe Sources [5421B]
Ign ftp://ftp.free.fr dapper Release
Get:21 ftp://ftp.free.fr dapper/free Packages
Ign http://deb.opera.com etch/non-free Packages
Hit http://deb.opera.com etch/non-free Packages
Ign ftp://ftp.free.fr dapper/free Packages
Get:22 ftp://ftp.free.fr dapper/non-free Packages
Ign ftp://ftp.free.fr dapper/non-free Packages
Get:23 ftp://ftp.free.fr dapper/free Sources
Ign ftp://ftp.free.fr dapper/free Sources
Get:24 ftp://ftp.free.fr dapper/non-free Sources
Ign ftp://ftp.free.fr dapper/non-free Sources
Get:25 ftp://ftp.free.fr dapper/free Packages
Err ftp://ftp.free.fr dapper/free Packages
  Unable to fetch file, server said 'Failed to open file.  '
Get:26 ftp://ftp.free.fr dapper/non-free Packages
Get:27 http://archive.ubuntu.com dapper/universe Packages [2458kB]
Err ftp://ftp.free.fr dapper/non-free Packages
  Unable to fetch file, server said 'Failed to open file.  '
Get:28 ftp://ftp.free.fr dapper/free Sources
Err ftp://ftp.free.fr dapper/free Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:29 ftp://ftp.free.fr dapper/non-free Sources
Err ftp://ftp.free.fr dapper/non-free Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:30 http://archive.ubuntu.com dapper/main Packages [619kB]
Get:31 http://archive.ubuntu.com dapper/restricted Packages [4571B]
Get:32 http://archive.ubuntu.com dapper/multiverse Packages [95.2kB]
Get:33 http://archive.ubuntu.com dapper-updates/main Packages [129kB]
Get:34 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:35 http://archive.ubuntu.com dapper-updates/main Sources [47.9kB]
Get:36 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:37 http://archive.ubuntu.com dapper-backports/main Packages [12.3kB]
Get:38 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:39 http://archive.ubuntu.com dapper-backports/universe Packages [41.4kB]
Get:40 http://archive.ubuntu.com dapper-backports/multiverse Packages [2508B]
Fetched 4915kB in 1m40s (48.8kB/s)
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/dapper-extras/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/dapper-extras/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/dapper-extras/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/dapper-extras/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '
Reading package lists... Done
W: GPG error: http://deb.opera.com etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
gravediggers@gandalf:~$                                   
```and I don't know if any of these were important.
My sources.list was originally the clean one for Breezy as posted by on the psycocats site, but I thhink it got a couple of extra entries after I ran Automatix earlier this year, which may explain the errors.

Anyway, I have now rebooted, and am trying to determine if the upgrade was successful. Am I now fully Dapper, or half Dapper and half Breezy. How do I tell?
Do I now proceed to the Edgy upgrade , or do I go back to Breezy?
Any help appreciated?

(Note: My linux is a bit rusty as I haven't kept up in the past 10 months!)

---

### Post by Sef on 2006-12-03
> You may want to run apt-get update to correct these problems

Have you run that command?

---

### Post by gravediggers on 2006-12-03
I take it that your comment is with reference to the GPG error message. The answer is no, I haven't run a subsequent apt-get update. As I got heaps of error mesages during the upgrade, I didn't want to do anything else until I was sure that I was successfully upgraded to Dapper (in case I needed to go back to Breezy).
[LIST=1]
[*]So, is it safe to do apt-get update at this point, and what exactly is it going to do for me?
[*]Do I ignore all of the other errors , other than the GPG error message at the end?
[*]How do I know if I am fully upgraded to Dapper? Is there a file or two that I can check, or a command that I run?
[*]If I am correctly upgraded, then is there anything else I need to consider before taking the next step of going to edgy.
[*]The update-manager package does not appear to be part of the standard Kubuntu build (for Breezy, anyway). Is thas the only package that I need to install so that I can use the official upgrade method to go to Edgy?[/LIST]

---

### Post by Shay Stephens on 2006-12-03
I had no success in upgrading.  And I don't hold out any hope it will work for you either.  I would seriously consider doing a fresh install of edgy.  Backup your data while you have a chance if not already done.

---

### Post by gravediggers on 2006-12-04
Ok Shay, each to their own - it just seems a bit defeatest to me!

Did the 'sudo apt-get update' as Sef suggested, but got all the same (or similar errors). Should I change my sources.list to the standard Dapper one and the try again, or should I back out?
How do I actually tell what release I'm at?:-?

---

### Post by Shay Stephens on 2006-12-04
It's not defeatist, it is realistic.  Scan the forums for people who have upgraded, the vast majority, who by the way started with a working dapper install, had problems, including myself.  You, starting with a broken install of dapper, you have no chance hehehe.  You would save time, effort, and aggravation by just doing a clean install of edgy and be done with it :D

---

### Post by Old Pink on 2006-12-04
Ignore Shay at all costs. :) 

I updated from Dapper to Edgy and all is running perfectly fine. ;)

---

### Post by Shay Stephens on 2006-12-04
> **Old Pink said:**
> Ignore Shay at all costs. :)
Except the part about making a backup ;)

---

### Post by Old Pink on 2006-12-05
> **Shay Stephens said:**
> Except the part about making a backup ;)

Good point. ;) 

Always backup, then even should the worst possible thing occur, you can recover your system. 

And a backup will usually fit on a DVD, so there's no excuse. :)

---

### Post by gravediggers on 2006-12-06
On that point, is there a good thread or wiki on backing up? And whats the best tool to use?

---

### Post by Johnsie on 2006-12-06
Most of the people who had problems upgrading to Edgy from Dapper had the same problem....

They needed to apt get their video driver and reconfigure x:

---

### Post by Shay Stephens on 2006-12-06
> **Johnsie said:**
> They needed to apt get their video driver and reconfigure x:

Do you have a link on how to go about doing that?

---

