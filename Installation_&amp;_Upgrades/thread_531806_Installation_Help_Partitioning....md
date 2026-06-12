---
title: "Installation Help: Partitioning..."
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by bdsatish on 2007-08-22
Hi frenz,

Yestday, i was tryin 2 install Fiesty (kubuntu) frm the "Alternate CD"
Dual-boot with Win XP.

Wen the partitioning screen came up, i chose "Manual partitioning":

The screen read thus:

---------------------------------------------------------------------------
SCSI1(0,0,0) (sda) - 80.0 GB ATA ST38001A
#1 primary 21.0 GB B K fat32 /media/sda1
#5 logical 21.0 GB K fat32 /media/sda5
#6 logical 21.0 GB K fat32 /media/sda6
#7 logical 17.1 GB K fat32 /media/sda7

-------------------------------------------------------------------------

In windows, I used to get 4 drives (in above order) as C:/ , D:/ , E:/ 
and F:/

I plan to use D:/ drive (#5 logical, see abv tabl) completely for Ubuntu.

I've cleaned-up the D:/ drive , except for 2 GB of immovable windows-application programs.

So, i have some 18 GB left. I need, 16 GB for ubuntu in itself and 2 GB swap...

But i dont know how to proceed from the above screen & do this... help !

---

### Post by merlinus on 2007-08-22
If you want to use #5 logical, then select that and ubuntu will use all of it.

If you want to save windows files that are on that partition, then you will have to resize it.

My advice:  let ubuntu have all of one of your three logical partitions for itself.

-merlin

---

