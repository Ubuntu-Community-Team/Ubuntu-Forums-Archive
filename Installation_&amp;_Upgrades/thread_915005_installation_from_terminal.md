---
title: "installation from terminal"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by pariksakurikar on 2008-09-09
everytime i try to use ```
sudo apt-get install
``` ______ from the terminal window...
i get a message sayin connecting to archive.ubuntu.com and it never connects..
it always shows 0% and then there is a timeout...
please help!!!!!!!!!!

---

### Post by Rocket2DMn on 2008-09-09
Try running this command first:
```
sudo apt-get update
```
Then attempt to install whatever package you are trying to get from the repositories.

If it still doesn't work, you may want to change mirrors from System->Administration->Software Sources.  Repositories sometimes go down, so switching mirrors usually fixes that.  It's also nice to find a mirror that is faster than the main repos.

---

### Post by pariksakurikar on 2008-09-09
i have another major problem here..... actually i was tryin to install linux-backports-modules....and there was some error....both sudo apt-get install -f and sudo apt-get update....are givin a message sayin that some subprocess retudned exit status -1....and even synaptic is not able to do anythin....i did a remove...but there also there was an error... and im unable to install anythin new till this broken dependency is fixed...

---

### Post by Rocket2DMn on 2008-09-09
Can you please post the commands you are using + the output?

---

### Post by pariksakurikar on 2008-09-09
x:-~$sudo apt-get install -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.22-15-generic
Suggested packages:
  linux-doc-2.6.22 linux-source-2.6.22
The following NEW packages will be installed:
  linux-image-2.6.22-15-generic
