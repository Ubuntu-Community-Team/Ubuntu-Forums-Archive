---
title: "Ubuntu 8.1 /  Vista Dual Boot - need some help with grub menu"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by TomX19 on 2008-11-09
Hi,

I am a complete Ubuntu novice, so if at any point I sound like I know what I'm talking about it's pure luck!

A couple of days ago I decided I wanted to keep Vista for a couple of things, even though it crashes infuriatingly frequently!  So, following some instructions I found at this link -

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

- I managed to partition the drive and re-install Vista in the partition I made.  I then set about trying to set up the grub menu in order to select the OS to use.  My plan is to keep Vista for iTunes and pretty much use Ubuntu 8.1 for all web browsing - including something that I can log into MSN Messenger with at some point.  I don't play any games or do much else really.

So, now Vista just boots itself and one wouldn't know that Ubuntu is installed, so I booted Ubuntu from the Live CD and tried the following:

sudo grub <enter>

This worked

Then what I should be doing - according to the instructions) is the following:

root (0,0)

setup (hd0)

quit

exit

The system does not seem to recognise the command "root (0,0)", I guess in ubuntu this is not right, as the instructions at the link are general Linux.

What I should do then is reboot into the Ubuntu installation (Vista now should not be an option) and add the following to /boot/grub/menu.lst - but I can't currently boot into ubuntu except from the Live CD

title Windows Vista
root (hd0,1)
makeactive
chainloader +1


Is it obvious to anyone where I'm going wrong?

Thanks

---

### Post by caljohnsmith on 2008-11-09
Try this from the Live CD:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should restore Grub to your MBR so you will get the Grub menu on start up. If that works and you can boot Ubuntu, then please post:
```
sudo fdisk -l
```
And I can help you booting Vista from Grub if you need it. :)

---

### Post by TomX19 on 2008-11-09
Thanks.  :)

I'm at work now so I'll have another go tomorrow.

My intention is to have a small menu at startup where I can choose Vista or Ubuntu.

---

### Post by TomX19 on 2008-11-10
Thanks very much for your help.  I've got it working just how I wanted it.  


I also did a bit of googling regarding setting up the menu how I wanted it and I've now got a grub menu which comes up (without needing to hit ESC) and offers a small options list to boot into either Ubuntu or Vista with a fifteen second timeout....

:)

---

### Post by caljohnsmith on 2008-11-10
That's great news, I'm glad you have it all sorted out. Cheers and have fun with Ubuntu. :)

---

