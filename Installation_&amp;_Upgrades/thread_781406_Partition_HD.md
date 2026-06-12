---
title: "Partition HD"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by pwc on 2008-05-04
This is a general question about partitioning my hd for a fresh install of Hardy. I'm planning to install with the alternate cd on a 160 GB disk(sata). This time I will set up three partitions as "/", "/home" and "swap". With my present Gutsy it's the standard "/" and "swap"(I'm finally wising up after using Ubuntu since 6.04). 
 Most "How to's" say to allot only 5-10 GB for the "/" partition. But I'm planning on installing VirtualBox with XP as in my present setup. Now my question is: Won't the hd space for XP be taken up in the "/" partition and should I allot more space(say 20 GB) for it? 

pwc :confused:

---

### Post by TenPlus1 on 2008-05-04
Usually I give Ubuntu's / partition 30gb for any programs that may need to be installed in the future...  As for the swap file, that's typically the same size as memory available and the rest of the hard-drive for your /home directory...

VirtualBox uses a hidden directory in your /home partition/folder so it wont actually be using the / filesystem...

---

### Post by Pumalite on 2008-05-04
Yes. I have 20 GB assigned to '/' in a 500 GB drive.

---

### Post by pwc on 2008-05-04
OK, thanks for both your responses, I'll go with 20GB and 4GB for swap. That will leave about 135GB for /home.

Thanks again,
pwc

---

### Post by Pumalite on 2008-05-04
Good luck.

---

