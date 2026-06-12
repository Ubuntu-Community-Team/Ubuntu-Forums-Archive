---
title: "Init file missing - 13.04 new install"
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by WinkingFrog on 2013-05-31
Hi all, hopefully someone can help out a Linux newbie here (and yes, I have done some searching before posting:P)

I have spent some time having a good play with a USB live distro prior to making the switch, but soon decided to completely change my Compaq Presario CQ61 laptop over to Ubuntu. I have now run through the installation of 13.04 64bit twice, stopping in between to clear down the partitions thinking that the left over guff from Windows/Recovery might have caused this error - but it's back again, exactly the same.

After install I reboot from the live distro and am faced with a blank purple screen and flashing caps lock light. So I tried to follow the advice for that but can't - ubuntu isn't getting far enough through install to fiddle with drivers and the likes, and works on the live distro fine so I can't see it being that anyway. When I restart the machine again I get the launch menu, so take the option to load with rescue mode. Again, I get so far through the boot sequence to be faced with a 'Kernel panic - not syncing: No init found' error. But unlike most of the forum posts I have found there are no suggestions for the init switch, just "init= ". I have attached an image below showing more of the error. I can still get into the file system using the live distro, but being a newbie with some basic linux server knowledge from my web development background I have kind of hit a wall with getting this up and running.

[IMG]https://lh5.googleusercontent.com/-TQ4DrVkOp1Q/UahYgRWm8xI/AAAAAAAAAKs/dvk8v2QK-iw/w672-h502-no/photo.JPG[/IMG]

Can someone help me sort this out?

All advice listened to carefully and tried with enthusiasm ;-)

Cheers,

Gordon

---

### Post by ohnonot on 2013-06-01
- make sure the .iso is not corrupted (check checksums), neither is the usb stick or whatever you're using.
you didn't by anychance make your install media with unetbootin? i'm sometimes having problems with that, though it's a great tool.
- /init - should be somewhere on the install media.
it says there on your screen where to look for the answer Linux Documentation/init.txt - either on the install medium or by making a websearch.

- i get the impression your laptop is a bit dated; maybe the fullblown unstable ubuntu 13.04 is not quite the right thing? try 12.04 LTS (long term support) or maybe xubuntu 12.04 lts.

---

