---
title: "Stuck in GRUB Rescue"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by aeroprof on 2012-10-18
I have a problem that I have not been able to find an answer for after searching.

I have a PC where I can swap out the system disks (I use those slide in/out SATA trays).  On one disk I installed Win7 - everything ran fine.  I removed the first disk and inserted a second disk and installed Ubuntu - that ran fine.

Now here is where the problem starts:

I removed the second disk (Ubuntu) and insert the first disk (Win7), when I try to boot up I get the following error message:

"no such device grub rescue"

If I re-insert the second disk (Ubuntu) it will boot into Ubuntu just fine.  So, some how, my computer will no longer recognize the first disk (Win7) and all I did was install Ubuntu and a completely separate second disk.  (Remember, since I am using those slide in/out trays the two disks are *never* installed in the computer at the same time.)

I don't know enough about MBRs and such....but how did installing Ubuntu on Disk #2 cause the Win7 operating system on Disk #1 to no longer load?  I can only conclude it has something to do with the BIOS...but how do I fix it???

Thanks to all in advance for any help you can provide.

---

### Post by grahammechanical on 2012-10-18
Is there a third disk sitting inside the machine? If so then the Ubuntu install put the Grub bootloader into the MBR of that internal hard disk.

Regards.

---

### Post by aeroprof on 2012-10-18
Thank you for your reply.

Yes, there is a third disk that is always in the computer - it is simply a data disk and I never installed anything on it.  If the MBR is on that third data disk (and that really confuses me!) preventing me from loading Win7, how do I fix things?

Just to be clear:  Disks #1 and #2 are "internal" disks not externally connected through a USB port or sometime like that.  I have a rack mounted in my computer case that is connected directly to the motherboard via SATA and I can slide dives in and out of the rack.  So when a drive is inserted it should be viewed be the system as an internal drive drive, shouldn't it?

---

### Post by Bashing-om on 2012-10-18
aeroprof; Hi !

these terminal commands will tell you where grub is installed - removes any doubts.
```

sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub

```[INDENT]just try'n to help

[/INDENT]

---

