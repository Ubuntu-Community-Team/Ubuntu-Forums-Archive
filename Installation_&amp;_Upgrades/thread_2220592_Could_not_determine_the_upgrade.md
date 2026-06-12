---
title: "Could not determine the upgrade"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by frans-bilsen on 2014-04-28
Hi,

I'm trying to upgrade from 13.10 to 14.04 and got this after running sudo do-release-upgrade:

---8<---
Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Calculating the changes

Calculating the changes

Could not determine the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 


Restoring original system state
---8<---

The last 'Unofficial packages not provided by Ubuntu' may very well apply, but how do I determine this, so I can (hopefully) remove them?

Thanks,
Frans

---

### Post by Ubi_one_2014 on 2014-04-28
try apt-get update && apt-get dist-upgrade first

pls post the  output here

---

### Post by ibjsb4 on 2014-04-28
Try

```
[COLOR=#000000]sudo do-release-upgrade -d[/COLOR]
```

---

### Post by frans-bilsen on 2014-04-29
No problems seen:

sudo apt-get update

Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy InRelease
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates InRelease
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports InRelease
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy Release.gpg
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports Release.gpg
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy Release
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates Release
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/main Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/restricted Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/universe Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/main amd64 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/restricted amd64 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/universe amd64 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/restricted i386 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/universe i386 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/main Translation-en_GB
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/main Translation-en
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/multiverse Translation-en
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/restricted Translation-en_GB
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main amd64 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/universe Translation-en_GB
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted amd64 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe amd64 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/restricted Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/universe Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse amd64 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/main amd64 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/restricted amd64 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/universe amd64 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/main i386 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/restricted i386 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/multiverse i386 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/main Translation-en_GB
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/multiverse Translation-en_GB
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/restricted Translation-en_GB
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/restricted Translation-en
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/universe Translation-en_GB
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/universe Translation-en
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/main Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/restricted Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/universe Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/multiverse Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/restricted amd64 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/universe amd64 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/multiverse amd64 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/main i386 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/restricted i386 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/universe i386 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/multiverse i386 Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/multiverse Translation-en
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/restricted Translation-en
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/main Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/multiverse Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/restricted Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy/universe Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/main Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/restricted Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-updates/universe Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/main Translation-en_GB
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/main Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/multiverse Translation-en_GB
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/restricted Translation-en_GB
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/restricted Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/universe Translation-en_GB
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) saucy-backports/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US

sudo apt-get dist-upgrade:

Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by frans-bilsen on 2014-04-29
Same as before.

---

### Post by frans-bilsen on 2014-04-29
> **ibjsb4 said:**
> Try

```
[COLOR=#000000]sudo do-release-upgrade -d[/COLOR]
```

same as before.

---

### Post by bapoumba on 2014-04-29
You are still on saucy 13.10.

Has trusty been offered to you via a dialog box ? If not, got to software sources and make sure you have checked to be notified on new releases.

---

### Post by Ubi_one_2014 on 2014-04-30
cd /etc/apt/sources.list.d

ls[enter]

pls post the output

---

### Post by frans-bilsen on 2014-04-30
-rw-r--r-- 1 root root 157 apr 29 21:45 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list
-rw-r--r-- 1 root root 157 apr 29 21:45 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.distUpgrade
-rw-r--r-- 1 root root 157 apr 29 21:39 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
-rw-r--r-- 1 root root 152 apr 29 21:45 steam.list
-rw-r--r-- 1 root root 152 apr 29 21:45 steam.list.distUpgrade
-rw-r--r-- 1 root root 152 apr 29 21:39 steam.list.save
-rw-r--r-- 1 root root 134 apr 29 21:45 ubuntu-wine-ppa-saucy.list
-rw-r--r-- 1 root root 134 apr 29 21:45 ubuntu-wine-ppa-saucy.list.distUpgrade
-rw-r--r-- 1 root root 134 apr 29 21:39 ubuntu-wine-ppa-saucy.list.save
-rw-r--r-- 1 root root 134 apr 29 21:45 xorg-edgers-ppa-saucy.list
-rw-r--r-- 1 root root 134 apr 29 21:45 xorg-edgers-ppa-saucy.list.distUpgrade
-rw-r--r-- 1 root root 134 apr 29 21:39 xorg-edgers-ppa-saucy.list.save

