---
title: "Having trouble installing/updating programs with Terminal"
date: 2016-09-18
forum: Installation &amp; Upgrades
---

### Post by denilsonjvv on 2016-09-18
Recently, I've been trying to download programs from Google Chrome browser with Terminal.
For example when I try to download Spotify with these's instructions: [https://www.spotify.com/us/download/linux/](https://www.spotify.com/us/download/linux/) ,
I received an error on step 3 as followed:
```
** (appstreamcli:5060): CRITICAL **: Error while moving old database out of the way.AppStream cache update failed.
Reading package lists... Done
W: The repository 'cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: http://liveusb.info/multisystem/depot/dists/all/Release.gpg: Signature by key 32027DE3D67157C45E69C0AE4E940D7FDD7FB8CC uses weak digest algorithm (SHA1)
E: Failed to fetch cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)/dists/xenial/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Some index files failed to download. They have been ignored, or old ones used instead.



```
In addition, when I try to install programs, it gives me different errors. 
I believe that [this]("https://ubuntuforums.org/showthread.php?t=2325039") post is similar to my issue but I need additional help because I'm new to Ubuntu.
Any help would be appreciated, thanks!

---

### Post by howefield on 2016-09-18
Is this a live install with persistence on a USB stick ?

The output of

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

might be useful.

---

### Post by oldfred on 2016-09-18
Do you still have the installer CD-ROM selected as a choice for repositories?
Post this in code tags as a bit longer:

 cat /etc/apt/sources.list

---

### Post by denilsonjvv on 2016-09-18
As I mentioned above, I'm not too good with the knowledge of how Terminal works so I might not understand some of the questions that you guys ask me.
The output of egrep... :
```

/etc/apt/sources.list:deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu xenial main restricted #Added by software-properties
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main universe restricted multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list:deb-src http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu xenial-security main universe restricted multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main multiverse restricted universe
/etc/apt/sources.list:deb http://liveusb.info/multisystem/depot all main
/etc/apt/sources.list.d/embrosyn-ubuntu-cinnamon-xenial.list:deb http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main
/etc/apt/sources.list.d/embrosyn-ubuntu-cinnamon-xenial.list.save:deb http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main
/etc/apt/sources.list.d/gezakovacs-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu xenial main
/etc/apt/sources.list.d/gezakovacs-ubuntu-ppa-xenial.list.save:deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu xenial main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/haraldhv-ubuntu-shotcut-xenial.list:deb http://ppa.launchpad.net/haraldhv/shotcut/ubuntu xenial main
/etc/apt/sources.list.d/haraldhv-ubuntu-shotcut-xenial.list.save:deb http://ppa.launchpad.net/haraldhv/shotcut/ubuntu xenial main
/etc/apt/sources.list.d/jklein-ubuntu-ubermix-xenial.list:deb http://ppa.launchpad.net/jklein/ubermix/ubuntu xenial main
/etc/apt/sources.list.d/jklein-ubuntu-ubermix-xenial.list.save:deb http://ppa.launchpad.net/jklein/ubermix/ubuntu xenial main
/etc/apt/sources.list.d/kramden-team-ubuntu-ubermix-xenial.list:deb http://ppa.launchpad.net/kramden-team/ubermix/ubuntu xenial main
/etc/apt/sources.list.d/kramden-team-ubuntu-ubermix-xenial.list.save:deb http://ppa.launchpad.net/kramden-team/ubermix/ubuntu xenial main
/etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial main
/etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list.save:deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial main
/etc/apt/sources.list.d/spotify.list:deb http://repository.spotify.com stable non-free
/etc/apt/sources.list.d/webupd8team-ubuntu-atom-xenial.list:deb http://ppa.launchpad.net/webupd8team/atom/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-ubuntu-atom-xenial.list.save:deb http://ppa.launchpad.net/webupd8team/atom/ubuntu xenial main

```

---

