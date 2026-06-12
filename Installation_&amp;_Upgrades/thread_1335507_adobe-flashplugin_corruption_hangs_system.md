---
title: "adobe-flashplugin corruption hangs system?"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by DRNewcomb on 2009-11-23
I seem to have a problem with a corrupt adobe-flashplugin which has, as odd as this may seem, locked up my system. It started with the update manager not being able to update the adobe-flashplugin because of an error code of some sort. This went on for a few weeks with this error blocking other upgrades. I tried to uninstall the flashplugin. Now, I can only get into the system through the recovery shell (ESC at bootup). Running apt-get I can't install, remove or update the flashplugin. I also can't "apt-get install ubuntu-desktop", which worked before when I had a hosed system. 

Any suggestions?

---

### Post by zvacet on 2009-11-23
```
sudo apt-get update && sudo apt-get upgrade
```

post output here.Also you can post 

```
cat /etc/apt/sources.list
```

---

### Post by DRNewcomb on 2009-11-23
> **zvacet said:**
> ```
sudo apt-get update && sudo apt-get upgrade
```

post output here.Also you can post 

```
cat /etc/apt/sources.list
```

Output from above without the sudo, since I was in a root shell, but using a "|tee" to get it saved into a file.
> 
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be upgraded:
  adobe-flashplugin
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/4018kB of archives.
After this operation, 262kB of additional disk space will be used.
Do you want to continue [Y/n]? (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%

etc.
> 
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 277235 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.12.36-1hardy1 (using .../adobe-flashplugin_10.0.32.18-1hardy1_i386.deb) ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing /var/cache/apt/archives/adobe-flashplugin_10.0.32.18-1hardy1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/adobe-flashplugin_10.0.32.18-1hardy1_i386.deb

I get essentially the same errors whenever I try to upgrade, install or remove anything.

Sources.list
> 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
# deb [http://mirror.csclub.uwaterloo.ca/debian-multimedia/](http://mirror.csclub.uwaterloo.ca/debian-multimedia/) stable main
# deb [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) karmic main
deb [http://ppa.launchpad.net/qgis/unstable/ubuntu](http://ppa.launchpad.net/qgis/unstable/ubuntu) karmic main


Also, what happens when I try a normal boot is that I get a text (TTY) login prompt that starts to blink and won't accept input except about every 5th time I press a character. I can't login this way because I can never get the password entered. All the above is done in a root shell from the recovery boot.

---

### Post by phillw on 2009-11-23
I had an issue, quite involved, with flash player...

[http://ubuntuforums.org/showthread.php?t=1305829](http://ubuntuforums.org/showthread.php?t=1305829)

It is long, it is messy - but, it got them working. The last page has the solution for flash player, save you reading it all.

Try this,
 				 				**Re: unable to uninstall corrupted flash player file** 			
 			 			 		   		 		 		Fixed the problem for me

sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin

If that fails, use the long version on page 4.

Regards,

Phill.

---

### Post by DRNewcomb on 2009-11-24
Thanks! I did as suggested above. I now have a perfectly "clean" system. Dpkg is happy, fsck is happy, we're fully updated.  Just one problem. When I do a normal boot-up I still get the flashing "Starting up" and am not able to log-in. No X11 startup. I can get in by pressing <ESC> at boot and booting in recovery mode to get a TTY login and I have network connectivity. I tried "apt-get install -f ubuntu-desktop" and was informed that everything was just dandy. Should I try a "--reinstall" or "--force-yes"?

---

### Post by nene7 on 2009-11-24
i wrote[FONT=monospace] but it say that i have to reinstalle the adobe-flashplugin package how i do it.[/FONT]
 
sudo apt-get update && sudo apt-get upgrade

---

