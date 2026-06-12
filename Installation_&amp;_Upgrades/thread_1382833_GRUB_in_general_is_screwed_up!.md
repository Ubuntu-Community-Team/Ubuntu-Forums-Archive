---
title: "GRUB in general is screwed up!"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by PGleo86 on 2010-01-16
Hi, I have a Gateway laptop that I recently purchased new with Windows 7 64 bit preinstalled. I immediately upon receiving it installed Ubuntu 9.10 after shrinking the partition of Windows from 220 GB to 110 GB. I installed Ubuntu in the free space freed up by this, but after I used Windows 7 a bit, that partition got very full, so I deleted the Ubuntu partition, formatted it, and merged it with the Windows partition. Upon doing this, i figured that it might be good to restart, so I did, and upon restarting, I was greeted by the GRUB rescue prompt. I saw this, and immediately knew that I deleted all but this small fragment of GRUB with the Ubuntu partition, but I couldn't boot from HDD. I ended up reinstalling Ubuntu from LiveCD, to a 20 GB partition, leaving 200 GB for Windows. This reinstalled GRUB, again to the Ubuntu partition, and I figured it would be fine, so I left the computer updating Windows 7 during dinner. When I came back, I found that the computer was restarting. I thought, "Oh, good, it just finished updating". Then, to my horror, it shut down, rebooted again, got to the "GRUB loading" screen, and shut down and rebooted in an infinite loop. I now can't get past this from the HDD, only by booting from a CD. I have no Windows 7 recovery discs, just a 12 GB partition on the HDD labeled by GRUB as "Windows Vista (loader)". My other partitions are a 100 MB partition that I assume Windows 7 put there, labeled "Windows 7 (loader)", and my main Windows 7 partition (200 GB), and my 20 GB Ubuntu partition where the defective GRUB is (presumably) installed. I have the Super GRUB Disc, and a Karmic LiveCD. Any help would be much appreciated, and even if I can just boot Windows 7, get my personal files, and then restore to factory settings (will that erase GRUB?) and restore Windows from there, it would be immensely helpful. Thanks!  Specs: 2.1 GHz AMD Athlon 64 X2, 3 GB DDR2/800, 250 GB HDD, onboard Radeon 3200 graphics

---

### Post by Leppie on 2010-01-16
booting off the livecd, open a terminal and issue these commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
ignore the warning/message you receive.
this process will restore the mbr to factory settings, hence boot straight into windows.

---

### Post by kansasnoob on 2010-01-16
If Leppie's suggestion doesn't work we'll need to see the output of the Boot Info Script run from the Live CD as explained here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by PGleo86 on 2010-01-16
Actually, I'm typing this from my Win7, which booted straightaway . Thanks for the help!

---

### Post by Leppie on 2010-01-16
glad it's working as you wanted it :)

---

### Post by PGleo86 on 2010-01-16
> **Leppie said:**
> glad it's working as you wanted it :)
Thanks for the help!I would never have figured that out on my own!

---

### Post by Leppie on 2010-01-16
> **PGleo86 said:**
> Thanks for the help!I would never have figured that out on my own!
well, most things are easy once you know how to do them ;)

---

### Post by PGleo86 on 2010-01-16
> **Leppie said:**
> well, most things are easy once you know how to do them ;)
Well, I'm still just a lowly noob. I'd heard of lilo but never really saw possibilities involving it. I really owe you one, though. Most of my school work is on this thing

---

### Post by Leppie on 2010-01-16
> **PGleo86 said:**
> Well, I'm still just a lowly noob. I'd heard of lilo but never really saw possibilities involving it. I really owe you one, though. Most of my school work is on this thing
we all have to start somewhere.
there's actually many tools that could restore the mbr, ultimate boot cd, windows recovery cd, windows installation cd, etc.
search engines are our friends ;)

---

### Post by PGleo86 on 2010-01-16
> **Leppie said:**
> we all have to start somewhere.
there's actually many tools that could restore the mbr, ultimate boot cd, windows recovery cd, windows installation cd, etc.
search engines are our friends ;)
This was probably the easiest way though...

---

