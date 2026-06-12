---
title: "Ubuntu Install Woes"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by DaveJHQ on 2007-04-03
Hi Guys, 
I'm currently trying to install Ubuntu onto my desktop, and its starting to give me problems. The system im runing is:
    Asus A8N-SLI Deluxe m/b
    AMD A64 X2-3800
    1 x 250GB IDE HDD (Just random data)
    1 x 320GB SATA HDD (more data :) )
    1 x 200GB SATA HDD (partioned into: (winblows C)(data D)(2gb for swap file)(20GB for linux)
    2 x 1GB Corsair Ram
    1 x GeForce FX 7600GT
Its a neat system, but i really dont want to eventually go from XP to Vista, I'd much rather go to Linux.

I have downloaded the AMD64 iso, and the live disk works perfectly (running off it atm). I go through the 'Setting up with Linux' as in the April ed of PC User, and everything goes ok. I go to restart, it ejects my cd, I put the tray in and press enter, and nothing happens. I press the restart button and when my computer boots it goes to Win XP Pro, it totally skips Ubuntu. Why?

Thanks in advance guys ;)
Dave

---

### Post by bulldog on 2007-04-03
Very common issue.
When you install ubuntu you get GRUB as a bootloader.
Nothing wrong with that one,BUT it will be installed on hd0,in other words your primary master IDE hdd.
You have your windows hdd set in the BIOS as master boot device,but linux thinks different.
Your IDE hdd is hd0
Your Sata hdd's are hd1 and hd2.

So to see grub,boot from the IDE hdd.
There's a fair chance you get problems to boot into ubuntu or windows,but that can easily be fixed.
Try first and post what happens,if you can boot ubuntu without errors,you can't boot into windows,you have to make some modification to the menu.lst.

Let us know what happens,we can tell you what you have to do to make GRUB boot windows and ubuntu as well.
You have to set the IDE hdd as the master boot device in your BIOS.

---

### Post by mikewhatever on 2007-04-03
At the end of the installation you should have been asked to install GRUB boot loader. Do you remember where did it go to? I suspect that Ubuntu installation is fine, but GRUB is installed on the HDD that is not set to boot first. Super GRUB disk should be able to boot you into Ubuntu [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Once in Ubuntu, open the terminal (Application>Accessories>Terminal) type in the following and post the output
> sudo grub
find /boot/grub/stage1
sudo fdisk -lu
sudo gedit /boot/grub/device.map

---

### Post by DaveJHQ on 2007-04-04
Hey guys, thanks for the help! I have removed the offending IDE drive, and put it into an external case, ran the install and now its all good:) 
Just gotta install some drives which I'm about to do and Im laughing!
Dave

---

