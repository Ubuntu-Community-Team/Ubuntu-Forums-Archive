---
title: "Need to know some things before upgrade to 11.04 beta"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by ChrisWells on 2011-04-01
Firstly I've never (successfully) upgraded before using update manager -d but I've only tried once.

I'm on 10.10 at the moment but I want to make a full disk backup using Acronis and try out 11.04 beta 1 so if I can't boot (like with the 11.04 Alpha 3) I'm ok.

What I want to know is if I upgrade to beta 1 it will install new things and settings, if beta 2 is released and I upgrade to that (after having beta 1 installed) will it overwrite all the settings again? Or will I be able to spend time set beta 1 up nice how I want it (if it works) and just smoothly upgrade gradually to final 11.04 keeping it pretty much exactly how I want it?

Also with the software sources, I understand I need to disable the ones I manually added before updating from 10.10 then to re-enable them, but how do I re-enable them for Natty as they are currently for Maverick? Do I just change the word Maverick to Natty, or is it better to remove and re-add them for natty? And do the authentication keys need updating or are they ok? I don't really know a lot about the keys.

1 more thing (sorry) will an upgrade overwrite any settings I have e.g. etc/fstab, sudoers, things like that? I know when you upgrade it gives you an option for some things e.g. keep or replace, if I keep old settings from maverick does it matter? Or does 11.04 add new lines/things to these files if I choose replace?

Sorry for all the questions, I'm pretty new been using ubuntu as my only OS for couple months now and most of my time has been spent tweaking settings and I don't want to lose them, or do a clean install when 11.04 final is released as I won't ever be able to remember them all.

Thanks for any answers

---

### Post by dabl on 2011-04-01
Sounds like you'd better stick with 10.10, while you continue to learn about Linux.  No offense intended -- but your questions indicate you don't understand that there will be new versions of many packages, including the Gnome or KDE configuration settings utilities, in the new 11.04 version.  When you are comfortable with the idea of backing up your user data to some external media, and then trying an upgrade, on the understanding that you _might_ need to reinstall the entire OS and restore your data backup, THEN you can consider seriously doing the upgrade.

---

### Post by laptoplinux on 2011-04-02
Something else that I'd advise you to look into is setting up your hard drive to have a separate /home partition.  Since what I'm talking about here **will involve wiping your drive**, you don't want to do it now.  But whenever you have some time and the opportunity to make a full backup of your stuff, you might want to think about it.

The benefits of keeping the / (root) and /home directories on two separate partitions is that it can greatly simplify installing, reinstalling, or upgrading an OS.  All your files (and many of your settings) are stored in the /home directory.  With split partitions, you only install the new OS on the root partition, and the installation process leaves the /home directory untouched.

So you can actually make a clean install of an operating system without destroying your files.  

Again, I'm not advising you to actually do this until you have researched it, are comfortable with doing it, and have a bit of downtime to do it in, but it's just a handy option (tangentially related to the post topic) to keep in mind for later.

---

### Post by beew on 2011-04-02
All you need is to install the beta in a usb drive or an external drive to test it out. Why trade in your work system  (which is only a few months old!) for a beta? I really have a hard time undertsanding the compulsive upgraders. :)

Go read the Natty thread, 11.04 is not stable now.

---

### Post by TedinOz on 2011-04-02
> **laptoplinux said:**
> Something else that I'd advise you to look into is setting up your hard drive to have a separate /home partition.  Since what I'm talking about here **will involve wiping your drive**, you don't want to do it now.  But whenever you have some time and the opportunity to make a full backup of your stuff, you might want to think about it.

The benefits of keeping the / (root) and /home directories on two separate partitions is that it can greatly simplify installing, reinstalling, or upgrading an OS.  All your files (and many of your settings) are stored in the /home directory.  With split partitions, you only install the new OS on the root partition, and the installation process leaves the /home directory untouched.

So you can actually make a clean install of an operating system without destroying your files.  

Again, I'm not advising you to actually do this until you have researched it, are comfortable with doing it, and have a bit of downtime to do it in, but it's just a handy option (tangentially related to the post topic) to keep in mind for later.

