---
title: "Deleted part of partition, Can't boot"
date: 2015-06-01
forum: Installation &amp; Upgrades
---

### Post by Frank_Snyder on 2015-06-01
So I was trying to format part of a SD card and like a dummy deleted two sections of partitioned data from my HDD in the process. I figured that for sure I had broke something so luckily I backed up everything before restarting. Sure enough after restarting I was greeted with this screen...

[http://i.imgur.com/SH4R33P.jpg](http://i.imgur.com/SH4R33P.jpg)

The laptop is a toshiba satellite e55-a5114 and came with windows 8.1 preinstalled. I installed ubuntu 14.04 onto it and allocated it 10GB of space and ended up pretty much never using the windows partition.

I have since created a bootable 15.04 usb and reinstalled the OS over the whole HDD twice now. The second time I designated that it write zeros over the empty spaces, effectively wiping the whole drive. Yet I continue to get the exact same "Reboot or select proper boot device" at startup. The first time I installed it a message popped up about the install being UEFI and that it might give me issues booting because of that for some reason. Is that a possibility?

---

### Post by grahammechanical on 2015-06-01
The motherboard will give us that message if it cannot find an operating system to load. Is the motherboard still expecting to find an OS on a USB port? Is the motherboard set to look for an OS on the hard disk?

Regards.

---

### Post by RobGoss on 2015-06-01
Hello and welcome to the forum, I'm not sure what you're referring to as [COLOR=#000000] SD card? is this a SD card you have inserted in to your computer?

And what are you hoping to accomplish here? are you wanting to just install Ubuntu on your computer but you're getting this message each time you boot.

I'm not sure what you deleted from your partitions but If I'm correct and you just want to install Ubuntu on this machine you will need to format your machine in order to clean things up and maybe do a fresh install of Ubuntu. This is my suggestion if you only want Ubuntu installed on this computer. [/COLOR]

---

### Post by Frank_Snyder on 2015-06-02
I'm sorry for not being clear. The SD card had nothing to do with the issue I was having other than the fact that I mistook it for my HDD. The SD card was actually being setup for Raspbian for my Pi. I was having issues with Raspbian so I went to start deleting the multiple partitions setup on the SD card but instead of having my SD card selected, I had my HDD selected when I started deleting those partitions (from the disk manager within Ubuntu).

After this, there was nothing left to do after a reboot. The laptop wouldn't boot without the error from above. The bootable USB of Ubuntu obviously worked fine.

As I said, I reinstalled Ubuntu 15.04 and in the process selected the option to erase everything from the HDD. After the first install and no luck, I explicitly checked "Write zeros over empty space" as well when reinstalling and telling it to erase everything off the HDD.

I suspect it's something that needs to be changed in the BIOS under boot properties but at the same time that confuses me as nothing was changed before the deletion and it booted perfectly fine.

---