---

### Post by frans-bilsen on 2014-04-30
I just removed (still have a backup) all of those files and tried "sudo do-release-upgrade" again, same result.

---

### Post by bapoumba on 2014-04-30
Please make sure all you ppa and other repositories are uncheked from Software Sources.
Then run ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` to make sure your system is fully up to date.
Then your can process from here [https://help.ubuntu.com/community/TrustyUpgrades](https://help.ubuntu.com/community/TrustyUpgrades)

Post any error message you get.

---

### Post by Ubi_one_2014 on 2014-04-30
alt+f2
update-manager[enter]

if nothing happends:

apt-get install update-manager, and repeat firsy step

---

### Post by frans-bilsen on 2014-05-01
> **bapoumba said:**
> Please make sure all you ppa and other repositories are uncheked from Software Sources.
Then run ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` to make sure your system is fully up to date.
Then your can process from here [https://help.ubuntu.com/community/TrustyUpgrades](https://help.ubuntu.com/community/TrustyUpgrades)

Post any error message you get.

This is the error from the messagebox from update-manager (unsurprisingly it's exactly the same as for the command line version):

Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.

---

### Post by frans-bilsen on 2014-05-01
> **Ubi_one_2014 said:**
> alt+f2
update-manager[enter]

if nothing happends:

apt-get install update-manager, and repeat firsy step

Of course I only tried the command line version because it's easier to paste stuff into forums.
So no difference.

BR,
Frans

---

### Post by bapoumba on 2014-05-01
Do you have this log file ?
/var/log/dist-upgrade/apt.log

[https://www.kubuntuforums.net/showthread.php?63885-An-unresolvable-problem-occurred-while-calculating-the-upgrade&p=337288&viewfull=1#post337288](https://www.kubuntuforums.net/showthread.php?63885-An-unresolvable-problem-occurred-while-calculating-the-upgrade&p=337288&viewfull=1#post337288)

---

### Post by frans-bilsen on 2014-05-01
Hi,

As this didn't yield any result I tried to file a bug report and found there are things like this.

This bug ([https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1301164](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1301164)) seems to be most helpful with: 
"There is a long list of non official packages installed on your system  that are likely responsible of blocking the upgrade. You can start by  reverting all video related packages to the version of an official  Ubuntu repository (i.e all xorg-edgers related packages) then try the  upgrade again."

And historically:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1069133](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1069133)

So as I sort of asked in the first post, how do I find out what packages are installed from non-official ubuntu sources, I can find the ppa's but how do I know what packages are installed from them. I guess I would need to remove those ppa's and remove all packages from them, then install official versions if possible (which probably isn't possible).

Thanks

---

### Post by bapoumba on 2014-05-01
See my above post :)
You can look for the broken packages and we can try to work from there.

Please make sure you have disabled all your ppa and third party repos, thanks.

---

### Post by frans-bilsen on 2014-05-01
> **bapoumba said:**
> Do you have this log file ?
/var/log/dist-upgrade/apt.log

[https://www.kubuntuforums.net/showthread.php?63885-An-unresolvable-problem-occurred-while-calculating-the-upgrade&p=337288&viewfull=1#post337288](https://www.kubuntuforums.net/showthread.php?63885-An-unresolvable-problem-occurred-while-calculating-the-upgrade&p=337288&viewfull=1#post337288)

So I ran 
```
$ sudo ppa-purge xorg-edgers
```

Well actually I had to install ppa-purge first, then add the xorg-edgers ppa again and then purge it
It doesn't stop where it used to. 

This seems to fix it, I'll let you know if it really worked :-).

Thanks,
Frans

---

### Post by bapoumba on 2014-05-01
Ah, cool :)
Found several threads with the same error and video drivers, but was not quite sure that could be your case.

---

### Post by frans-bilsen on 2014-05-01
Yep, all is good now. 

Thanks

---

### Post by bapoumba on 2014-05-01
Please mark your thread as solved (under Thread Tools), thanks :)

---

