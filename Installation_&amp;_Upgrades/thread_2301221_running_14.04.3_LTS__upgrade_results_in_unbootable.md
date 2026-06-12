---
title: "running 14.04.3 LTS / upgrade results in unbootable machine (missing /dev/sda1)"
date: 2015-10-31
forum: Installation &amp; Upgrades
---

### Post by John_Klassa on 2015-10-31
I'm on rackspace, running 14.04.3 LTS (GNU/Linux 2.6.35.4-rscloud x86_64).  Things have been great for months, since I upgraded from (I think) 10.04 via a multi-step upgrade process.  Point is, I've done the usual:

[INDENT]apt-get update
apt-get upgrade
apt-get dist-upgrade
[/INDENT]

and the like, repeatedly, for months now.  As of a couple of weeks ago, however, my attempts to "apt-get upgrade" end in this error:

[INDENT]cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
cryptsetup: WARNING: could not determine root device from /etc/fstab
[/INDENT]

whereupon I can no longer boot my system because (according to the console), "/dev/sda1 does not exist" (and I'm thrown into a BusyBox [initramfs] shell).**[B][B][B]**[/B][/B][/B]**[B][B][B][B]**[/B][/B][/B][/B]**[B]**[/B]

After recovering from a backup image, I set about to try to upgrade, again, while avoiding this problem.  (I actually created a new VM from my backup imagine, so that I could screw around and not affect my "production" box.)

So, as I never asked for or set up "cryptsetup", and since that was implicated in the error message, I got onto a freshly-restored-from-image copy of my system, and did "apt-get remove cryptsetup", followed by "apt-get update" and "apt-get upgrade", repeatedly, until there was nothing new to install.  No errors this time.  However, when I reboot this (dummy) system, I get the same error that my primary system hits (the "/dev/sda1 does not exist").

I'm been unsuccessful in figuring this one out, using forums and google searches.

My /etc/apt/sources.list has only these in it:

[INDENT]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty main restricted universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates main restricted universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted universe
[/INDENT]

so it's not like I'm running esoteric software.

This ring a bell with anyone?  I'm well and truly stuck.

---

### Post by John_Klassa on 2015-10-31
Incidentally, now, I do see this at the end of the upgrade process (in lieu of the cryptsetup errors):

update-initramfs: Generating /boot/initrd.img-2.6.35.4-rscloud
grep: /boot/config-2.6.35.4-rscloud: No such file or directory

So, perhaps there's something of rackspace's that's also coming into play (they've got backup agents and the like)...?

---

