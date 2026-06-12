---
title: "&quot;lsb_release -a&quot; won't show 6.06.1"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by vtel57 on 2006-08-11
Yeah, mine won't update either. :(

Here's my source.list

> ## dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## dapper-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## dapper-updates universe main restricted multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe main restricted multiverse

## dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

## dapper-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

## dapper universe main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## dapper-backports main restricted universe multiverse

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

## canonical dapper-commercial main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## automatix

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

I must be missing something here. :(

---

### Post by ubuntu_demon on 2006-08-11
**I'm posting this as a forums user and not as a staff member. This all on your own risk.**

**HOWTO FIX 6.06.1 not showing up**

Don't worry If "lsb_release -a" doesn't tell you that you are using 6.06.1. It's probably easy to solve. **Please follow all steps.**Try this :

**1)** Do a reboot and try "lsb_release -a" again.
**2)** Make sure your sources.list is alright. 

Replace your Dapper sources.list for a clean one :
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

A little note :
You **could** disable multiverse and universe **if** you had them disabled previously and you have no universe nor multiverse packages installed. IMHO multiverse and universe should be used for most users. So you probably don't have to comment them.

**3)**
Start the terminal. Don't type the $.

$sudo apt-get update
$sudo apt-get install ubuntu-minimal ubuntu-standard ubuntu-desktop [I](or xubuntu,kubuntu,edubuntu)
[/I]
$sudo apt-get upgrade
$sudo apt-get dist-upgrade

if it says "package A is being kept back" either force it to update like this :
$sudo apt-get install *packageA*

Or remove it if you don't like the package :
$sudo apt-get remove *packageA*

**4)** reboot
**5)** lsb_release -a should return 6.06.1. If it doesn't try this :
$ sudo aptitude install lsb_release lsb-base --reinstall
$ lsb_release -a

Still no result ? Then save your current work and go to ctrl-alt-f1 instead of a normal terminal. A lot of stuff will get removed but it is easily reinstalled.

First let's remove all lsb packages :

$ sudo aptitude remove lsb-release lsb-base --purge

You probably won't have any of these installed but if you do remove them :
$ sudo aptitude remove lsb-core lsb-cxx lsb-desktop lsb-graphics lsb-qt4 lsbappchk lsb-rpm --purge

Let's install some stuff again :
$ sudo aptitude install ubuntu-minimal lsb-release
$ sudo aptitude install ubuntu-standard 
$ sudo aptitude install ubuntu-desktop
$ lsb_release -a
If it's still wrong then post the results of all the commands including the result of :
$ dpkg -l | grep lsb
**6)** Now you can create a custom sources.list again. Please be a bit conservative with it.

Here's a sources.list which is suitable for most average users :
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by vtel57 on 2006-08-11
I am using the 386 kernel. I followed Ubuntu_Demon's tutorial a few posts back on this thread and my system still shows 6.06 only, no 6.06.1. :(

Using $sudo apt-get install ubuntu-minimal ubuntu-standard ubuntu-desktop, the output stated that I had the newest versions already installed.

](*,)

---

### Post by ubuntu_demon on 2006-08-11
> **vtel57 said:**
> I am using the 386 kernel. I followed Ubuntu_Demon's tutorial a few posts back on this thread and my system still shows 6.06 only, no 6.06.1. :(

Using $sudo apt-get install ubuntu-minimal ubuntu-standard ubuntu-desktop, the output stated that I had the newest versions already installed.

](*,)
Did you run $sudo apt-get update ?
You are using a clean sources.list and you didn't forget to reboot ?

---

### Post by vtel57 on 2006-08-11
I didn't use your suggested source list because it has source code and backports enabled. However, I have all the other repositories on my own source.list just like your suggested list. Question though... would I **need** source code or backports for this upgrade to work. And yes, I followed all the other steps as you had them listed, including the reboot. 

By the way, thank you for your assistance! :)

Regards,

~Eric

---

### Post by vtel57 on 2006-08-11
OK, this time I used your exact sources.list. Here's my terminal output for the commands in your post above:

