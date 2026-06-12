---
title: "Unable to upgrade 14.04 to 14.10 in New Zealand"
date: 2015-01-27
forum: Installation &amp; Upgrades
---

### Post by johnspeedster on 2015-01-27
I have been unable to get the internal card reader to function since I upgraded to 14.04. Have tried every option found on-line but none work for me. One suggestion was to upgrade to 14.10, but I have a recurring problem that has bugged me for some time. Any updates I try always start well then fail with the message "Unable to connect to mirror.ihug.co.nz:http:" I have changed the download source to Canterbury but part way through any upgrade it reverts to ihug. Other wording includes "W: Failed to fetch [http://mirror.ihug.co.nz/ubuntu/dists/trusty-security/multiverse/binary-amd64/Packages](http://mirror.ihug.co.nz/ubuntu/dists/trusty-security/multiverse/binary-amd64/Packages)  404  Not Found" then finishes with "E: Some index files failed to download. They have been ignored, or old ones used instead." Several times I have got this message "A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry." but on checking, the network seems fine and has not fallen over - is it too slow? Vodafone broadband should be fine. 
Can I download the upgrade to a disk and run from that?
My system must be choking on all the bits and parts of code I have installed but I'm hoping/assuming that rubbish is cleared up (or atleast not causing a problem) at the end of an upgrade.
Although I have been an Ubuntu user for many years, I still don't understand most of it. These problems all seem to point to a common fault/problem but I can't work it out. Any ideas or suggestions from NZ or elsewhere would be most appreciated.

---

### Post by lisati on 2015-01-27
Odd. I haven't noticed any server difficulties. On the other hand, I'm still on 12.04.

BTW, it shouldn't matter too much which ISP you're with: all landline connections go through the same lines company.

---

### Post by sudodus on 2015-01-27
> **johnspeedster said:**
> I have been unable to get the internal card reader to function since I upgraded to 14.04. Have tried every option found on-line but none work for me. One suggestion was to upgrade to 14.10, but I have a recurring problem that has bugged me for some time. Any updates I try always start well then fail with the message "Unable to connect to mirror.ihug.co.nz:http:" ...

1. I suggest that you try 14.10 *live* without installing instead of upgrading. Upgrade only if the card reader works.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

2. If you have problems with updates, you could (temporarily) ***change to another mirror***.

3. And you can run the following commands, originally posted by *oldfred*.

You ***need sudo*** for all of these commands:

```
# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

# Remove lock
# If you are absolutely sure you do not have another upgrade process running.
# Locked dpkg - only if sure you are not running another update.

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a 

```

---

### Post by johnspeedster on 2015-01-28
Thanks for those ideas. I started at the top of the list and ran 14.10 live. Interesting. On screen it showed as 14.04 and still didn't work, so I downloaded from another site. This one hung after I choose to Try. Downloaded a further copy and installed it alongside 14.04 - still no card reader working. Went through the oldfred suggestions, again to no avail. The card reader is shown as being present - RTS 5229 - so I ran various attempts at installing the driver again extracting into the Home folder, but no luck. Did try using the "best" mirror but it still seems intent on changing back to ihug part way through any update. It does load some data from ihug, then falls over. Have decided to give up and load photos into the wife's iPad!

---

### Post by ian-weisser on 2015-01-28
> **johnspeedster said:**
> Any updates I try always start well then fail with the message "Unable to connect to mirror.ihug.co.nz:http:" I have changed the download source to Canterbury but part way through any upgrade it reverts to ihug. Other wording includes "W: Failed to fetch [http://mirror.ihug.co.nz/ubuntu/dists/trusty-security/multiverse/binary-amd64/Packages](http://mirror.ihug.co.nz/ubuntu/dists/trusty-security/multiverse/binary-amd64/Packages)  404  Not Found" then finishes with "E: Some index files failed to download. They have been ignored, or old ones used instead."

Please show us the entire content of your /etc/apt/sources.list file,
and the entire content of all files in the /etc/apt/sources.list.d/ directory

---

### Post by johnspeedster on 2015-01-28
Thanks. I can only hope this is the data you have requested. Despite having used Ubuntu for years, as I said above, I really don't know how to do "things". So saying, when I read this stuff below, it makes me wonder??? Why is 12.10 still there? and twice??

# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty main restricted
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty-updates main restricted
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty universe
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty universe
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty-updates universe
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty multiverse
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty multiverse
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty-updates multiverse
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty-updates universe
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty-security main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty-security main restricted
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty-security universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty-security universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty-security multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty-proposed multiverse restricted universe main

john-HP-650-Notebook-PC:~$ ls /etc/apt/sources.list.d/
deluge-team-ppa-trusty.list
deluge-team-ppa-trusty.list.distUpgrade
deluge-team-ppa-trusty.list.save
ehoover-compholio-trusty.list
ehoover-compholio-trusty.list.distUpgrade
ehoover-compholio-trusty.list.save
google-earth.list
google-earth.list.distUpgrade
google-earth.list.save
mc3man-trusty-media-trusty.list
mc3man-trusty-media-trusty.list.distUpgrade
mc3man-trusty-media-trusty.list.save
mjblenner-ppa-hal-trusty.list
mjblenner-ppa-hal-trusty.list.distUpgrade
mjblenner-ppa-hal-trusty.list.save
n-muench-vlc-trusty.list
n-muench-vlc-trusty.list.distUpgrade
n-muench-vlc-trusty.list.save
pipelight-stable-trusty.list
pipelight-stable-trusty.list.distUpgrade
pipelight-stable-trusty.list.save
team-xbmc-ppa-trusty.list
team-xbmc-ppa-trusty.list.distUpgrade
team-xbmc-ppa-trusty.list.save

---

### Post by ian-weisser on 2015-01-28
A couple issues there.

First, backup the /etc/apt/sources.list file before you edit it.

You don't need to edit it manually. You can use System Settings --> Software & Updates to make any changes you wish.


You should delete the Partner repository from Quantal. You will never use it again.

> **johnspeedster said:**
> ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) **quantal** partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) **quantal** partner


You might want to Delete the Quantal CD. You will never use it again.

> **johnspeedster said:**
> # deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ **quantal** main restricted
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ **quantal** main restricted


You have 12 references to mirror.ihug.co.nz , and then the same 12 for nzarchive.ubuntu.com. apt will happily go try to draw both.
Delete the mirror.ihug.co.nz lines:

> **johnspeedster said:**
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty main restricted
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty-updates main restricted
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty universe
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty universe
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty-updates universe
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty multiverse
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty multiverse
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty-updates multiverse
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) trusty-updates multiverse


Disable or delete the -proposed repository. That's where developers troubleshoot bugs and build problems before the updates are pushed out.
It is not intended for general use, and breakage is common there.

> **johnspeedster said:**
>  ## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) trusty-proposed multiverse restricted universe main

See if that solves the problem.
If it does not, we will move on to the next step.

---

### Post by johnspeedster on 2015-01-29
Excellent. I'll get onto that a bit later when it is far too hot to be outside working!

---

### Post by lisati on 2015-01-29
> **johnspeedster said:**
> <snip>when it is far too hot to be outside working!
:lolflag: Sure has been hotter than usual where I am too.

---

### Post by johnspeedster on 2015-01-30
Yipeeeee!! Excellent. I now get a clean update and upgrade! Still no card reader, but great news so far! I'll start a backup now and upgrade to 14.10 later unless someone thinks they may have a solution to the card reader problem. Thanks again everyone.

---

### Post by sudodus on 2015-01-30
I suggest that you download the 14.10 iso file and ***try it live*** before you decide to upgrade. You can also ***try*** the next version (the daily build), still being developed, Vivid Vervet to become 15.04 in April via the testing tracker link [http://iso.qa.ubuntu.com/qatracker/milestones/326/builds](http://iso.qa.ubuntu.com/qatracker/milestones/326/builds)
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by johnspeedster on 2015-02-02
Ok, no joy with 14.10 and not sure how to try 15.04. But just another observation.... not only is the card reader not functioning, but none of the three usb ports recognise my android phone when plugged in. It charges, but not able to use as a drive to download photos. Are the two problems related? I have used several usb cables and other devices seem to work Ok. lsusb does not show phone in any port but does list a flash drive or my Garmin cycle computer in whichever port utilised.

---

### Post by sudodus on 2015-02-02
I think the android problem very different from your original problem. Please create a new thread with a good descriptive title. It will increase your chances to get good help from people who know about connecting android devices.

---

