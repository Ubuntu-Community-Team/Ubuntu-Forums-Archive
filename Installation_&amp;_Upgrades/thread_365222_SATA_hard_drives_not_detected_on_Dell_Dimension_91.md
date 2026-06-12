---
title: "SATA hard drives not detected on Dell Dimension 9150. Raid array problem?"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by David Marrs on 2007-02-19
Hi guys,

I'm trying to install 6.10 on a dell 9150 but when I come to partition the hard drive, none is detected. Actually, more accurately, 2 discs are detected, but both are described as empty and containing no partitions. This is clearly wrong as at least one disc contains windows and data.

Windows Explorer shows 2 drives, C:\ and U:\. C:\ contains all data and U:\ appears at first to be empty, but actually used space shows that it contains exactly the same amount of data as C:\ does (~50GB). After looking in the device manager, it looks like I've got a raid system set up here.

Device manager shows:
[LIST]
[*]SCSI and RAID controllers - Intel(R) 80821GR/GH SATA RAID Controller
[*]IDE ATA/ATAPI controllers - Intel(R)  82801G (ICH7 Family) Ultra ATA Storage Controllers - 27DF
[*]Disk Drives - ARRAY
[/LIST]
I presume here that "ARRAY" refers to a raid array. I have no idea why my computer would need such a thing, but there you are.

After googling I found [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) . It looks like I've got some homework of my own to do but some pointers would be appreciated. Specifically, how can I find out more about my raid setup and precisely how it operates? I'm a bit of a raid newb here.

And does anyone have any general advice on what it's like to install to a raid system? Is Ubuntu the best system for this job or are other distros ahead? I don't need a pointnclick interface, but I do need to be able to have Linux installed and running within a weekend because this is a work/production machine and time = money. I would happily disable all this raid stuff and just use one disc for windows and the other for Linux if it means dual booting is possible. We're reaching a point at work where moving to Linux for web development is becoming important, but we still need access to Windows for other (mostly design related) areas.

Thanks for any advice.

---

