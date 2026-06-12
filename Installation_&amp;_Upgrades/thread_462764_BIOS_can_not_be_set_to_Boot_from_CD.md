---
title: "BIOS can not be set to Boot from CD"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by BPak on 2007-06-03
My Bios does not allow to set the CD Boot as its preference.

I understand thaty you need to have the Ubuntu running to make a Bootable Floopy?

Is there another way to Start the LiveCD and run Ubunto so that I can make a Bootable Floopy?

---

### Post by confused57 on 2007-06-03
I don't know if it could be done with the live cd(maybe a Puppy Linux or DSl, depending on how much ram), but here's a method I found for making a SBM floppy in Linux:
[http://wiki.linuxquestions.org/wiki/Boot_floppy#Creating_a_Smart_Boot_Manager_boot_floppy](http://wiki.linuxquestions.org/wiki/Boot_floppy#Creating_a_Smart_Boot_Manager_boot_floppy)

Here's the download mirror for the sbminst-static file:
[http://btmgr.sourceforge.net/3.7/](http://btmgr.sourceforge.net/3.7/)

I won't be able to anytime soon, but I may give it a try in the near future...you might want to try it yourself & let me know if you got it working.

---

### Post by BPak on 2007-06-03
confused57 - Thanks for the reply.

I tried the CD on another computer that could CD Boot and it would not work. Reason was the CD Drive was not good.

So went back to BIOS and did some more scratching around and by accident found there are TWO different settings for the Order of Boot.

I use the Bios to set which of the two hard drives on the computer are to be the one to boot with nearly every day and am used to just doing that.

A SideScreen note in the BIOS Screen said the Order could be changed with the + and -  keys. So trying this Outside of the normal settings allowed me to move the Cd Rom above the Hard Drive for boot order.

The result is I now have the Live CD working and booting from the CD Drive.

I looked through the links you directed me to and it appears that those settings are created from a linux OS. It would be good if there was a STANDARD FILE that could be downloaded and put on the Floppy isc to start a boot up of Linux on the CD Rom.

Thanks again!

---

