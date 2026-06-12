---
title: "Big problems updating packages AGAIN"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by ExemplarUbuntu on 2006-12-18
Four days ago I tried to update a few packages. It should have been a trivial exercise with no impact on the work being done on the machine but not for the first time it caused major problems.

Last year the machine was out of action for about 5 days while I repeatedly installed, de-installed and re-installed dozens of packages until eventually it booted to the desktop. Not a pleasant experience and one I was keen not to repeat, this is why I had not updated anything for such a long time. Most of the installation was Badger but it could have been a mixture of Badger and earlier versions, after 5 days I didn't care, it booted again and we could get on with some work.

Last Friday I stupidly tried to update just a few harmless packages. It seemed to be ok but I noticed that I couldn't sudo gedit any files. The gedit window didn't open, it just hung waiting. I couldn't run synaptic from the menu either, I had to sudo synaptic. I updated gedit, a big mistake, it tried to update quite a few packages and this seems to have caused a lot of the problems.

When I rebooted it seemed to have lost a some drivers since it didn't recognise the network adapters. Without any network setting it wouldn't start the desktop. IIRC this is an X problem but frankly it just shouldn't happen, it should always do enough to enable X to start.

So now it was reduced to the trog command line and no obvious way to rollback any of the changes. Using a PC I was able to burn a CD with an archive copy of Badger, that was lucky otherwise I may as well have given up on it and lost a lot of work.

Having modified the sources.list (why is this step even needed ?) I was able to try to fix the problem. After a few hours I managed to get the desktop login page to appear but after the login it just presented a brown screen with a non-functioning terminal window and an error message in it. At one point I even tried booting from the CD in order to fix the issues but the installation insists on trying to re-partition the HD even if there is a valid partition set-up, why? It won't let you proceed if it hasn't wiped everything first.

At this point I had 2 kernels installed 2.6.10.5 and 2.6.12.9 However only the former would work, the latter booted into busybox since it didn't seem able to read vital info from the partition.

After quite a lot more time spent trying to install packages it would go no further. Aptitude insists on trying to remove 2.6.10 and then complains that removing the working kernel is a really bad idea. Aptitude says that 2.6.10 is broken due to missing initrd-tools but that package isn't available.

Due more to luck than judgement 2.6.10 was now recognising the network adapters, I don't know why the situation had improved. So I decided to manually configure the network adapters not something that I keep at the front of my mind but after a few attempts and a dozen more reboots it configured the adapters during the boot.

This meant I could try updating online but it still wouldn't locate initrd-tools and keeps trying to remove the only working kernel on the system !

To say the least I am not impressed by any of this. If it was the first time it would be bad enough but after last years disaster trying to update to Badger and now such a big problem just updating a few packages I don't want to risk any more updates.

