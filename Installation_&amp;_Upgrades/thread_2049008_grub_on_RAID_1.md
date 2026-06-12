---
title: "grub on RAID 1"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by albert s on 2012-08-27
where do I install grub to on a Raid 1 ?
I keep going into a boot loop, and Ive tried putting grub everywhere I can think of,
please help.

---

### Post by darkod on 2012-08-27
It depends of the raid type.
If it's fakeraid (bios raid), then you need to install grub2 onto the MBR of the array, which will be something like /dev/mapper/blahblah, and without any number at the end.

If it's software raid, grub2 is installed on the MBR of both disks, like /dev/sda and /dev/sdb for example.

---

### Post by albert s on 2012-08-27
its bios RAID, 
so I drop the bit at the end which is like  ' _9200p2p1 '
is that right ?
I just use the  '  /dev/isw_[COLOR=Red]bdhgdnendshgdjdndhg[/COLOR] '  bit
[COLOR=Red]
the red is random[/COLOR]
but the rest is where Im actually putting down, i cant remember the actual red bit.

---

### Post by darkod on 2012-08-28
No, you need to drop only the partition label, which might be only the 'p1' or 'p2p1'. Not sure because it depends on the raid.

Usualy it would end only in '1' or 'p1' but I have no idea, it seems every board is doing it differently.

But the '9200' might be part of the raid device name, so dropping it might make the command not work.

If you can, boot with the live cd in live mode, and look in Gparted. Often it can recognize a fakeraid and show the device name. Write it down and use that name. In the Gparted drop down box to select a disk, it will show only the device name, like it shows /dev/sda. So, what ever is in there, should be the full name of the array, without any partition labels.

---

### Post by albert s on 2012-09-04
star man Darkrod
it needed the [COLOR=Red]_9200[/COLOR] bit at the end . 
thank you, sorry I didnt reply sooner, Ive been away for a couple of days and just got back and got it loaded up tonight.

---

