---
title: "Elantech trackpad does not work.  Worked initially at boot up a few times."
date: 2016-11-19
forum: Installation &amp; Upgrades
---

### Post by geronimo48 on 2016-11-19
Hello,

I am a neophyte with Ubuntu.  I just installed Ubuntu last night (for the first time ever) on my laptop and the trackpad will not work.  I have an Acer laptop with Elantech trackpad.  

The Elantech trackpad shows up when I check with the commands that I found online.  However, it allows me to click, but it does not allow me to scroll the pointer.  I am at wits end and getting ready to turn back to the dark side.  

I tried editing the Grub command line in several different ways.  I have tried to download the original drivers found on the laptop manufacturer's site, but for some reason I cannot open the file.

I switched from Windows 10, which has proven to be a disaster for me.

Your help is  greatly appreciated. :D

---

### Post by Andrew F in Australia on 2016-11-20
Hi Geronimo.

I have a new (10 day old) laptop here with similar issues.  In my case, the Elan touchpad was not recognised for the first 5 boots, worked for a couple, then didn't for one and now (touch wood) appears to be working properly. 2 fingers on the trackpad allow you to scroll, full cursor and button control with 1 finger.

Intel i7-6400HQ chip

I did edit the /etc/grub file as you allude to as per: [http://askubuntu.com/questions/763584/elantech-touchpad-not-working-on-ubuntu-16-04-and-arch-linux](http://askubuntu.com/questions/763584/elantech-touchpad-not-working-on-ubuntu-16-04-and-arch-linux)
I also ran the following from the bug report below: sudo dkms ldtarball psmouse-elantech-x551c.tar.gz 

This seems to be your bug (I found this last week when I was looking for fixes.): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442/+index?comments=all)

There were a few fixes in there as well to try. Apparently there is a tick-box in the mouse settings to enable 2 finger scrolling that I wasn't aware of either.  Just in case it's something so simple.

It looks as though the trackpad is still a bit buggy in linux.

Good luck,

A

---

