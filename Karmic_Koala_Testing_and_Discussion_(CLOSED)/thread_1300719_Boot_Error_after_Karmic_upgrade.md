---
title: "Boot Error after Karmic upgrade"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Buuntu on 2009-10-25
So yesterday I decided I was going to go ahead and give Karmic a try.  I started the upgrade and left it running over night while I went to a friend's house.  When I came back the next day, the screen was black and I was forced to manually restart.  When I boot up my partition now, I get this error:

```
mountall: symbol lookup error: mountall: undefined symbol: udev_monitor_filter_add_match_subsystem_devtype
init: mountall main process (891) terminated with status 127

```
Booting in recovery mode has the exact same result.

Btw, my mom apparently got on yesterday (not sure if the upgrade was done) and tried to log into her account while it was on mine.  Upon doing so, she said the screen just went black, which is how I found it this morning.

Is there something I can do without having to do a clean install?  I have a month-old backup, but I would rather not have to use it if I don't have to.

---

### Post by LewRockwell on 2009-10-25
Odds are that the fault occurred before your mother attempted to use the device.

.

---

### Post by Buuntu on 2009-10-25
Yeah, I figured that much.

---

### Post by diaco on 2009-10-25
there is a solution here:
[http://ubuntuforums.org/showpost.php?p=8061705&postcount=1](http://ubuntuforums.org/showpost.php?p=8061705&postcount=1)
take a look!

---

### Post by Shpongle on 2009-10-25
you could try repair broken packages with the recovery partition of with a live cd that help with an issue i had similar to yours

---

### Post by Buuntu on 2009-10-25
Ok I tried a few commands to try and fix the broken packages, but each had its own set of errors.

'apt-get dist upgrade' had a few lines about not being able to fetch data (relating to karmic-security).  'apt-get update' and 'apt-get upgrade' both had errors about: ```
libx-ext-dev
rsyslog
ubuntu-minimal
console-setup
xserver-xorg
```

'dpkg --configure -a' didn't do anything either... :(

Thanks for the help, but do you have any other ideas?

---

### Post by sandyd on 2009-10-25
> **Buuntu said:**
> Ok I tried a few commands to try and fix the broken packages, but each had its own set of errors.

'apt-get dist upgrade' had a few lines about not being able to fetch data (relating to karmic-security).  'apt-get update' and 'apt-get upgrade' both had errors about: ```
libx-ext-dev
rsyslog
ubuntu-minimal
console-setup
xserver-xorg
```'dpkg --configure -a' didn't do anything either... :(

Thanks for the help, but do you have any other ideas?
looks like you got a half-upgrade system.

can you post your /etc/apt/sources.list ?

apt-get update should not really be sending out errors.

---

### Post by LewRockwell on 2009-10-25
> **carlee said:**
> apt-get update should not really be sending out errors.

{{chuckle}}

.

---

### Post by Buuntu on 2009-10-25
Oh, I just realized it's because my wireless card doesn't work out of the box - I had forgotten that.  I'll try connecting directly to my router and report back on how things went.

---

### Post by sandyd on 2009-10-25
> **Buuntu said:**
> Oh, I just realized it's because my wireless card doesn't work out of the box - I had forgotten that.  I'll try connecting directly to my router and report back on how things went.
in that case, i can guess what likely hapenned.

the wireless interface died in the middle of the installation, but ubuntu ignored the 404 faliures and continued installing the rest of the packages.

---

### Post by Buuntu on 2009-10-26
*UPDATE ON HOW THINGS WENT*

So I managed to  hook up to my router and connect to the internet.  Sadly, that didn't really fix it...

This is what I tried in the terminal:
```
sudo mount /dev/sda3 /mnt
sudo chroot /mnt
apt-get update
apt-get dist-upgrade
```and even tried
```
dpkg --configure -a
apt-get dist-upgrade
```While 'apt-get dist-upgrade' did seem to install some things, there were still about 603 MB that weren't installed (I think there was over 800+ MBs before).

The errors included in 'apt-get dist-upgrade' were:
```
Errors were encountered while processing:
/var/cache/apt/archives/mysql-server-5.0-5.1.30really5.0.873-0ubuntu3.i386.deb
E: sub-process /usr/bin/dpkg returned an error code(1)
```Another thing that I think might be the problem still is the grub menu.  It doesn't seem to have changed and I'm still having to select the old kernel.  Could this be the problem?  If so, how do I update it?

---

### Post by Buuntu on 2009-10-26
I tried running update-grub, but the menu.lst file still shows the old kernel.  Maybe I'm wrong in assuming that an update to Karmic also updates your kernel?  By the way, the current kernel I use is 2.6.28-16.

---

### Post by Buuntu on 2009-10-27
Ok so I have made SOME progress.  Basically, I chrooted into my partition and ran apt-get dist-upgrade from there, which fixed most of it I think.  Now grub shows the correct kernel, and I'm able to almost boot up, but it freezes before I reach gnome.  Here is the output from 'apt-get dist-upgrade': [http://paste.ubuntu.com/303122/](http://paste.ubuntu.com/303122/)

Any ideas?

---

### Post by diaco on 2009-10-28
i had this problem too.
after 3 days searching, couldn't find any solution and installed a new ubuntu.
it isn't nice if updating the os may destroy it

---