> vtel57@ericsbane02:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [11.1kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources [255kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [2043B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [1805B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources [533B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources [1478B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [95.2kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources [975kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [71.7kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [46.2kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources [14B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources [14B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources [14B]
Fetched 1559kB in 9s (156kB/s)
Reading package lists... Done
vtel57@ericsbane02:~$ sudo apt-get install ubuntu-minimal ubuntu-standard ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
ubuntu-minimal is already the newest version.
ubuntu-standard is already the newest version.
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
vtel57@ericsbane02:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
vtel57@ericsbane02:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I'm going to reboot now and see what happened. Back in a minute...

Unfortunately, that didn't do it either. :(

Here's my output from lsb_release -a:

> vtel57@ericsbane02:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06 LTS
Release:        6.06
Codename:       dapper
vtel57@ericsbane02:~$



*shrugging* :-?

---

### Post by ubuntu_demon on 2006-08-11
IMHO it was better to have a seperate thread for your problem.

What's the result of :
$uname -a

---

### Post by vtel57 on 2006-08-11
> **ubuntu_demon said:**
> IMHO it was better to have a seperate thread for your problem.

What's the result of :
$uname -a

```
$ uname -a
```

Output:

> Linux ericsbane02 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux

---

### Post by ubuntu_demon on 2006-08-11
Your problem is very strange :)

What kind of processor do you have ?

What's the history of this machine ? When did you install it ? How did you install it ?

---

### Post by ubuntu_demon on 2006-08-11
> **vtel57 said:**
> I didn't use your suggested source list because it has source code and backports enabled. 

It's not relevant to this problem whether they are enabled or not.

I will check this thread later. Probably tomorrow.

---

### Post by vtel57 on 2006-08-11
> **ubuntu_demon said:**
> Your problem is very strange :)

What kind of processor do you have ?

What's the history of this machine ? When did you install it ? How did you install it ?

MSI - AMD Athlon XP 2600+

1Gig RAM

Boot drive - Seagate 120Gig - Primary EIDE (Partition 1, ext3, 15Gig - Ubuntu Linux 6.06 root; Partition 2, ext3, 100Gig - /home; Partition 3, 5Gig swap)

80Gig Maxtor RAID-0 (Partition 1, NTFS, 20Gig - Windows XP Pro; Partition 2, FAT, 60Gig - storage)

Nvidia GEFORCE4 Ti4200

Creative Labs Soundblaster 5.1 Audio

Creative Labs CDROM - Secondary EIDE Slave

Creative Labs CDRW - Secondary EIDE Master

ZIP 100 ATAPI - Primary EIDE Slave

Standard 3.5" Floppy 

This machine was assembled and has been in use since '03 with Windows XP. I've never had any hardware troubles with it. The Ubuntu was first installed just under a month ago.

---

### Post by FatherDale on 2006-08-12
This worked. Thanks!

---

### Post by ubuntu_demon on 2006-08-12
vtel57 this problem is not hardware related.

Try reinstalling lsb-release. I've updated the HOWTO post :
[http://www.ubuntuforums.org/showpost.php?p=1369334&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1369334&postcount=2)

---

### Post by vtel57 on 2006-08-13
Hi Ubuntu_Demon!

I'm sorry it's taken me so long to respond, but I've been offline since Friday. I wiped the drive with Ubuntu and reinstalled a fresh CD of 6.06.1. However, it developed unrelated stability problems and I ended up wiping it again. I'm in Windows right now... arrrrrrgh! I'm going to reinstall the Ubuntu in just a short while. 

Thank you so much for your assistance!

Regards,

~Eric

---

### Post by ubuntu_demon on 2006-08-13
> **vtel57 said:**
> Hi Ubuntu_Demon!

I'm sorry it's taken me so long to respond, but I've been offline since Friday. I wiped the drive with Ubuntu and reinstalled a fresh CD of 6.06.1. However, it developed unrelated stability problems and I ended up wiping it again. I'm in Windows right now... arrrrrrgh! I'm going to reinstall the Ubuntu in just a short while. 

Thank you so much for your assistance!

Regards,

~Eric
What kind of stability problems ? 

If you did a regular install and you have stability problems look for :

-heat (make sure it's not a heat problem. sometimes opening the case adds enough cool air for a system to become stable again)
-dust (make sure you clean your computer once in a while)
-check the memory (you can check it using the grub entry)
-try a different videocard

If it's stable after the installation but you have some problems after installing certain software then you might try my guide here :
[http://www.ubuntuforums.org/showthread.php?t=186792](http://www.ubuntuforums.org/showthread.php?t=186792)

---

### Post by llamakc on 2006-08-13
I just stumbled on this thread and noticed this on my system:

```

root@dothan:/home/ken# aptitude remove lsb-release --purge
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  launchpad-integration lsb-core ubuntu-minimal update-manager
The following packages will be REMOVED:
  lsb-release
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 81.9kB will be freed.
The following packages have unmet dependencies:
  update-manager: Depends: lsb-release but it is not installable
  launchpad-integration: Depends: lsb-release but it is not installable
  ubuntu-minimal: Depends: lsb-release but it is not installable
  lsb-core: Depends: lsb-release but it is not installable
Resolving dependencies...
open: 1273; closed: 2009; defer: 0; conflict: 14                               oThe following actions will resolve these dependencies:

Remove the following packages:
deskbar-applet
ekiga
eog
evince
evolution
evolution-exchange
evolution-plugins
file-roller
gaim
gcalctool
gconf-editor
gedit
gnome-app-install
gnome-applets
gnome-games
gnome-media
gnome-nettool
gnome-panel
gnome-system-monitor
gnome-terminal
gnome-utils
gnome-volume-manager
gthumb
gucharmap
hal-device-manager
language-selector
launchpad-integration
libgucharmap4
liblaunchpad-integration0
liblpint-bonobo0
lsb
lsb-core
lsb-cxx
lsb-desktop
lsb-graphics
nautilus
nautilus-sendto
python-gnome2-desktop
python-launchpad-integration
python2.4-gnome2-desktop
rhythmbox
serpentine
sound-juicer
synaptic
totem
totem-gstreamer
ubuntu-desktop
ubuntu-minimal
update-manager
update-notifier
xubuntu-desktop
yelp

Downgrade the following packages:
ubuntu-docs [6.06.2 (now) -> 6.06.1 (dapper)]

Leave the following dependencies unresolved:
contact-lookup-applet recommends evolution (>= 2.0)
evolution-data-server recommends evolution (>= 2.0.0)
nautilus-data recommends nautilus (= 2.14.1-0ubuntu9)
ubuntu-docs recommends yelp
openoffice.org-evolution recommends evolution
gnome-session recommends gnome-panel
gnome-session recommends nautilus
gnome-terminal-data recommends gnome-terminal
gnome-games-data recommends gnome-games
gnome-panel-data recommends gnome-panel (= 2.14.2-0ubuntu1)
Score is -20286

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```

I don't use aptitude often enough. Any ideas on how to get the broken packages fixed (and get lsb_release to show 6.06.1)?

---

### Post by ubuntu_demon on 2006-08-13
> **llamakc said:**
> I just stumbled on this thread and noticed this on my system:

```

root@dothan:/home/ken# aptitude remove lsb-release --purge
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  launchpad-integration lsb-core ubuntu-minimal update-manager
The following packages will be REMOVED:
  lsb-release
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 81.9kB will be freed.
The following packages have unmet dependencies:
  update-manager: Depends: lsb-release but it is not installable
  launchpad-integration: Depends: lsb-release but it is not installable
  ubuntu-minimal: Depends: lsb-release but it is not installable
  lsb-core: Depends: lsb-release but it is not installable
Resolving dependencies...
open: 1273; closed: 2009; defer: 0; conflict: 14                               oThe following actions will resolve these dependencies:

Remove the following packages:
deskbar-applet
ekiga
eog
evince
evolution
evolution-exchange
evolution-plugins
file-roller
gaim
gcalctool
gconf-editor
gedit
gnome-app-install
gnome-applets
gnome-games
gnome-media
gnome-nettool
gnome-panel
gnome-system-monitor
gnome-terminal
gnome-utils
gnome-volume-manager
gthumb
gucharmap
hal-device-manager
language-selector
launchpad-integration
libgucharmap4
liblaunchpad-integration0
liblpint-bonobo0
lsb
lsb-core
lsb-cxx
lsb-desktop
lsb-graphics
nautilus
nautilus-sendto
python-gnome2-desktop
python-launchpad-integration
python2.4-gnome2-desktop
rhythmbox
serpentine
sound-juicer
synaptic
totem
totem-gstreamer
ubuntu-desktop
ubuntu-minimal
update-manager
update-notifier
xubuntu-desktop
yelp

Downgrade the following packages:
ubuntu-docs [6.06.2 (now) -> 6.06.1 (dapper)]

Leave the following dependencies unresolved:
contact-lookup-applet recommends evolution (>= 2.0)
evolution-data-server recommends evolution (>= 2.0.0)
nautilus-data recommends nautilus (= 2.14.1-0ubuntu9)
ubuntu-docs recommends yelp
openoffice.org-evolution recommends evolution
gnome-session recommends gnome-panel
gnome-session recommends nautilus
gnome-terminal-data recommends gnome-terminal
gnome-games-data recommends gnome-games
gnome-panel-data recommends gnome-panel (= 2.14.2-0ubuntu1)
Score is -20286

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```

I don't use aptitude often enough. Any ideas on how to get the broken packages fixed (and get lsb_release to show 6.06.1)?
It's a bit hardcore. It's better to first try the --reinstall switch (that won't remove other stuff). I've updated the HOWTO post :

[http://www.ubuntuforums.org/showpost.php?p=1369334&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1369334&postcount=2)

---

### Post by vtel57 on 2006-08-13
I believe the corruption problems were caused by my attempt to restore a /home directory from the previous install of Ubuntu on this system. That's when everything went buggy... mea culpa, mea maxima culpa.

My current fresh install of 6.06.1 is moving along fine.

Thanks!

~Eric

> **ubuntu_demon said:**
> What kind of stability problems ? 

If you did a regular install and you have stability problems look for :

-heat (make sure it's not a heat problem. sometimes opening the case adds enough cool air for a system to become stable again)
-dust (make sure you clean your computer once in a while)
-check the memory (you can check it using the grub entry)
-try a different videocard

If it's stable after the installation but you have some problems after installing certain software then you might try my guide here :
[http://www.ubuntuforums.org/showthread.php?t=186792](http://www.ubuntuforums.org/showthread.php?t=186792)

---

### Post by llamakc on 2006-08-13
What confuses me about this issue is that the file /etc/lsb-release is provided by the package base-files:

```

ken@dothan:/etc$ dpkg -S /etc/lsb-release
base-files: /etc/lsb-release

```

One of the other lsb-* packages must write to this /etc/lsb-release file to update it. I have done the apt-get --reinstall of all of the lsb-* packages, as well as the ubuntu-minimal and -desktop metapackages. Nothing changed for me (even after a reboot).

FWIW I use apt-get instead of aptitude on most occasions.

---

### Post by mlind on 2006-08-13
> **llamakc said:**
> I just stumbled on this thread and noticed this on my system:

```

root@dothan:/home/ken# aptitude remove lsb-release --purge
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  launchpad-integration lsb-core ubuntu-minimal update-manager
The following packages will be REMOVED:
  lsb-release
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 81.9kB will be freed.
The following packages have unmet dependencies:
  update-manager: Depends: lsb-release but it is not installable
  launchpad-integration: Depends: lsb-release but it is not installable
  ubuntu-minimal: Depends: lsb-release but it is not installable
  lsb-core: Depends: lsb-release but it is not installable
Resolving dependencies...
open: 1273; closed: 2009; defer: 0; conflict: 14                               oThe following actions will resolve these dependencies:

Remove the following packages:
deskbar-applet
ekiga
eog
evince
evolution
evolution-exchange
evolution-plugins
file-roller
gaim
gcalctool
gconf-editor
gedit
gnome-app-install
gnome-applets
gnome-games
gnome-media
gnome-nettool
gnome-panel
gnome-system-monitor
gnome-terminal
gnome-utils
gnome-volume-manager
gthumb
gucharmap
hal-device-manager
language-selector
launchpad-integration
libgucharmap4
liblaunchpad-integration0
liblpint-bonobo0
lsb
lsb-core
lsb-cxx
lsb-desktop
lsb-graphics
nautilus
nautilus-sendto
python-gnome2-desktop
python-launchpad-integration
python2.4-gnome2-desktop
rhythmbox
serpentine
sound-juicer
synaptic
totem
totem-gstreamer
ubuntu-desktop
ubuntu-minimal
update-manager
update-notifier
xubuntu-desktop
yelp

Downgrade the following packages:
ubuntu-docs [6.06.2 (now) -> 6.06.1 (dapper)]

Leave the following dependencies unresolved:
contact-lookup-applet recommends evolution (>= 2.0)
evolution-data-server recommends evolution (>= 2.0.0)
nautilus-data recommends nautilus (= 2.14.1-0ubuntu9)
ubuntu-docs recommends yelp
openoffice.org-evolution recommends evolution
gnome-session recommends gnome-panel
gnome-session recommends nautilus
gnome-terminal-data recommends gnome-terminal
gnome-games-data recommends gnome-games
gnome-panel-data recommends gnome-panel (= 2.14.2-0ubuntu1)
Score is -20286

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```

I don't use aptitude often enough. Any ideas on how to get the broken packages fixed (and get lsb_release to show 6.06.1)?


Use this instead
```

sudo dpkg -P --force-depends *package*

```

---

### Post by llamakc on 2006-08-13
root@dothan:/home/ken# dpkg -P --force-depends lsb-release
dpkg: lsb-release: dependency problems, but removing anyway as you request:
 ubuntu-minimal depends on lsb-release.
 update-manager depends on lsb-release.
 launchpad-integration depends on lsb-release.
 lsb-core depends on lsb-release.
(Reading database ... 180402 files and directories currently installed.)
Removing lsb-release ...
Purging configuration files for lsb-release ...
root@dothan:/home/ken# apt-get clean
root@dothan:/home/ken# apt-get install lsb-release
Reading package lists... Done
Building dependency tree... Done
Package lsb-release is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  base-files

No way in h3!! am I forcing an install of base-files. So after doing the above suggestion I'm stuck with:

```

root@dothan:/home/ken# apt-get install lsb
Reading package lists... Done
Building dependency tree... Done
lsb is already the newest version.
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  launchpad-integration: Depends: lsb-release but it is not installable
  lsb-core: Depends: lsb-release but it is not installable
  ubuntu-minimal: Depends: lsb-release but it is not installable
  update-manager: Depends: lsb-release but it is not installable
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
root@dothan:/home/ken# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following packages will be REMOVED
  deskbar-applet ekiga eog evince evolution evolution-exchange
  evolution-plugins file-roller gaim gcalctool gconf-editor gedit
  gnome-app-install gnome-applets gnome-games gnome-media gnome-nettool
  gnome-panel gnome-system-monitor gnome-terminal gnome-utils gthumb gucharmap
  hal-device-manager language-selector launchpad-integration libgucharmap4
  liblaunchpad-integration0 liblpint-bonobo0 lsb lsb-core lsb-cxx lsb-desktop
  lsb-graphics nautilus python-gnome2-desktop python-launchpad-integration
  python2.4-gnome2-desktop rhythmbox serpentine sound-juicer synaptic totem
  totem-gstreamer ubuntu-desktop ubuntu-minimal update-manager update-notifier
  xubuntu-desktop yelp
0 upgraded, 0 newly installed, 50 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 148MB disk space will be freed.
Do you want to continue [Y/n]?

```

Yay beer!

---

### Post by llamakc on 2006-08-13
Note to self: less beer, more clean sources.list before system administration.

---

### Post by ubuntu_demon on 2006-08-13
the package lsb is not installed on default. 

I've updated my howto a bit. Try it. We'll gradually improve it together :)

---

### Post by llamakc on 2006-08-13
I have them now. Had to apt-get lsb-release again.

---

### Post by ubuntu_demon on 2006-08-13
> **llamakc said:**
> Note to self: less beer

LOL :-D

> **llamakc said:**
> 
 more clean sources.list before system administration.

That's the first thing to try :)

Did you solve your problem ?

---

### Post by llamakc on 2006-08-13
Yep, I'm good to go now. 6.06.1 is now showing.

---

### Post by ubuntu_demon on 2006-08-13
> **llamakc said:**
> Yep, I'm good to go now. 6.06.1 is now showing.
Great. So the sources.list was the problem ?

---

### Post by llamakc on 2006-08-13
Probably. I saw during one of the apt-get dist-upgrades that base-files needed interaction from me to overwrite /etc/lsb-release.

That didn't occur until I cleaned up my sources.list.

What concerns me is the act of doing `apt-get dist-upgrade` with dapper sources.list SHOULD move me up to the most recent version. That was always the Debian way (provided the sources.list was correct). Ubuntu uses that same approach, correct?

---

### Post by ubuntu_demon on 2006-08-13
> **llamakc said:**
> Probably. I saw during one of the apt-get dist-upgrades that base-files needed interaction from me to overwrite /etc/lsb-release.

That didn't occur until I cleaned up my sources.list.

What concerns me is the act of doing `apt-get dist-upgrade` with dapper sources.list SHOULD move me up to the most recent version. That was always the Debian way (provided the sources.list was correct). Ubuntu uses that same approach, correct?

correct. But you probably messed something up somehow. Maybe you should be a little more conservative regarding your sources.list.

---

### Post by llamakc on 2006-08-13
Here's what I have right now. I do use the wine packages and I occasionally toy with Opera.

```

ken@dothan:~$ cat /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://packages.freecontrib.org/plf/ dapper free non-free

deb http://wine.sourceforge.net/apt/ binary/

deb http://deb.opera.com/opera etch non-free

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```

---

### Post by ubuntu_demon on 2006-08-14
> **llamakc said:**
> Here's what I have right now. I do use the wine packages and I occasionally toy with Opera.

```

ken@dothan:~$ cat /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://packages.freecontrib.org/plf/ dapper free non-free

deb http://wine.sourceforge.net/apt/ binary/

deb http://deb.opera.com/opera etch non-free

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```
Don't use PLF it is shutting down. They currently list no important packages which aren't available otherwise.

You should use dapper-commercial for opera.

There's a better wine mirror available.


my recommended Dapper sources.list which is probably used by a lot of people :
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

That being said. I don't think that your sources.list is the cause unless you had some other strange repositories (you don't have to use them for long). But better be conservative.

---

