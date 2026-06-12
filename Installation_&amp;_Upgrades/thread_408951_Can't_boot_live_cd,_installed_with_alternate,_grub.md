---
title: "Can't boot live cd, installed with alternate, grub problems."
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by DemaSRV on 2007-04-14
On every ubuntu version I have tried I have received the same problem.

I could not boot into the live cd at all, it would freeze up just after the tan screen came up and I could move my mouse around for a little bit.  With 6.06 and 7.04 I was getting an error that told me to boot with noapic, i tried it with no luck (some kind of IO-APIC not syncing)  So eventually I tried the alternate version, and installed it to my joy.  After the reboot I'm getting a grub error 17.  I have the super grub disk recovery disk, since even damn small linux wouldnt work. I'm almost ready to give up but I want to give it one more try.

I think my raid 0 might have something to do with the problem, but that is my windows install so I dont know why it should be affecting everything since I'm installing linux on a seperate 9 gig drive i have.

Asus Crosshair
AMD X2 4200+
nVidia 7950 GT
2x Seagate barricuda 160gb drives
western digital 9 gig drive
2 gig DDR2 pc6400 ram

I really need to be steered in the right direction, I've been reading and reading and just can't seem to come across a fix.  Thanks for your help.

---

### Post by DemaSRV on 2007-04-14
Still haven't resolved the problem, trying to bump.

I ended up ficing the mbr with windows,so I have a linux install I cannot get to, but more than anything i want to be able to use the livecd.  It just locks up when the tan screen comes up and after about a minute of me being able to move the mouse around, it just locks up.

---

### Post by randell6564 on 2007-04-14
> I think my raid 0 might have something to do with the problem, but that is my windows install so I dont know why it should be affecting everything since I'm installing linux on a seperate 9 gig drive i have.
Yes, BUT.., Grub is trying to find it's home on "raid 0" in order to achieve a dual-boot!

It HAS to be there so that you can boot Windows OR Linux.  Google raid/Linux, and you will come to see that raid devices and Grub are not very agreeable.

---

### Post by DemaSRV on 2007-04-15
Ok, well I can fix that later, right now I really just want to be able to at least boot a live cd.  Right now it is just locking up, and I'm getting the MS-BIOS APIC not syncing error.  I haven't found a solution for it yet, and booting with noapic doesn't work.

Thanks!

---

### Post by DemaSRV on 2007-04-15
This thread :[http://ubuntuforums.org/showthread.php?t=409855](http://ubuntuforums.org/showthread.php?t=409855) 
helped me get the livecd actually working.  Now I just have to find a way for my RAID 0 to work with Grub...

---

