---
title: "Ubuntu 7.10 The Good the Bad and the Ugly."
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by boudicca on 2007-10-20
Where do I start.....well .... I was on Wednesday a casual 7.04 user with compiz and vmware 5.5 running my old xp machine as my installed features and most importantly using my install for browsing and my media over the digital out.

Dual core P4 1GB, Asrock 775 Dual-vsta, 2 Sata Hard Disks, Nvidia 7600GS (Envy Drivers) and Audigy.....oh and Realtek 1000T ethernet.

Here comes 7.10....oh wonderful....and its upgradable apparently.......So I went for the Over the network upgrade.

All went fine until the reboot......

Was stuck in a vicious circle of Bullet Proof X......No network via the Gigabit port and having to shutdown bulletproof just to get back init 3 to bring the network back up using the built in 100meg ethernet and IFUP with a bit of mucking about was able to get the Gui back with  dpkg-reconfigure xserver.xorg, but on every logout and reboot, bulletproof would put me back in the cannot detect cycle.

The next day, I tried the new Envy drivers.....nada kept....complaining about couldn't install this add that....removed drivers,.....still no joy at the same time, network up network down up down.....What a mess.

So my experience of the upgrade is "DONT!"

Next I downloaded the CD, ran the setup installed a new ext3 partition as root.....good thing I had the space on my disks........

Installing clean was a dream......drivers....one click on the gui...sorted.....on click on the audio sorted.....gigabit ethernet sorted.....Compiz and more importantly once I downloaded Gnome Compiz Manager.....Cubing again...wonderful.

Now.....VMware........oh dear....compiler errors.....ouch.....so I got out the new version 6.02 from the website.....Voila.....vmware sorted.......

Basically my lesson was don't upgrade.....too painful.....just reinstall......good thing my main stuff is elsewhere or I would have been swearing like a trooper........

Shaz

---

### Post by sloggerkhan on 2007-10-20
My experience with upgrade is that it doesn't work well unless you've kept your install very very 'vanilla'

---

### Post by leon_mcnichols on 2007-10-20
Yea? Well I get 

E: /var/cache/apt/archives/kitchensync_4%3a3.5.7enterprise20070926-0ubuntu2_i386.deb: trying to overwrite `/usr/share/apps/ksync/ksyncui.rc', which is also in package ksync

how the smeg am I supposed to fix this one? 

Kicks back and calms down with a thing of :popcorn:

---

### Post by leon_mcnichols on 2007-10-23
You mean to honestly tell me no one has a clue about this issue?:confused:

---

### Post by ssam on 2007-10-23
looks like kitchensync and ksync both have a file with the same name/path. try uninstalling one or both of them, and see if the upgrade works.

i had a look in lauchpad and found this [https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/133944](https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/133944)

---

