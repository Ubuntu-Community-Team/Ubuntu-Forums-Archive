---
title: "hard drive sleep, power-down, spin-down"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by sem7ex on 2009-11-14
Hi everybody,

i have setup a (low power) htpc / nas running ubuntu 9.04 (sucessfully updgraded to 9.10). It has 2 mirrored ext3 hdd's acting a nas. The problem is i can't manage to get the hdd's to spin down after a certain amount of time. I dont't even know if this is possible using ext3. I figured out with iotop that kjournald is always doing some IO. Modifiying the update interval didn't solve the problem. I have read and tried a lot of things but nothing helped. I probably need IO on the hdd's in less than 5% of the time.

What is in your oppinion the best solution for this?

Installing on a usb stick? How long does a usb stick resist to an OS?

Using another file system? NTFS is not really an option because it's really slow and some applications don't work on ntfs.

Don't get me wrong, i'm no windows fan (anymore) but this was possible in windows 95. That is .. 1.4 decades ago. I can't remember if also in 3.11.

Thanks for all your sugestions.

---

### Post by grandsatrap on 2009-12-06
I am interested in this too.

I would like my hard drives to power down all night - when no one is using the server. Of course, there are is still cron.daily ...

I want my server to always be on, but I only use it for a maximum of 2 hours per day - at unpredictable times.

I just don't understand why the harddrives can't be idled. Do I need to put my operating system in a RAM drive?

---

