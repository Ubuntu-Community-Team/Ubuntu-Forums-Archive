---
title: "Grub is now missing"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by Canime on 2011-03-02
I have installed windows 7 back to its former state in after foolishly messing around with some installation options in an Ubuntu install (this caused windows to disappear, and me to repair it). In *repairing* windows, I overwrote my grub file and the boot options for Ubuntu, so that it looks something like this:

Disk 1: Primary Partition - Windows 7 
Disk 1: Secondary Partition - Windows 7
Disk 1: Secondary Partition - Free Space ( this is where I have Ubuntu installed)

How can I repair my grub file so that I can boot into my Ubuntu installation?

---

### Post by wilee-nilee on 2011-03-02
> **Canime said:**
> I have installed windows 7 back to its former state in after foolishly messing around with some installation options in an Ubuntu install (this caused windows to disappear, and me to repair it). In *repairing* windows, I overwrote my grub file and the boot options for Ubuntu, so that it looks something like this:

Disk 1: Primary Partition - Windows 7 
Disk 1: Secondary Partition - Windows 7
Disk 1: Secondary Partition - Free Space ( this is where I have Ubuntu installed)

How can I repair my grub file so that I can boot into my Ubuntu installation?

Boot the Ubuntu live cd of the installed distro and run these two commands and post the results
fdisk -lu
grub-install -v

---

### Post by Canime on 2011-03-02
I've tried that route, and have tried to install grub-install, and followed the traditional instructions in an attempt to get it to load. Later on, it worked with some errors, so I used the --force option. I rebooted, it showed windows 7 and Linux options, but for some reason by selecting Linux, windows boots. When I select windows 7 windows 7 boots. 

I've pretty much come full circle now, by reloading Linux with all the options at default, and windows 7 wont boot. This is giving me the craps.

Anyhow, when I ran sudo fdisk -l I basically get 

sda1 * NTFS - windows drive C:
sda6 Linux partition
sda5 NTFS - windows drive E:

but that doesnt matter now because of course I re-installed linux and lost windows, so I'm going to spend the rest of the evening trying to get it round the right way...

---

### Post by Canime on 2011-03-02
Further more, I have a linux installation working now on some free space on my drive. The partition I originally created could cope with both Windows and Linux, it just needed some fine adjustments to the installation process. 

I can make some recommendations now that I have all this working and they are.
[LIST]
[*]In ubunut 10.10, the install screen offers to install amongst other operating systems, and if you select be carefull of the next two or three points
[*]Make sure that the slide bar gives the option of resizing to the partition you want, and not to some space it thinks is free for destruction
[*]Apply care in the advanced options, it can be a delicate situation to format a partition if you and THEN select a boot loader that isn't the right one.
[*]Make sure that your boot loader is the correct one in the drop down list, it is immensly time consuming if you happen to change this around.
[/LIST] 
And, be careful at the beginning of any installation process because you will find eventually if you didn't get it EXACTLY right in the beginning that you will have to change it somewhere down the track, this could be because

[LIST]
[*]You get extremely bored of windows and want to change to linux, and therefore you want a linux installation on your primary partition rather than some free space somewhere else in the sector.
[*]You already installed linux like I did on your primary partition, you then erased it and put on windows and you no longer have the linux installation you originally wanted.
[*]You now have paritions floating around that are unworkable from whichever angle you look at them from.
[*]You have enough data on your partition and no good reason to switch your partitions around, your installations around either for the hundredth time, or even the effort after two days messing with them to come up with a hairbrained solution to the whole process.
[/LIST]
I even after all this messing about considered buying a new computer to cope with the space restrictions now offered by the greedy windows 7 installation, and under-rated new linux distribution which installed correctly after the fifth time. Lucky I backed it up before I started, or else I would be whistling a different tune.

---

### Post by wilee-nilee on 2011-03-02
Ah the words of learning, discrediting the OS for operator error.:)

Glad you got a set up that works, but with a few questions you could have had easier travel possibly.

Partitioning is easy, loading the mbr is easy, and loading operating systems is really easy with Windows and Ubuntu.

---

### Post by Canime on 2011-03-02
No discrediting anywhere, I expected a bit of trouble, and I like the fact that Linux is free! Trying to fix the mbr with Linux was probably where I started having troubles. Namely because of Grub legacy as opposed to using grub2. I'll add that there is almost no way of attempting a save of a Linux installation if you receive a grub prompt instead of the flash screen, and that happened in about the second installation attempt. 

But YES! it works... Now!

---