Edit : last years problems are here [http://www.ubuntuforums.org/showthread.php?t=85319](http://www.ubuntuforums.org/showthread.php?t=85319)

---

### Post by hal10000 on 2006-12-18
I don't know what happens during your last years update, but in general it's a good idea to keep your system up-to-date, and it usually works fine.
Sine you didn't update anything for such a long time, maybe many of your dependencies are not correct anymore.
You shoud first update your package list. In a terminal window type [COLOR="Red"]sudo apt-get update[/COLOR] and then install the packages you need to upgrade. Maybe if you do so, there are many other packages to be updated too; be courageous, do it.

---

### Post by ExemplarUbuntu on 2006-12-18
I just tried that, I am sure I tried it before. It connects to dapper updates and then says "done". It does nothing as far as I can tell.

This is the sources.list which I am sure needs some changes:

deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

##deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
###deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted

# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

## deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted
###deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

###deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

##deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
##deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

---

### Post by ExemplarUbuntu on 2006-12-18
I added dapper main restricted to the sources and re-ran update:

Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release [34.8kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages [619kB]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages [4571B]
Fetched 659kB in 10s (61.2kB/s)
Reading package lists... Done

running it again produces no more updates. Synaptic still wants to remove my only working kernel.

Currently apache2 isn't working, neither is mysql. It has deleted some vital parts somewhere along the way.

---

### Post by ExemplarUbuntu on 2006-12-18
I did a google search for initrd and found out which repository it's in and added it to sources

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted

Installing this means that Synaptic no longer wants to delete the 2.6.10 kernel. So hopefully I can now update some more of the system and try to fix all the non-working packages.

I'd still like to be able to boot with the newer kernel, maybe it will now.

---

### Post by hal10000 on 2006-12-18
I guess the latest ubuntu-kernel is 2.6.17. You should install this.

---

### Post by ExemplarUbuntu on 2006-12-18
The latest one showing in synaptic here is 2.6.15 so I installed that. I wasn't sure if it would make matters worse, I don't have any faith in the update system anymore.

It did install without removing 2.6.10 but it wouldn't boot. It got as far as uncompressing and the booting message, the screen flickered, re-drew the same and nothing else happened. The keyboard still worked but it didn't boot, not even into busybox.

If the kernel has dependancies why did they not get installed ?

Thanks for the help, btw.

Peter

---

### Post by ExemplarUbuntu on 2006-12-18
Ok, this is the current situation:

2.6.15 will not boot Ubuntu
2.6.12 boots into busybox

2.6.10 is still the only working kernel but it has minor problems:

1. modprobe produces a couple of errors during boot-up
2. the network eth0 device is always disabled after boot. The settings are retained, I just manually activate the port.
3. apache2 is installed but it cannot find the apache2 command to start it
4. usb memory sticks are not mounting automatically any more

I've updated a few packages, most of the system is only a little out of date 1.10.5 instead of 1.10.7 etc.  I am avoiding x/gtk/gnome/nautilus as this is what has caused the problems with the previous updates.

Any suggestions ? If I can make the network configure during boot-up, it might fix other issues.

---

### Post by SFDD on 2006-12-18
> **ExemplarUbuntu said:**
> I don't want to risk any more updates.

Just for the record, dont' feel bad about not keeping your system up to date. Despite that Dapper update a few months back that "killed" so many nVIdia-based machines--my own two included--I have enabled the System Update to keep my machines up to date. Yet that last kernel update worried me. While I do perform each update, I wait to see if others have trouble first. Sure enough, there were reports, so I was concerned. Eventually, I figured I'd give it a shot and sure enough, it killed one of my machines with the nVidia problem users were reporting, PLUS a kernel panic situation that was not oneof the more "popular" disasters of that upgrade.

I was only a few moments away from an install of SUSE when I read a thread in which someone offered a fix to the kernel issue, which was necessary so I could go in and see if I also needed the fix for the nvIdia issue. (Which, of course, I did.)

So, I feel for you and completely agree: I fear Ubuntu system updates now. For all the bad reputation Windows has, I've never once had a Windows update kill my system. I guess I'm lucky in that regard in Windows, but unlucky in that regard with Ubuntu. But like so many others, I'm trying to ween myself away from Ubuntu. And what I thought would be a waiting period until apps came up to speed, I'm realizing now is a waiting period until the OS update become reliable too.

Between these issues and Firefox 2.0 on Edgy, I'm not seeing this "reliability" Linux is supposedly known for. (And, yes, even without Flash installed Firefox crashes regularly on me.)

So don't feel bad if someone says your current woes are due to not upgrading regularly. Even some of us who have find ourselves in similar situations.

---

### Post by ExemplarUbuntu on 2006-12-18
> **SFDD said:**
> Just for the record, dont' feel bad about not keeping your system up to date.

It's ok, I don't feel at all bad ;-)

I don't really have time to follow the current status of Ubuntu and the problems or otherwise with the various releases. I just update and expect it to work, I don't expect non-working stuff to be available. This is a result of using Freemint on my Atari at home, It's never let me down and it's only written by an handful of guys. I've been lucky or is that cautious with Windows too.

When Ubuntu works, it's fine but breaking itself so catastrophically with a few package updates is not good. I need to get Apache working again asap and that doesn't look likely at the moment.

---

### Post by bulldog on 2006-12-18
The problem is,you only read about the users who have trouble with the update,so it seems that everyone has issues.
But the fact is that the majority of users have no problems at all,but they don't put a post on the forum that their updates went well.

I myself run Edgy and have had no issues with the upgrades,even though I have a nVidia graphics.
I had some trouble with Firefox in the beginning with Edgy,but after creating a new profile it runs smoothly.

---

### Post by ExemplarUbuntu on 2006-12-18
I haven't read about any users having trouble except when reading this forum to try to find out how to recover my system when it falls in a heap.

I wasn't starting an argument based on other peoples comments just stating what happened when I tried to update a few packages.

Currently I am trying to fix apache2, it is now at the latest version but apache2-mpm-prefork, which I need, doesn't like that so once again deadlock. Synaptic doesn't offer to install the correct required version. I don't even know why apache2 was updated.

How do I downgrade the version ?

---

### Post by ExemplarUbuntu on 2006-12-18
/etc/network/run is a broken link. It did point to /dev/shm/network but that file no longer exists.

This may explain why the network isn't configuring during boot.

---

### Post by hal10000 on 2006-12-18
When looking into your /etc/apt/sources.list, I see that you have mixed sources from Breezy Badger and dapper. I suggest either changing the dapper entries to breezy and then downgrade your system (after changing sources.list do [COLOR="Red"]sudo apt-get update[/COLOR]. The other way is to comment out the breezy entries and do a clean upgrade, but I guess you prefer the former.
Whatever you do, you should have a proper sources.list or you will surely run into problems, not only with your apache installation.

---

### Post by ExemplarUbuntu on 2006-12-19
Thanks, I wasn't sure if that was a sensible thing to do or not. I started adding more to try to fix the earlier problems and it did work to some degree.

I'll comment out everything except breezy and see how I get on.

sudo apt-get update doesnn't seem to do much so I had a look at upgrade but didn't actually commit it.

$ sudo apt-get update
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [191B]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Fetched 2B in 1s (1B/s)
Reading package lists... Done

Has this changed anything ?

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  jade mysql-server python-twisted python2.4-opengl python2.4-twisted
  update-manager
The following packages will be upgraded:
  dhcp3-client dhcp3-common docbook docbook-dsssl evince gksu iptables
  language-selector libasn1-6-heimdal libc6 libc6-dev libc6-i686 libdb4.1
  libdbd-mysql-perl libdbi-perl libgksu1.2-0 libgl1-mesa libgl1-mesa-dri
  libglu1-mesa libgnome2-canvas-perl libgnutls11 libgphoto2-2 libgphoto2-port0
  libgssapi1-heimdal libkrb-1-kerberos4kth libkrb5-17-heimdal libmad0
  libmysqlclient10 libnautilus-extension1 libnspr4 libnss3 libpng10-0 libpq3
  libpq4 libroken16-kerberos4kth libtotem-plparser0 libungif4g modutils
  mysql-client nautilus nautilus-data pmount pwgen python-apt
  python-gnome2-extras python-opengl python2.3 python2.3-numeric python2.3-tk
  python2.3-xml python2.4-gnome2-extras python2.4-twisted-bin totem
  totem-gstreamer xaw3dg xkeyboard-config xlibs-data
57 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 37.8MB of archives.
After unpacking 9626kB disk space will be freed.

Do you want to continue [Y/n]? n

---

### Post by ExemplarUbuntu on 2006-12-19
Well I think 've now managed to get it up-to-date as far as Breezy is concerned.
There are still 2 problems during boot, apm and another modprobe fail.

The network  is still down once booted even though it says the network configures and comes up during the boot.

More of a problem is that Apache2-common 2.0.55-4ubuntu2.1 is installed but running apache2 at the cli produces nothing.

++ Fixed this by synpatic removing apache2-common and apache2-utils and the re-installing them with apache2-mpm-prefork.
++ Also had to re-install libapache2-mod-php4 and it's updated dependancies from the security repository.

The network device still says it is configured at boot but *isn't* actually activated, very annoying since I have to go to the machine and manually start it. It may be because the network devices are de-configureed at shutdown, I am not sure if this is a new feature.

USB mem-sticks aren't detected either. This may be a config thing but it's been so long since I originally got this machine working.

---

### Post by ExemplarUbuntu on 2007-01-03
I still have the network and usb issues.

Anyone ?

---

### Post by ExemplarUbuntu on 2007-01-10
Network issue mostly fixed, it starts at boot now, despite an error.

I think the reason that the other 2 kernels do not boot is down to udev reporting "wrong" drive names. I suspect that eventually I will have to do a full upgrade to clear these issues and no doubt gain a few new ones ;-)

Thanks for the help everyone.

---

