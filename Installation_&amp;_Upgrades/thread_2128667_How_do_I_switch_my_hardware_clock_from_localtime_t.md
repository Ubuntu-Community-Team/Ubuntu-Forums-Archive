---
title: "How do I switch my hardware clock from localtime to UTC"
date: 2013-03-23
forum: Installation &amp; Upgrades
---

### Post by daveee on 2013-03-23
I originally set my Xubuntu 12.04 install to store localtime to the hardware clock, because I thought that would require the minimum amount of hassle for dual-booting with Windows.

But after I read that it was easy to switch Windows to handle a UTC system clock here: [https://wiki.archlinux.org/index.php/Time#UTC_in_Windows](https://wiki.archlinux.org/index.php/Time#UTC_in_Windows)

and read about the impact of a localtime system clock on Linux here: [http://tldp.org/HOWTO/Clock-2.html](http://tldp.org/HOWTO/Clock-2.html)

I decided to switch my computer's hardware clock (RTC) to UTC.  Unfortunately, although I know I selected that option when installing Xubuntu, I didn't find any mention of how to make this change here: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

Eventually I figured out, the change that needed to be made was:

1) Confirm the correct timezone is set using dpkg-reconfigure tzdata
2) Set the correct time using System=>Time and Date
3) Push this time/date to the hardware clock (RTC) using hwclock --utc --systohc
4) Edit /etc/default/rcS and change utc=NO to utc=YES

I'm not pretending to have this all figured out, but thought I'd try to share my learnings with anyone else who was unable to figure out that /etc/default/rcS was useful in whether UTC or localtime was used with the hardware/RTC clock.

---

### Post by Irihapeti on 2013-03-23
If you already have Windows installed and then install Ubuntu, it assumes that Windows is using local time (which most people do, after all) and sets "UTC=no" in /etc/default/rcS

I ran into this problem last year when I was doing a lot of test installations and eventually discovered it was supposed to do that. 
[https://bugs.launchpad.net/ubuntu/+source/clock-setup/+bug/946132](https://bugs.launchpad.net/ubuntu/+source/clock-setup/+bug/946132)

Just something to keep in mind. If you know about it, you can then fix it manually. If not, it can drive you silly.:)

---

