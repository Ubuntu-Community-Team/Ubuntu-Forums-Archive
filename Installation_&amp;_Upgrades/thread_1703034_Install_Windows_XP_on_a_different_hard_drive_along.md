---
title: "Install Windows XP on a different hard drive alongside Ubuntu"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by Maximus559 on 2011-03-08
I'm sure this has been discussed before, but I can't seem to find any definitive instructions. What I'd like to do is pop a new hard drive in one of my Ubuntu PCs and install Windows XP on the new hard drive. (Don't worry, I'm not going back to XP... I just wouldn't mind playing some old games again.)

This machine originally had one hard drive with Windows 98 SE installed. When I starting using Ubuntu, I just added another hard drive and installed to that. Now I boot from the Ubuntu drive and have Windows 98 as an option in the Grub menu.

If I add another hard drive and install Windows XP, how can I update the Grub menu? I realize that it's possible to manually edit the menu.lst file for Grub, but I didn't have to do that in order for Grub to recognize my Windows 98 drive. Would running update-grub as root do the trick?

---

### Post by oldfred on 2011-03-08
A sudo update-grub should find your windows install. For many it just works, but.

But which drive is sda? Which drive are you installing windows to. Many with mixed IDE/SATA have issues with which drive is hd0 which windows seems to prefer and which is hd1.

If they are all SATA drives and you make windows hd0/sda it seems to work the best. The others seem to depend on how good the BIOS is in reporting to grub2 and how good grub2 is in using that info.

Good luck.

---

### Post by Maximus559 on 2011-03-08
Thanks for the reply. Actually, all of the drives are IDE (yes, it is an old P4 system). If I remember correctly, I've already filled up one IDE cable, so the new drive would be the master on its own cable.

---

### Post by oldfred on 2011-03-09
With older IDE systems, the only bootable drive was the primary master.

Often then windows would be the primary master, and Ubuntu on any other drive but grub's boot loader was installed to the primary master to let you boot any system. Windows then would still see itself as hd0 and Ubuntu using UUIDs or hd1 does not care. Windows does boot from hd1 but for whatever reason it seems to often have more issues in setting it up correctly to dual boot.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by Maximus559 on 2011-03-16
Got it working today. Turns out I was wrong about how the system was set up initially. I actually had the Ubuntu drive as the primary slave and the Windows 98 drive as the primary master. I also did not have any IDE slots left open... not sure why I thought I did.

I ended up just replacing the Windows 98 drive with a new hard drive and installing XP to that. Grub couldn't handle the new arrangement, though, so I had to reinstall it from the live CD as described [here ]("https://help.ubuntu.com/community/Grub2")and then boot into Ubuntu and run sudo update-grub. Now I boot from the Ubuntu drive which is the primary slave, so apparently this is possible.

On a related note, I'd forgotten what a pain XP is to set up. Makes me appreciate Ubuntu even more.

---

### Post by kagerato on 2011-03-16
> **Maximus559 said:**
>  Grub couldn't handle the new arrangement ...

It's not that Grub can't handle it, as you found after reinstalling it from the Live CD.  It's that the Windows installer (all of them, including 7) unilaterally and without any warning or explicit permission clobbers the master boot record, overwriting it with its own data.

---

### Post by Maximus559 on 2011-03-17
Not sure how that would be possible in this case, as the drive containing Ubuntu and Grub was not even connected to the system when I installed XP. I did it this way on purpose to ensure that the XP installer couldn't tamper with anything. My guess is that Grub freaked out because it was expecting to see an 8 GB FAT32 drive containing Windows 98, and found a 120 GB NTFS drive containing Windows XP instead. Just a guess, though.

---

