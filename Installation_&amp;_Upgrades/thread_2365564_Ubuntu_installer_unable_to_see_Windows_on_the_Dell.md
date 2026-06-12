---
title: "Ubuntu installer unable to see Windows on the Dell XPS 15 9560"
date: 2017-07-07
forum: Installation &amp; Upgrades
---

### Post by The musmula on 2017-07-07
Hello all,

I'll just cut to the chase: I want to install Ubuntu (Ubuntu GNOME ideally) on my new xps 15 (the 4K touchscreen version with 16gb of RAM and the 512GB SSD if that's relevant. No fingerprint reader). I tried following [this]("https://github.com/rcasero/doc/wiki/Ubuntu-linux-on-Dell-XPS-15-(9560)") guide but I get stuck at the point when I should select the "install Ubuntu alongside windows" option. I want to keep Windows and ideally I wouldn't want to mess with the partitions myself since I never did that sorta thing for a UEFI system. Basically I just get the "wipe and install Ubuntu" option. Tbh, the partitions on this thing are a bit wee but GParted seems to find its way around all of this and I can edit them around but I'd like the installer to just figure out how to best set up dual boot. So far I've tried the Ubuntu GNOME 16.04 installer after which I figured the Ubuntu 16.04 installer might do it. Nope. But it occurred to me that if I bump it up to 17.04, the problem would be gone. Nah, if anything the installer is worse on Ubuntu GNOME 17.04 because it can't handle DPI scaling at all, which is just weird.

Here's a look at my partition setup: [http://imgur.com/a/0smgC](http://imgur.com/a/0smgC)

Thank's for your time, you beautiful crowd of terminal ninjas

---

### Post by Frogs Hair on 2017-07-07
I dual boot and use the Windows disk manager to create unallocated space for Ubuntu to install along side of Windows. This is done by shrinking the Windows partition from the Windows side.The photo _seems_ to indicate you have less than. 1.00 MB of unallocated space and the along side installation option should automatically detect the unallocated volume. I'm not familiar with the partition software you are using, so you might want to post an image of Windows disk management.

---

### Post by yancek on 2017-07-07
Obviously, from the image you posted as pointed out above, you only have 1MB free on which to install Ubuntu so that will never work.  Followng the advice above by shrinking the windows partition from Disk Management to get unallocated space would be a good first step.  You should run chkdsk from windows after making a change in partitions.

 

> Basically I just get the "wipe and install Ubuntu" option. 

That's the only logical option with your drive/partition setup.  I would suggest that in addition to modifying your windows partitions, you read through the Ubuntu documentation at their site below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by The musmula on 2017-07-08
Hahahahaha, Jesus, was I this stupid? I thought I could resize those during the installation since I was able to do that once when setting up a dual boot for Elementary and Ubuntu GNOME. Thanks, I'll try that and report back

That did it, thanks

---

