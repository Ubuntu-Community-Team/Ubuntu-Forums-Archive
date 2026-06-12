---
title: "HP Prolliant installation error"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by fritzdjam on 2011-11-12
HI,
I make my first step on linux, i usually use it on x86 computer, now I have a prolliant ML 370, I have install linux on it and on the first boot I have on error.
Message:
*Attempting Boot From Floppy Drive (A: )*
*Attempting Boot From Hard Drive (C: )*
*error: fd0 read error*
 
I Have 6 disk divide on 2 raid
Raid1 with 2 disk
Raid1 with 4 disk
 
Thanks for your help

---

### Post by darkod on 2011-11-12
That says fd0 error, floppy error. Are you using floppy to boot? If not, have you tried disabling the floppy in BIOS, just make it invisible for the system.

---

### Post by fritzdjam on 2011-11-14
Thanks Darko
I disable the floppy,but nothing happen, it 's like there's no hdd. I saw that there is no scsi bios installed, Need more help

---

### Post by darkod on 2011-11-14
Did you use the server or alternate cd to install, or the desktop cd? Desktop cd doesn't support raid and the bootloader might not have been installed properly.

Also, which disk did you choose as destination for the bootloader? Did you set in bios to boot from that disk?

---

### Post by fritzdjam on 2011-11-14
I used the server cd and I installed the bootloader on the fist raid

---

### Post by darkod on 2011-11-14
Can you select in bios to boot from that array? I have no idea what the bios looks like.

---

### Post by fritzdjam on 2011-11-14
Look in the attach file a tell me what do you think

---

### Post by darkod on 2011-11-15
Hmmm, I can't be sure, but it looks correct to me. If it still doesn't boot, it might not be able to boot from the raid card (which would be very stupid). Look in boot devices how the raid controller doesn't exist in the list.

Another question, have you considered using the ubuntu software raid? In that case, enter your raid card and delete all the arrays, leave the disks as ordinary non-raid disks.

When doing the server setup in the partitioning step, you create the partitions you want and then select Configure Software RAID. Basically the OS is assembling raid arrays from the partitions you tell it to. You can also do 1+0 and 5 with software raid. Some people are even more satisfied how it works compared to raid card.

Also, if you are willing to go for it, I would check that the server can boot from any disk first. Destroy your current arrays, and install ubuntu server without any raid just on one disk. To see if the server will boot it. Have you tried that?

---

