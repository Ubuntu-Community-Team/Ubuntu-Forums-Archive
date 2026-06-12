---
title: "I Have a strange problem with the size of the ext4 partition"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-14
Gparted said that the size of the partition is 37.34 Gib in use 4.54Gib not in use 32.73 Gib
this partition is sdb3 i have another partition which is swap 1.91Gib which is sdb2 but is 
irrelevant to the problem my problem is that when i check with baobab he said i have the 
capacity of the file system is 36.8GB in use is 4.0GB and free is 32.8

so far so good i can understand that there is a minor difference between the size of the partition and the size of 
the file system but when but when i simply go to places-computer-file system at the bottom of the windows it said 
24 items available free space 30.9GB so where did 1.9GB go?

thanks in advance.

EDIT:
is it had anything to do with the swap partition which is also 1.9GB or is it a mere coincident? 
becausethe swap partition has it's own separate space i created both partitions manually and i gave the swap 2048mb.

---

### Post by popat007 on 2010-04-14
I too have strange readings of my filesystem, when right click it shows totalling 128.0 TB :P (wish i had) look at my prt.scr. bellow

---

### Post by aviramof on 2010-04-14
no one knows?

---

### Post by SgtPepperKSU on 2010-04-15
The lack of consistency in using units when describing sizes makes it hard to say where, or if, there is a problem.

Please repost the details (or screenshots) paying close attention to the units displayed in the various locations.

Some specific things to keep in mind:
GB != GiB (1 GB ~= 0.93 GiB)
MB != mb != MiB (1 MB = 8000000000 mb (assuming byte==octet) ~= 0.95 MiB)

---

### Post by aviramof on 2010-04-15
Gparted=37.34 Gib partition size  4.54Gib in use 32.73 Gib not in use 
baobab=36.8GB partition size 4.0GB in use  32.8GB is free
nautilus=30.9GB is free.

that how it was when i posted this thread at least so the problem is with nautilus i guess.

---

### Post by SgtPepperKSU on 2010-04-15
Thanks.  I wasn't sure the correct units were used in your original post due to some numbers being completely without units and using mb when you assumedly meant MiB.  Still, both posts say Gib when they should (again, assumedly) be GiB.  These points may normally be nit-picks, but when trying to see if the sizes displayed are correct, they become very important.

Converting everything to common units:
```

               Size      Used      Free
 Gparted: 37.34 GiB  4.54 GiB 32.73 GiB
  baobab: 34.27 GiB  3.73 GiB 30.55 GiB
nautilus:                     28.78 GiB

```

So, there seems to be fishiness all around.  None of the numbers seem to line up with each other (even considering filesystem overhead)...

Unfortunately, the fact that there doesn't seem to be any rhyme or reason behind those numbers leaves me without any ideas.

---

