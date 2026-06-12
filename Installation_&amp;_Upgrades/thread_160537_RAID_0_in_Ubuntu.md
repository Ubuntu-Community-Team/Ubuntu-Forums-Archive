---
title: "RAID 0 in Ubuntu"
date: 2006-04-15
forum: Installation &amp; Upgrades
---

### Post by oandrew on 2006-04-15
Hi,

I am new in using Ubuntu.  I currently using a RAID 0 setup on a DFI motherboard with windows XP and BootMagic setup.  When I install the Ubuntu, it did not detect my RAID and the partitions in Windows.  I wonder where I can load my RAID driver disk during setup?  Any other thoughts?

---

### Post by ubernoob on 2006-04-15
Is it raid on your motherboard? Then it is most likely not real hardware raid, but a kind of software raid. I think it is called fake raid. You should search for that on google or in the forum.

---

### Post by oandrew on 2006-04-16
I don't think it is a software raid.  I am using the DFI Landparty UT SLI-DR using the Nvidia RAID.  Any idea?

---

### Post by ubernoob on 2006-04-16
if linux found all your disks it is fakeraid. If linux only found one disk, then it is hardware raid.

---

### Post by drbobit on 2006-04-17
Hi, I've tried to install breezy on a RAID 0 array and had the same problem with linux finding seperate drives. I'm using a Epox motherboard:

[http://www.epox-europe.com/products/view.php?product_id=294](http://www.epox-europe.com/products/view.php?product_id=294)

Now while the on-chip nForce 3 250GB Host Controller raid controller could well be fake raid. I have had the same issue with the dedicated Silicon Image Sil-3114 raid controller which is a dedicated S-ATA chip. :-k 
Is this software raid on a chip too?

If any one reading this has succesfully installed on a hardware raid 0, can you drop a post and just confirm it's possible without some sort of pre install driver madness.

thanks

---

### Post by ubernoob on 2006-04-17
I did it on a server once. Then i only found one disk.

When i bought this new computer i wanted raid myself and bought raid 5 on the motherboard. After hours of googling i finally found out that it was fake radi. What a dissapointment.... When i have time and money, i will buy a new raidcontroller.

---

