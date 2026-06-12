---
title: "Bug in latest update! (affects Shut Down and Volume)"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by danielgrosvenor on 2010-09-03
There's some bug or other error in the updates I've just installed.

Note: I run Update Manager very frequently (almost daily).  The last time I ran it was 2 days ago, so this bug can only have been released into updates today or yesterday.

I ran it this evening and there were quite a lot of new updates (around 50mb in total), and I installed them all without really checking to see what they were - but as I'm new to Linux I don't exactly have any weird or rare software running on my laptop, so they only would have been for Ubuntu itself or some very common programs.

After installing it required a reboot.  Upon booting up again, the volume icon has turned to 'Mute All' and I am unable to turn my laptop off.  Telling it to shut down simply causes the screen to go black for a couple of seconds and then return to the login screen.

I also notice that the Suspend/Hibernate options have disappeared, and I now only have the option to Log Out, Restart or Shut Down.


{As I'm new to Linux I have no idea how best to proceed, or even how to officially 'report' this if indeed it is a bug contained in one of the updates.  Any guidance people can offer me would be appreciated.}

---

### Post by ajgreeny on 2010-09-03
As far as I can see, the packages that have been upgraded on my system since the last day of August have been:-

Upgraded the following packages:
gwibber (2.30.1-0ubuntu1) to 2.30.2-0ubuntu1
gwibber-service (2.30.1-0ubuntu1) to 2.30.2-0ubuntu1
chromium-browser (5.0.375.125~r53311-0ubuntu0.10.04.1) to 5.0.375.127~r55887-0ubuntu0.10.04.1
chromium-browser-inspector (5.0.375.125~r53311-0ubuntu0.10.04.1) to 5.0.375.127~r55887-0ubuntu0.10.04.1
wget (1.12-1.1ubuntu2) to 1.12-1.1ubuntu2.1
aptdaemon (0.11+bzr345-0ubuntu4) to 0.11+bzr345-0ubuntu4.1
libgudev-1.0-0 (1:151-12) to 1:151-12.1
libudev0 (151-12) to 151-12.1
mountall (2.15) to 2.15.1
python-aptdaemon (0.11+bzr345-0ubuntu4) to 0.11+bzr345-0ubuntu4.1
python-aptdaemon-gtk (0.11+bzr345-0ubuntu4) to 0.11+bzr345-0ubuntu4.1
udev (151-12) to 151-12.1
usb-creator-common (0.2.22) to 0.2.22.1
usb-creator-gtk (0.2.22) to 0.2.22.1
bogofilter (1.2.1-0ubuntu1) to 1.2.1-0ubuntu1.1
bogofilter-bdb (1.2.1-0ubuntu1) to 1.2.1-0ubuntu1.1
bogofilter-common (1.2.1-0ubuntu1) to 1.2.1-0ubuntu1.1
libwww-perl (5.834-1) to 5.834-1ubuntu0.1
[COLOR=Red]linux-headers-2.6.32-24 (2.6.32-24.41) to 2.6.32-24.42
linux-headers-2.6.32-24-generic (2.6.32-24.41) to 2.6.32-24.42
linux-image-2.6.32-24-generic (2.6.32-24.41) to 2.6.32-24.42
[COLOR=Black]linux-libc-dev (2.6.32-24.41) to 2.6.32-24.42[/COLOR][/COLOR]

Of those the only ones that might have had any detrimental effect on a system would be the kernel upgrades.

Assuming you have an older kernel showing in grub, try booting to it and see if your system runs properly with that.  If you don't see a grub menu, hold shift when you switch on and a menu should appear.

---

