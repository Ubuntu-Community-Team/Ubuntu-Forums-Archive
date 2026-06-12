---
title: "problem installation disk partition"
date: 2015-01-18
forum: Installation &amp; Upgrades
---

### Post by ben_amor on 2015-01-18
hello ! i'm new in ubutnu.. my problem was in the step of disk partitionning ! to be agree i have to allow 3 partions for ubuntu one for the root and a second for /home and a last one for the swap (logical) ! but i'm already have 2 others partitions the first one for windows 8 loader (i don't know from where it comes) and the second for the operating system and files(files,music,games..) i just finished to allow the root and home partitions but i couldn't to allow the partitin for the swap and i have a big space which is unusable ! i can't modify it ! i think that i can just allow the disk for 4 partitions..right?  how i can solve this ! help me please

---

### Post by Bashing-om on 2015-01-18
ben_amor; Hi ! Welcome to the forum ...

Yes, you are correct that in the old legacy (MBR) msdos partitioning there is that 4 partition limit. BUT there is a way around it .... What one does is make up an 'extended' partition. This 'extended' partition counts as one of the 4 'primary' partitions.
In this 'extended' partition - as a container - one makes up 'logical' partitions. ubuntu will happily install onto these 'logical' partitions when you point the installer to them .

Consider further how you want to configure your system .. and if additional advise is required, by all means ask .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-01-18
I assume you have not yet installed Ubuntu, but it will be very useful if you can boot to a live Ubuntu system from DVD or USB and show us the output of terminal command ```
sudo parted -l
``` and if you can manage it, a screenshot of gparted.

That will show us if you have a BIOS or UEFI system, and what partitions already exist on the disk.

---