0 upgraded, 1 newly installed, 0 to remove and 91 not upgraded.
6 not fully installed or removed.
Need to get 0B/18.5MB of archives.
After unpacking 63.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  linux-image-2.6.22-15-generic
Install these packages without verification [y/N]? y
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... 0% Fail
Error retrieving bug reports from the server with the following error message:
 W: Connection timed out - connect(2) (bugs.debian.org, #80)
It could be because your network is down, or because of broken proxy servers, or the BTS server itself is down. Check network configuration and try again
Retry downloading bug information?[Y/n]? n
Abort the installation[Y/n]? n
Retrieving bug reports... Done
Parsing Found/Fixed information... Done
/bin/sh: /usr/sbin/dpkg-preconfigure: not found
(Reading database ... 228401 files and directories currently installed.)
Unpacking linux-image-2.6.22-15-generic (from .../linux-image-2.6.22-15-generic_2.6.22-15.58_i386.deb) ...
Can't locate Debconf/Client/ConfModule.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /var/lib/dpkg/tmp.ci/preinst line 20.
BEGIN failed--compilation aborted at /var/lib/dpkg/tmp.ci/preinst line 20.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-15-generic_2.6.22-15.58_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: /boot/grub/splash.xpm.gz
Found kernel: /boot/vmlinuz-2.6.22-14-386
Found kernel: /boot/vmlinuz-2.6.22-14-virtual
Found kernel: /boot/vmlinuz-2.6.22-14-server
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-15-generic_2.6.22-15.58_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

x:-~$

---

### Post by pariksakurikar on 2008-09-09
similar to the connection to archive.ubuntu.com,
i am also unable to retrieve bug information each time i install....

im thoroughly confused...
and im unable to do anythin further...

---

### Post by Rocket2DMn on 2008-09-09
I have never seen anything like that before, let's check your sources file as well as some other info
```
cat /etc/apt/sources.list
lsb_release -a
apt-cache policy linux-image-2.6.22-15-generic
```
Also, let's try cleaning out the cache you have and re-downloading the files that have yet to install.
```
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install -f
```
Please post all the commands + output back here.

---

### Post by pariksakurikar on 2008-09-09
the first cat command yielded :

deb file:/var/cache/apt-build/repository apt-build main
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by pariksakurikar on 2008-09-09
for lsb_release -a  :

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

---

### Post by pariksakurikar on 2008-09-09
the third apt-cache policy command yields:


linux-image-2.6.22-15-generic:
Installed: (none)
  Candidate: 2.6.22-15.58
  Version table:
     2.6.22-15.58 0

---

### Post by pariksakurikar on 2008-09-09
the 'clean' worked fine but the upgrade && update is not completin as it is agian connecting to security.ubuntu.com and status is 0%..... is there some proxy configuration that i must do for my terminal??

---

### Post by Rocket2DMn on 2008-09-09
OK, it's possible that security.ubuntu.com repositories (or parts of them) are down and thus not responding right now.  Let's comment out the entry for that repo in sources.list
```
gksudo gedit /etc/apt/sources.list
```
Now change the line in red so that it matches
```
deb file:/var/cache/apt-build/repository apt-build main
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://in.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
[COLOR="Red"]# deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted[/COLOR]
deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://in.archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb http://in.archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```
Save and close, then update/upgrade
```
sudo apt-get update && sudo apt-get upgrade
```
Have you considered upgrading to Hardy at all?

---

### Post by pariksakurikar on 2008-09-09
i tried this

now the sudo upgrade && update yields:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-backports-modules-2.6.22-15-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 5685kB disk space will be freed.
Do you want to continue [Y/n]? Y
/bin/sh: /usr/sbin/dpkg-preconfigure: not found
(Reading database ... 228184 files and directories currently installed.)
Removing linux-backports-modules-2.6.22-15-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-15-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-15-generic
Cannot find /lib/modules/2.6.22-15-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-15-generic
dpkg: error processing linux-backports-modules-2.6.22-15-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.22-15-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Rocket2DMn on 2008-09-09
Lol, what a mess, we'll take this slow.  Let's autoremove and clean
```
sudo apt-get autoremove
sudo apt-get clean
```
Now does
```
sudo apt-get update && sudo apt-get upgrade
```
run ok?

If it's still complaining about linux-backports-modules-2.6.22-15-generic, then install that kernel itself
```
sudo apt-get install linux-image-2.6.22-15-generic
```
Then try again.

---

### Post by pariksakurikar on 2008-09-09
well i know this is gettin annoyin for ya...but

i tried update/upgrade instead of upgrade/update  
(i know this is what u told me in the first place)

but anyway...again it come to downloading from the server which i have specified in 'software resources' and it stops functioning i.e network timeout

---

### Post by pariksakurikar on 2008-09-09
well i know this is gettin annoyin for ya...but

i tried update/upgrade instead of upgrade/update  
(i know this is what u told me in the first place)

but anyway...again it come to downloading from the server which i have specified in 'software resources' and it stops functioning i.e network timeout

---

### Post by Rocket2DMn on 2008-09-09
I don't recall if this program exists in Gutsy (I think it does), but try going to System->Administration->Software Sources and uncheck everything in every tab.  Then under the Ubuntu Software tab, check for main, universe, restricted, and multiverse.  Under the Updates tab, enable -security and -updates.  Back on the Ubuntu Software tab, where it says Download from: click Other.  Now hit the Select Best Server button and let it do its search (may take a few minutes).  When it's finished, accept its decision, then click Close on the Software Sources window.  It will ask you to refresh/update, let it do this.  When all that is done, please post your sources.list file again
```
cat /etc/apt/sources.list
```
PS: I deleted your duplicate post.

---

### Post by pariksakurikar on 2008-09-09
ok....sorry...but i took some time catchin up with that..
now...
in ref to post 14:
autoremove gives the same error as the one i put in post 13....

also if i try to install that kernel i get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-2.6.22-15-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-image-2.6.22-15-generic has no installation candidate

---

### Post by pariksakurikar on 2008-09-09
and this is the cat output:
although you should know that durin reloading at the software resouces...it tried to to remove thos files and still gave the same error that came in post 13.....:(

pls pls gemme outta this mess.....i wanna be able to install new upgrades again...:(




# deb file:/var/cache/apt-build/repository apt-build main
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://ftp.hostrino.com/pub/ubuntu/archive/](http://ftp.hostrino.com/pub/ubuntu/archive/) gutsy main universe restricted multiverse
deb [http://ftp.hostrino.com/pub/ubuntu/archive/](http://ftp.hostrino.com/pub/ubuntu/archive/) gutsy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by Rocket2DMn on 2008-09-09
I'm going to manually edit your sources.list file because this is insanely ridiculous
```
# deb file:/var/cache/apt-build/repository apt-build main
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://in.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://in.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
# deb http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy main universe restricted multiverse
# deb http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-updates universe main multiverse restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

I disabled the security repositories (so you can't get updates from here, but that seems to be the problem...), and enabled the main, restricted, universe, and multiverse repos.  Copy and paste that over your existing sources.list file, save and close, then run and paste here the output of
```
sudo apt-get update
```

---

### Post by pariksakurikar on 2008-09-09
well im really sorry but this aint working either...
now its connecting to in.archive.ubuntu.com and status is 0%.....

i think i asked earlier....
do i have to do some proxy settings for my terminal????

---

### Post by Rocket2DMn on 2008-09-09
There aren't specific proxy settings specifically for terminal, but you can configure some on your machine, probably from System->Administration->Network.  Are you behind a proxy?  It sounds like you can't even connect to the web outside of firefox - do you have special proxy settings there?

---

### Post by pariksakurikar on 2008-09-09
well yes im behind a proxy....but my synaptic was able to download packages...its only when it comes to somethin related to the terminal that this happens...

---

### Post by pariksakurikar on 2008-09-09
another thing.....without having to download anythin....can i not remove or undo what i have done today....i mean somehow remove the linux-backport-modules and the image both.... the clean seems to have removed them from /var/cache/apt/archives.....but still the system says there is a broken dependency...
so can i somehow remove this broken dependency without having to do anythin with downloading???

---

### Post by pariksakurikar on 2008-09-09
and yet another thing.....my dvd-rw drive is not functioning due to some hardware error.... i shall get it replaced eventually...but is there anyway i can upgrade to the new version of ubuntu?? if yes and if u can help me....please tell me the exact procedure as many of my friends had grub problems durin installation...i have a windows vista os along with ubuntu...
so if i can somehow boot from a usb drive...and upgrade...that'd be a relief...

---

### Post by Rocket2DMn on 2008-09-09
OK, well I'm not sure what the issue is with your terminal, you may have to search around for that one.  As long as you are able to take care of stuff through Synaptic, that is good.

The appropriate way to remove packages that you installed today would be to uninstall them through Synaptic.  I'm not very good with using dpkg, all I can really suggest is trying
```
sudo dpkg --configure -a
``` and seeing if it outputs anything (normally it doesn't).

As for your dvd drive, you need to start a new thread on that.  For upgrade options, see [uhelp]community/HardyUpgrades[/uhelp] (note the Known Problems section re: upgrading with kernel 2.6.22-14).  Also know that Intrepid Ibex is set to be released at the end of October, but it is not a LTS release like Hardy is.

I think I do recall hearing about problems that some people had with GRUB when vista is installed, but I'm not sure on the details.  You may need to research more or ask around about that one.

---

### Post by pariksakurikar on 2011-10-13
Logged into my ubuntuforums account after a really long time and was going through this post. I remember this happening when I was new to ubuntu and linux in general and hadn't really gotten the hang of it. I dont remember what the solution to this problem was, but I remember having fixed it and having subsequently upgraded to each new version of ubuntu as and when it was launched. ^_^

Most importantly, thanks a lot to Rocket2dMn for having been so patient!

---

