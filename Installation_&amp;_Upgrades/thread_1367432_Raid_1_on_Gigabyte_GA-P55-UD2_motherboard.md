---
title: "Raid 1 on Gigabyte GA-P55-UD2 motherboard"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by setchp on 2009-12-29
Trying to set up Ubuntu server 9.10.

New machine Gigabyte GA-P55M-UD2 motherboard. 3 x 500GB HD.
/dev/sda used by installation - all fine.
Used bios to set up Raid 1 (Mirror) on next 2 disks.
I can fdisk /dev/sdc (which I assume is the raid pair).
But when I try to mkfs.ext4 on /dev/sdc1 error is cannot stat device, device does not exist.

Any help greatly appreciated.

SteveP :confused:

---

### Post by phillw on 2009-12-29
Hi, and welcome to the forums.

There have been & continue to be, issues with 9.10 & Grub2 and RAID. There are ways round it, but, as you are doing a clean install, I'd quietly point you in the direction of 9.04 -- It'll just save you a lot of hair-pulling. Don't worry, 9.04 is fully supported for a about 18 months yet - by which time, things should have quietened down.

[https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)  is a good place to head.

Regards,

Phill.

---

### Post by Pablo Alonso on 2010-02-24
Hi setchp!
Have you found any solution for that? Or maybe a better idea?
I have the same mother right now and I want to use two raid 1 or maybe a raid 10 in this mother.

Also someone knows if this mother has a real hardware raid controller built in or it is another of the so called fakeRAID controller.

Thanks in advance to all people that make this community great!

Regards,
Pablo Alonso

---

