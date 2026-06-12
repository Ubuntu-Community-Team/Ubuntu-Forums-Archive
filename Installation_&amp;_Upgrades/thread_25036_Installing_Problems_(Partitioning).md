---
title: "Installing Problems (Partitioning)"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by Qwacko on 2005-04-09
Hi

I am trying to install Ubuntu 5.04, when the install process gets to the partitioning step it correctly finds the partitions which i edit and when i click the apply changes to drive (or something like that, can't remember exactly waht it says, but basically it is the button to proceed to the next step) the process of changing the partition table starts and quickly rushes to about 40% where it freezes,  i have tried leaving the installer alone for  awhile to see if it will proceed. Does anyone have any idea what may be causing this, maybe i need to leave it for longer, how long would you expect this process to take?

System:
Athlon XP 2500+
Gigabyte GA7N400 Pro2 (Sil 3112 Sata controller)
80Gb Seagate 7200.7 SATA HDD
512 MB Ram
Raedon 9600XT
(If these help)

Thanks in advance
James

---

### Post by erkki70 on 2005-04-09
Hi,
Could you precise what kind of install you want to perform?
Single or dual boot along with Windows?
Is your HD already partitionned?
What is exactly your selection when editing your parttion table?

More details will help.  :wink: 

Cheers,
Erkki

---

### Post by Qwacko on 2005-04-09
Hey

I am just trying to install Ubuntu Hoary Hedgehog 5.04. I am trying to do a dual boot with windows, my drive already has two partitions. When i go into the partitioning section of the install i resize one of my partitions (Not the one with windows installed on it) down by 10Gb and then select the free space and select automatically partition space, and it creates a swap space of about 450mb and about 9.5Gb for / , i then select write partitions to disk, and it proceeds into a progress bar, which freezes at about 40% complete. I think that is all i can really think of, if there is anything else that may help please feel free to ask.

Thanks Heaps
James

---

### Post by erkki70 on 2005-04-09
What's the type of the partition you're trying to resize to 10gb? NTFS, Fat32, other?
Do you actually have anything on this partition?
Have you tried resizing to something else than 10gb?
Have you checked if you can use the same settings as the partition wizard and do the same manually?
Just ideas though but might be worth trying...

Good luck.

Cheers,
Erkki

---

### Post by Qwacko on 2005-04-09
Hey

Thanks alot for your help, i managed to get it working by creating the partitions i needed using partition magic before i began the install.

Thanks
James

---

