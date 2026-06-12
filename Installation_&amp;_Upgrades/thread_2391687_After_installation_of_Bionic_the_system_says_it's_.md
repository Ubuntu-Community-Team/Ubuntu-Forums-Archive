---
title: "After installation of Bionic the system says it's Linux Mint 18.3?"
date: 2018-05-12
forum: Installation &amp; Upgrades
---

### Post by cogitans on 2018-05-12
I&#8217;ve been using Linux Mint for several years now. But now I decided to go to Ubuntu as the terms of Ubuntu changed.

 
So I downloaded &#8220;ubuntu-18.04-desktop-amd64.iso&#8221; and installed it. I installed a few programs that I&#8217;m fond of.

 
But now i began optimizing the system itself. And now things slowly  began to confuse me. Several places the system told me that my system is  Linux Mint 18.3. That&#8217;s pretty strange to say the least. I did a format  of my partition when I did the install so leftover files from Linux  Mint can&#8217;t be the issue.

 
I compared the 2 files from Ubuntu and Linux Mint. They aren&#8217;t of the  same name and my used iso-file is of the same name that Ubuntu  presents.

 
I did several systemcalls:

 
&#8220;cat /etc/lsb-release&#8221;
->
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=18.3
DISTRIB_CODENAME=sylvia
DISTRIB_DESCRIPTION=&#8220;Linux Mint 18.3 Sylvia&#8221;


 &#8220;head -11 /usr/share/mintsources/rebecca/mintsources.conf&#8221;
->
[general]
description=Linux Mint 17.1 "Rebecca"
codename=rebecca
base_codename=trusty
use_ppas=true

 [mirrors]
default=http://packages.linuxmint.com
base_default=http://archive.ubuntu.com/ubuntu
mirrors=/usr/share/python-apt/templates/LinuxMint.mirrors
base_mirrors=/usr/share/python-apt/templates/Ubuntu.mirrors


 I was almost sure that somehow I got the iso of Linux Mint downloaded  and installed and I was just about to do a redownload and install  everything from scratch&#8230;again.

 
