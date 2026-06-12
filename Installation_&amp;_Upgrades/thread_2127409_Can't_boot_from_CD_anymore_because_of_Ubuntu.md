---
title: "Can't boot from CD anymore because of Ubuntu"
date: 2013-03-19
forum: Installation &amp; Upgrades
---

### Post by Carligan on 2013-03-19
After having some problems with Windows 8 not working anymore etc (worst OS ever) I decided to go for some nostalgia and use Ubuntu for some days, and even see how it was after Unity was introduced as an old KDE user. 

I installed the newest Ubuntu and well, to say the least I had a lot of problems, such as automatically logging out when I opened a video on the computer, flash player constantly crashing etc. So I wanted to go back to Windows 7 and I burned an ISO ready to put it in.

I was astounded to realize that the PC just wouldn't load the disc for some reason. It did so when I installed some other Linux distro earlier. And I think the problem is that Ubuntu just loads too darn fast. I have the best processor and SSD on the market, so it just pretty much instantly boots. There is literallty NO time for my PC to regocnize the disc before Ubuntu loads. 

What should I do? I just want to install my darn Windows 7. Is there a way to remove Ubuntu from within with some sort of command/script, or perhaps have it boot way slower or something or is there another way?

And please don't tell me to disconnect my SDD when booting the Windows 7 CD or something like that because I simply can't. The geniuses that put together my PC must have glued the SDD or something like that to my cabinet because I simply can't move it at all, which means I can't get to its power suppply :mad:
It's not the CD either as this is happening with every CD that I have, including different Linux OS CDs. 


Your truly, mr. Soonoutofpatience.

---

### Post by dino99 on 2013-03-20
if you get problems with ALL your cd/dvd, then you might understand the burning issue: use a good burning app, like k3b, and select ALWAYS the slowest speed. Or better use usb stick with unetbootin.

standard installation: [http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)
boot settings: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by tanstaaflwdm on 2013-03-21
Check your bios to see what your boot device order is. I've discovered that either ubuntu or grub like to make the boot partition of your hd the first thing in the list which means it never gets to the CD/DVD drive.

Go into bios setup and make sure that the CD/DVD drive is the first thing in the list.

---

### Post by kurt18947 on 2013-03-21
> **tanstaaflwdm said:**
> Check your bios to see what your boot device order is. I've discovered that either ubuntu or grub like to make the boot partition of your hd the first thing in the list which means it never gets to the CD/DVD drive.

Go into bios setup and make sure that the CD/DVD drive is the first thing in the list.

That's what I was thinking as well, boot order in the BIOS.  Some machines (notebooks mostly) have a second f key to change boot order.  For instance,  pressing <f2>  immediately after pressing the power button might take you into the BIOS setup, while pressing <f12>  might permit you to boot from a device different from the default on a one-time basis. For example normal boot order is 1) internal hard drive 2) CD/DVD drive 3) USB drive.  You should be able to change these defaults in the BIOS setup screen or for example, boot from a USB drive one time by pressing <f12> on startup.  Your machine or motherboard documentation should address this.  If you don't have/can't find your printed material, googling  the model should turn up what you need.  Good luck.

---

### Post by oldos2er on 2013-03-21
> **Carligan said:**
> I installed the newest Ubuntu and well, to say the least I had a lot of problems, such as automatically logging out when I opened a video on the computer, flash player constantly crashing etc. So I wanted to go back to Windows 7 and I burned an ISO ready to put it in.


This sounds like a video driver problem. What are your hardware specs?

---

