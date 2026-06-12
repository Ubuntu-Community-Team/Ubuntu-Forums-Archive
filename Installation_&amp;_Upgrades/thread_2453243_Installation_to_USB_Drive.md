---
title: "Installation to USB Drive"
date: 2020-11-05
forum: Installation &amp; Upgrades
---

### Post by Jay_N on 2020-11-05
Hi fellow Ubuntu Studio users!
I am still using Ubuntu 12.04 on my old computer with a dual boot to Windows 7. In order to not disturb my ancient system I chose to install Ubuntu Studio 20.04.1 to an external hard drive which uses usb 2.0. 
I wanted to try out the newer version before I upgrade to a new computer, but didn't want to have to upgrade my old system. 
Here's my dilemma.
If I try to put this external system into hibernate or sleep mode (I can't remember what it's called - using my old system at the moment), it will do it but will almost immediately turn back on. 
If I try to restart, it will shut down the operating system (Ubuntu Studio 20.04.1) but doesn't restart - I get a black screen with a cursor at the upper left corner. I have to manually press my power button and restart that way. 
I recently ran the software update which needed a restart and I had to manually do it. I now receive system error messages upon login. 
Sometimes at the login screen if my system has sat undisturbed for a while it will just freeze at the password screen with a message something like 'verifying password' which never finishes the login and I also have to manually restart. 
I have a 64 bit system. Everything else seems to run fine on the external system.

Thanks for any advice / help you can offer.

---

### Post by C.S.Cameron on 2020-11-06
Did you make a Full install to your USB drive, or did you make a Persistent install?

You should not do a software update to a Persistent install as it may fill your casper-rw or writable persistence file or partition. This will leave your USB unbootable. A upgrade will not be possible.

If you did a Full install to the external drive, updates and upgrades should work okay.

---

### Post by charlie-ramirez-anima-st on 2020-11-06
The Suspension problem and the immediate wake-up, sometimes it is only a "bug", particularly if you use a logitech USB mouse (at least in my case) and if you have any object on the laptop's touchpad, or it is dirty. (windows filters all non-finger objects but apparently linux doesn't so any object on top is detected as a ghost finger)


-If you use an external mouse, try to leave with the sensor facing up, (since it is very sensitive and sometimes the minimum vibration wakes up the system)


-Now it could be due to the external disk and that it wakes up the system to avoid failures by rebooting or connecting it

Regarding the installation, some updates. particularly, when you jump between versions or change distros relatively frequently, some settings conflict, so it might be useful to make a backup of your files that are in / home (and custom settings of some apps in "/" if you have them) and do a clean installation (formatting partitions).


[There are some libraries that were discontinued particularly python libraries and repositories that have changed or no longer have an update for versions after 18.04 or are discontinued so that may be the problem] (puddletag also stopped working after 18.10)

---

### Post by Jay_N on 2020-11-06
Hello,
Yes I did a full install. I am using a 1 TB external usb drive. I have 500 GB allocated for this operating system on it. I have also partitioned the drive for / /home boot and swap. I can deal with these issues, as this external system is somewhat temporary, but I'd like to solve them if I can. My / partition is 20 GB, my /home is around 450 GB, my boot partition is 512 MB and the swap is 8GB.

---

### Post by C.S.Cameron on 2020-11-06
Have you tried changing from the old 12.04 bootloader to the new 20.04 bootloader or vice versa?

---