Then I wanted to make sure that the visuals agreed on my discoveries. And on
[https://www.ubuntu.com/desktop](https://www.ubuntu.com/desktop)
then desktop of Ubuntu looks just the same as my desktop although my system states that I&#8217;m using Linux Mint 18.3.

 
What&#8217;s going on here?
Has the mirrors of Ubuntus downloads been tampered with so some are pointing to Linux Mints servers?
How come the visuals are the same concerning the desktop?
I did all of these discoveries as I somehow noticed that there was a  folder named &#8220;linuxmint&#8221; in  &#8220;/usr/lib/linuxmint/mintSources/mintSources.py&#8221; during my updates.  That&#8217;s pretty strange, too, if I&#8217;m on Ubuntu Bionic.

 What&#8217;s going on here???

 
PS:
I&#8217;ve got my Home-directory on a partition separate from the main system.  It shouldn&#8217;t have any influenze on the systemfiles on my  systempartition. But I though it was worth mentioning that my  Home-folder is the only thing I&#8217;ve got from my old Linux Mint (with some  configuration-files on it).

 
PPS:
Oh, by the way: as the iso of Ubuntu 18.04 destroyed my GRUB during  installation (several attempts) and as &#8220;boot-repair&#8221; wasn&#8217;t able to fix  it I installed the system from an iso of Ubuntu 16.04 and did a  distribution-upgrade.

PPPS:
And I can't locate any windows concerning Additional Drivers as stated here:
[https://www.makeuseof.com/tag/install-proprietary-graphics-drivers-ubuntu-fedora-linux/](https://www.makeuseof.com/tag/install-proprietary-graphics-drivers-ubuntu-fedora-linux/)

PPPPS:
The command "cat /etc/apt/sources.list" states this confusing output:

```
# deb cdrom:[Ubuntu 16.04.4 LTS _Xenial Xerus_ - Release amd64 (20180228)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic main restricted
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic universe
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic-updates universe
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
#-->>deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
```

---

### Post by jeremy31 on 2018-05-12
If you tried to install Ubuntu in the Linux Mint partition, there is a chance that you didn't use the format option for that partition and that is why some files remain

---

### Post by PaulW2U on 2018-05-12
> **cogitans said:**
> I did a format  of my partition when I did the install so leftover files from Linux  Mint can’t be the issue.
cogitans, further to our exchange of comments which started at [https://community.ubuntu.com/t/bionic-based-on-linux-mint-18-3/5844](https://community.ubuntu.com/t/bionic-based-on-linux-mint-18-3/5844), please confirm how your disk is partitioned and which partitions you formatted. Thanks.

---

### Post by cogitans on 2018-05-12
As stated in the question:
"I did a format  of my partition when I did the install so leftover files from Linux  Mint can&#8217;t be the issue."

> **PaulW2U said:**
> cogitans, further to our exchange of comments which started at [https://community.ubuntu.com/t/bionic-based-on-linux-mint-18-3/5844](https://community.ubuntu.com/t/bionic-based-on-linux-mint-18-3/5844), please confirm how your disk is partitioned and which partitions you formatted. Thanks.

I've got decades of experience in partitioning so this isn't the issue. But to answer your question:

My (entire) OS-harddrive   
/dev/sdc1    ext4 Mount:             / Size:          119.24GB    Used: 11.36GB

Hmm, I'm trying to install the correct drivers, too. But I can't seem to find any place (GUI) to it through (I managed to do it from the terminal, though). As stated here:
[https://www.makeuseof.com/tag/install-proprietary-graphics-drivers-ubuntu-fedora-linux/](https://www.makeuseof.com/tag/install-proprietary-graphics-drivers-ubuntu-fedora-linux/)

neither any "**Additional Drivers**" shows in searching for "drivers" or going to "**Menu > Administration > Driver Manager**" (there's nothing of the name "Driver Manager").

---

### Post by PaulW2U on 2018-05-12
> **cogitans said:**
> My (entire) OS-harddrive   
/dev/sdc1    ext4 Mount:             / Size:          119.24GB    Used: 11.36GB
Thanks for that confirmation. So to summarise:

[LIST=1]
[*]You have one partition on /dev/sdc for Ubuntu 18.04 which as been formatted
[*]You have both xenial and bionic referred to in your repository sources
[*]lsb-release -a indicates you have Linux Mint installed
[*]But you actually see Ubuntu 18.04, i.e. GNOME Shell as your desktop
[*]A number of other minor issues compared to the above
[/LIST]
As a tester of most of the Ubuntu flavours for the 18.04 release I am totally confused by your experience of installing Ubuntu 18.04 on a newly formatted partition. Hopefully some else can throw some light on what you are seeing.

---

### Post by jbicha on 2018-05-12
> **cogitans said:**
> I installed a few programs that I’m fond of.


Did you install programs from Linux Mint? What files do you have in ```
/etc/apt/sources.list.d
``` ?

---

### Post by jeremy31 on 2018-05-12
jbicha That info is at the bottom of the original post

I have only seen similar things happen when not formatting the partition and even then I would have thought that the Ubuntu install would have replaced /etc/lsb-release

---

### Post by jbicha on 2018-05-12
@jeremy31, my question was slightly different than what was posted at the bottom of the original post. I'm particularly interested in whether he has PPAs enabled.

---

### Post by PaulW2U on 2018-05-12
> **jeremy31 said:**
> jbicha That info is at the bottom of the original post
the info quoted is the contents of /etc/sources.list. jbicha asked to see the listing at /etc/sources.list.d/
> **jeremy31 said:**
> I have only seen similar things happen when not formatting the partition and even then I would have thought that the Ubuntu install would have replaced /etc/lsb-release
Agreed, even if you don't ask for your / partition to be formatted the installer still **replaces** part of it and installs such files as /etc/lsb-release with the new version.

---

### Post by cogitans on 2018-05-12
> **PaulW2U said:**
> Thanks for that confirmation. So to summarise:

[LIST=1]
[*]You have one partition on /dev/sdc for Ubuntu 18.04 which as been formatted 
[*]You have both xenial and bionic referred to in your repository sources 
[*]lsb-release -a indicates you have Linux Mint installed 
[*]But you actually see Ubuntu 18.04, i.e. GNOME Shell as your desktop 
[*]A number of other minor issues compared to the above 
[/LIST]
As a tester of most of the Ubuntu flavours for the 18.04 release I am totally confused by your experience of installing Ubuntu 18.04 on a newly formatted partition. Hopefully some else can throw some light on what you are seeing.

Yep, I'm quite confused, too :-/

The only explanation I can come to think of is that some heavy configuration-files are located on my HOME-partition that takes control of my entire system more or less (my HOME-partition has been used for several versions of Linux Mint).
1:
But is that even possible? I mean for some configuration-files on the HOME-partition to that thorough effect on the system?

2:
I'm pretty much ready to do a reformat and rei-nstallation of the system. Does any utility like "Deja Cup" (wasn't that the name of it?) usable for Ubuntu 18.04 to register the installed programs so that I can quickly reinstall them after a system-re-installation?

---

### Post by cogitans on 2018-05-12
> **jbicha said:**
> Did you install programs from Linux Mint? What files do you have in ```
/etc/apt/sources.list.d
``` ?

In that directory I've got:

additional-repositories.list
audio-recorder-ppa-xenial.list
clipgrab-team-ppa-xenial.list
danielrichter2007-grub-customizer-xenial.list
etcher.list
geary-team-releases-xenial.list
getdeb.list
gezakovacs-ppa-xenial.list
graphics-drivers-ppa-xenial.list
i-nex-development-team-stable-xenial.list
jonathonf-vlc-xenial.list
libreoffice-ppa-xenial.list
megasync.list
nilarimogard-webupd8-xenial.list
noobslab-apps-xenial.list
official-package-repositories.list
openjdk-r-ppa-xenial.list
phablet-team-tools-xenial.list
plushuang-tw-uget-stable-xenial.list
spotify.list
stebbins-handbrake-releases-xenial.list
teejee2008-ppa-xenial.list
ubuntu-audio-dev-alsa-daily-xenial.list
ubuntu-wine-ppa-xenial.list
unit193-encryption-xenial.list
videolan-stable-daily-xenial.list
virtualbox.list
virtualbox.org.list
vivaldi.list
vivaldi.list.save

I guess some of those are for Mint, right?

---

### Post by cogitans on 2018-05-12
Well, I installed Mint Backup now, took a copy of the output of programs listed in this thread and went through the "Show programs" for installed programs.
Now I'll try a reinstall of Ubuntu.

Thanks for your help :-)

---