### Post by denilsonjvv on 2016-09-18
Unsure.
[COLOR=#000000][INDENT]cat /etc/apt/sources.list[/INDENT]
[/COLOR]
```

deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial main restricted #Added by software-properties


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main universe restricted multiverse


## Major bug fix updates produced after the final release of the
## distribution.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner


deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://security.ubuntu.com/ubuntu xenial-security main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main multiverse restricted universe
## Depôt MultiSystem
deb http://liveusb.info/multisystem/depot all main

```

---

### Post by howefield on 2016-09-18
Open up the Software & Updates application and from the "*Other Software*" tab deselect the CDROM options.

Then try...

```
sudo apt update && sudo apt upgrade
```

Any errors ?

---

### Post by denilsonjvv on 2016-09-18
> **howefield said:**
> Open up the Software & Updates application and from the "*Other Software*" tab deselect the CDROM options.

Then try...

```
sudo apt update && sudo apt upgrade
```

Any errors ?
Can't find that option.
[ATTACH=CONFIG]271253[/ATTACH]

---

### Post by howefield on 2016-09-18
> **denilsonjvv said:**
> Can't find that option.

OK, try the first tab.. Ubuntu Software, is the CDROM option there ?

If not we can do this via the terminal easily enough.

---

### Post by denilsonjvv on 2016-09-18
I actually did find the option on the first tab right after I replied to you :-? and then I input the code you told me to and this is the most common error I've been getting as well:
$ sudo apt update && sudo apt upgrade
```
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Ign:4 http://liveusb.info/multisystem/depot all InRelease                      
Hit:5 http://repository.spotify.com stable InRelease                           
Hit:6 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:8 http://liveusb.info/multisystem/depot all Release                        
Hit:10 http://archive.canonical.com/ubuntu xenial InRelease                    
Hit:11 http://security.ubuntu.com/ubuntu xenial-security InRelease             
Hit:12 http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial InRelease      
Hit:13 http://archive.ubuntu.com/ubuntu xenial InRelease                  
Hit:14 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu xenial InRelease    
Hit:15 http://ppa.launchpad.net/haraldhv/shotcut/ubuntu xenial InRelease
Hit:16 http://ppa.launchpad.net/jklein/ubermix/ubuntu xenial InRelease
Hit:17 http://ppa.launchpad.net/kramden-team/ubermix/ubuntu xenial InRelease
Hit:18 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial InRelease
Hit:19 http://ppa.launchpad.net/webupd8team/atom/ubuntu xenial InRelease
                              
** (appstreamcli:8406): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
20 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: http://liveusb.info/multisystem/depot/dists/all/Release.gpg: Signature by key 32027DE3D67157C45E69C0AE4E940D7FDD7FB8CC uses weak digest algorithm (SHA1)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-4.8.0-040800rc1-generic
The following packages have been kept back:
  grub-common grub-pc grub-pc-bin grub2-common
The following packages will be upgraded:
  bamfdaemon gtk2-engines-murrine hunspell-es language-pack-es
  language-pack-es-base language-pack-gnome-es language-pack-gnome-es-base
  libbamf3-2 libpam-systemd libsystemd0 libsystemd0:i386 mtools musescore
  musescore-common systemd systemd-sysv
16 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
2 not fully installed or removed.
Need to get 31.5 MB of archives.
After this operation, 189 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpam-systemd amd64 229-4ubuntu8 [115 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libsystemd0 i386 229-4ubuntu8 [224 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libsystemd0 amd64 229-4ubuntu8 [206 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 systemd amd64 229-4ubuntu8 [3,639 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 systemd-sysv amd64 229-4ubuntu8 [13.9 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 language-pack-es all 1:16.04+20160627 [1,836 B]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 language-pack-es-base all 1:16.04+20160627 [3,144 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 language-pack-gnome-es all 1:16.04+20160627 [1,860 B]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 language-pack-gnome-es-base all 1:16.04+20160627 [3,693 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 bamfdaemon amd64 0.5.3~bzr0+16.04.20160824-0ubuntu1 [81.8 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libbamf3-2 amd64 0.5.3~bzr0+16.04.20160824-0ubuntu1 [51.9 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gtk2-engines-murrine amd64 0.98.2-0ubuntu2.2 [84.9 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 hunspell-es all 1:5.1.0-1ubuntu2.2 [234 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 mtools amd64 4.0.18-2ubuntu0.16.04 [175 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 musescore-common all 2.0.2+dfsg-2ubuntu0.1 [12.0 MB]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 musescore amd64 2.0.2+dfsg-2ubuntu0.1 [7,833 kB]
Fetched 31.5 MB in 5min 3s (104 kB/s)                                          
(Reading database ... 312233 files and directories currently installed.)
Removing linux-image-4.8.0-040800rc1-generic (4.8.0-040800rc1.201608072231) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.8.0-040800rc1-generic /boot/vmlinuz-4.8.0-040800rc1-generic
update-initramfs: Deleting /boot/initrd.img-4.8.0-040800rc1-generic
New kernel install - deferring aufs update to postinst
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.8.0-040800rc1-generic /boot/vmlinuz-4.8.0-040800rc1-generic
/usr/sbin/grub-probe: error: failed to get canonical path of `aufs'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.8.0-040800rc1-generic.postrm line 328.
dpkg: error processing package linux-image-4.8.0-040800rc1-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-4.8.0-040800rc1-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```
Something to do with "linux-image-4.8.0-040800rc1-generic"

---

### Post by oldfred on 2016-09-18
I do not think the 4.8 kernel is even released yet. And rc1 is older.
So one of the many ppa's you have added must include newer kernels, but has not been updated?

Why so many ppas? Newer users should stay with standard repositories until they fully understand the advantages & disadvantages a ppa may give. I use very few ppa and other than Boot-Repair more in a test install, not my main working install.

I would turn off all ppa and get system to do normal updates. Then add one ppa at a time until you find the one causing the problems. That is if you really need/want all those ppas.

---

### Post by denilsonjvv on 2016-09-18
> **oldfred said:**
> I do not think the 4.8 kernel is even released yet. And rc1 is older.
So one of the many ppa's you have added must include newer kernels, but has not been updated?

Why so many ppas? Newer users should stay with standard repositories until they fully understand the advantages & disadvantages a ppa may give. I use very few ppa and other than Boot-Repair more in a test install, not my main working install.

I would turn off all ppa and get system to do normal updates. Then add one ppa at a time until you find the one causing the problems. That is if you really need/want all those ppas.

Could you walk me through these steps? I'm really tired of looking all over Google to find an answer :P, Thanks.

---

### Post by denilsonjvv on 2016-09-18
Problem: linux kernel 4.8 was installed and it was unable to process when I was downloading or upgrading other programs and it wasn't letting me uninstall it neither from Synaptic Package Manager or from the terminal because it showed errors. So...
Solution: [https://ubuntuforums.org/showthread.php?t=1735575&page=2](https://ubuntuforums.org/showthread.php?t=1735575&page=2)

```

sudo mv /etc/kernel/postrm.d/zz-update-grub /etc/kernel/postrm.d/zz-update-grub.bad

sudo apt-get install -f

sudo mv /etc/kernel/postrm.d/zz-update-grub.bad /etc/kernel/postrm.d/zz-update-grub
```

Basically, this error appeared when I tried to install a program:
```
sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.8.0-040800rc1-generic linux-image-4.8.0-040800rc3-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 386 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 258226 files and directories currently installed.)
Removing linux-image-4.8.0-040800rc1-generic (4.8.0-040800rc1.201608072231) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.8.0-040800rc1-generic /boot/vmlinuz-4.8.0-040800rc1-generic
update-initramfs: Deleting /boot/initrd.img-4.8.0-040800rc1-generic
New kernel install - deferring aufs update to postinst
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.8.0-040800rc1-generic /boot/vmlinuz-4.8.0-040800rc1-generic
/usr/sbin/grub-probe: error: failed to get canonical path of `aufs'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.8.0-040800rc1-generic.postrm line 328.
dpkg: error processing package linux-image-4.8.0-040800rc1-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.8.0-040800rc3-generic (4.8.0-040800rc3.201608212032) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.8.0-040800rc3-generic /boot/vmlinuz-4.8.0-040800rc3-generic
update-initramfs: Deleting /boot/initrd.img-4.8.0-040800rc3-generic
New kernel install - deferring aufs update to postinst
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.8.0-040800rc3-generic /boot/vmlinuz-4.8.0-040800rc3-generic
/usr/sbin/grub-probe: error: failed to get canonical path of `aufs'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.8.0-040800rc3-generic.postrm line 328.
dpkg: error processing package linux-image-4.8.0-040800rc3-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-4.8.0-040800rc1-generic
 linux-image-4.8.0-040800rc3-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```
So I followed the steps above (renaming the file which caused the error) and linux 4.8 kernel was able to UNINSTALL.
After hours of searching!
Thanks to everyone that helped me out!

---

### Post by howefield on 2016-09-19
Cool, well done and thanks for posting the fix. :)

---

