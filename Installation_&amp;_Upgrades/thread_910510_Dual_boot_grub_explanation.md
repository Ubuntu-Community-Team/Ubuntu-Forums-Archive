---
title: "Dual boot grub explanation"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by technotika on 2008-09-04
Hi guys I hve just dual booted using a guide on the net but am frustrated as I dont understand how I got it to work and really need to know as I can see simple solution to triple even quad boot in the future.

ok I have three hard disks.

so thats dev\sda, dev\sdb & dev\sdc

on sda I have ubuntu and on sdb I have two partitions and now vista just went on the second partition of disk 2 so thats dev\sdb2.

Ok the last part of the guide was to reinstate GRUB and add the new install as an option at the bottom.

i.e title VISTA
root (hd0,1)
makeactive
chinloader +1


this was the default setting if you used the first disk. 

Now remember I said VISTA is on the second disk second partition.
How come when I thought logically the root in grub needed to be HD1,2 in windows language disk 1 partition 2.

It didnt work, after guessing all combo's and nothing worked I ended using the exact same options in the example and it worked perfectly.

to me that option points to disk "0" partiton 1 which seems impossible as its on disk 2 partion 2. So really should be HD1,2.

Please help me understand so I can boot more linux distro's and also if I did would I just add another 4 lines pertaining to the new install. Thanks alot I can count on youbuntwo.:guitar:

---

### Post by Too Late on 2008-09-04
In grub, both disk and partition numbers start from zero. Thus, sdb2 is (hd1,1). (Assuming that sda is the booting device.)

---

### Post by technotika on 2008-09-04
cool thanks man but still dont get it

if that was the case then surely I should have successful boot from
edit (hd1,1) and not (hd0,1) as set currently

---

### Post by Too Late on 2008-09-05
Ok, sorry, I didn't read your post very well. However, as I said in brackets, the device which is set bootable in BIOS (i.e. device which MBR has grub installed) will always be hd0. So probably your computer boots from sdb. I mean, the grub disk numbers (hd0, hd1...) depend on the booting order, so they don't necessarily correspond to linux device names (sda, sdb...). Furthermore, do you have PATA/IDE or SATA disks, or both? They would make things more complicated (at least now when PATA disks are also called sd*).

---

### Post by technotika on 2008-09-06
arh right i see  - well they are all sata so thats ok but i cant be 100% which bunts is booting off so it makes sense knowing that could be the issue  - well not really an issue, just a bit of confusion on my part.

In the last 24 hours my GF hit a poisoned website on the xp laptop and it completely trashed it. 


Putting dual boot skills into action so ubuntu for safer browsing and mail and a windows for word.

Thanks for clearing things up!!

---