Interested in your comments here. Not unlike ChrisWells I am a new user running 10.10 and although I wouldn't be tempted with my very limited knowledge, of upgrading to a Beta version, the temptation to ultimately upgrade once a new version is stable,and when I know what I am doing,to be part of the growth in Ubuntu OS's is appealing. So my question is in relation to your backup comments. I do a regular back-up using Simple Backup and keep the latest on an an external drive. If I were ever to upgrade to say 11.04 and needed to restore from that back-up would it still work seeing it was done in one system and being applied to another?

---

### Post by itismike on 2011-04-02
Just adding my $.02 regarding in-place major version upgrading: 

I've been an avid Linux desktop user and tester for over close to 20 years and each time a new major release came out I attempted to perform an upgrade via [FONT="Courier New"]update-manager -d[/FONT]. 
And *each and every time* it screwed up my system so badly that I ended up installing the new version from CD. Versions I've experienced this in were: Redhat, SUSE, Debian, Mandrake, and every Ubuntu release since 5.10.

Maybe on a completely pristine system with no added software or tweaks it is possible, but not in my world, and I suspect not in the real world. I for one will never ever perform a major upgrade and expect it to function normally.

---

### Post by chefbodini on 2011-04-02
The cost of disk drives is pretty low now so why not get another drive?

Do create several partitions for your linux pleasure and do put /home on a seperate partition.  I have mine set up as such:

sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cae35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19530752   83  Linux
/dev/sda2            2432        4864    19530752   83  Linux
/dev/sda3            4864        6809    15625216   82  Linux swap / Solaris
/dev/sda4            6809      121602   922074112   83  Linux


This way I can use either sda1 or sda2 for what ever distro I want to try.  This allows me to keep an operational install on one of those partitions.

swap is of course on sda3

/home is on sda4 and is never touched by an install.

---

### Post by garvinrick4 on 2011-04-02
You do not lose your settings when doing an upgrade.
I comment out my ppa's in in my sources.list (put a # in front of ppa line.)
```
gksudo gedit /etc/apt/sources.list
```and make my comments and hit save:
Then:
```
sudo apt-get update && sudo apt-get upgrade
```Then:
```
sudo apt-get install aptitude
```then:
```
sudo sed -i 's/maverick/natty/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade
``` You are upgraded:
Now you can see if the ppa's you use have a natty version, I have very few ppa's and they
do not have nattys yet so I just uncomment them save.
```
sudo apt-get update 
```and yes it is just changing the version in .deb line for ppa.
#Every machine has different cards and drivers so they can all react different to new version:
#I myself have never had a problem on an upgrade: I keep one that I upgrade to use in bug testing and 
one that I do a clean install for bug testing purposes. I like to learn and use the next version, knowing there are going to be problems.
# You should have a seperate install for testing out a Alpha or Beta unless you want to fly by
the seat of your pants. This below is sources.list from maverick to natty after upgrade: Every one keeps theirs a little different.
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ natty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
 
deb http://mirror.anl.gov/pub/ubuntu/ natty main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ natty main restricted
 
## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.anl.gov/pub/ubuntu/ natty-updates main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ natty-updates main restricted
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.anl.gov/pub/ubuntu/ natty universe
deb-src http://mirror.anl.gov/pub/ubuntu/ natty universe
deb http://mirror.anl.gov/pub/ubuntu/ natty-updates universe
deb-src http://mirror.anl.gov/pub/ubuntu/ natty-updates universe
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.anl.gov/pub/ubuntu/ natty multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ natty multiverse
deb http://mirror.anl.gov/pub/ubuntu/ natty-updates multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ natty-updates multiverse
 
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner
 
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
 
deb http://mirror.anl.gov/pub/ubuntu/ natty-security main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ natty-security main restricted
deb http://mirror.anl.gov/pub/ubuntu/ natty-security universe
deb-src http://mirror.anl.gov/pub/ubuntu/ natty-security universe
deb http://mirror.anl.gov/pub/ubuntu/ natty-security multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ natty-security multiverse
# deb http://packages.medibuntu.org/ natty free non-free
deb http://mirror.anl.gov/pub/ubuntu/ natty-backports restricted main multiverse universe
deb http://packages.medibuntu.org/ maverick free non-free
```# If you keep your machine upgraded will get to beta2 by just doing that.
```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

