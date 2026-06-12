---
title: "Getting 'Error 18' on boot"
date: 2005-05-13
forum: Installation &amp; Upgrades
---

### Post by sfrazao on 2005-05-13
Hi,
I've sucessfully installed the  Hoary 5.04 on an old home PC ( AMD K6 @450Mhz).
The problem is that I'm getting an error on the startup:
--
GRUB Loading Stage 1.5
ERROR 18
--
I've already installed it several times, but I'm allways getting this error, prventing me to proceed.
Can anyone help me?

Thanks.

 
Please note the way I solved this problem:
Thanks to your replies I noticed that the HDD setup on Bios was at LBA mode.
I've scanned the HDD (on Bios) and changed it to Normal mode.
I realized that Ubuntu has progressed a litle bit on the boot, but not completely.
I've get back to Bios and scanned the HDD again and changed it back to LBA mode again.
Believe it or not, it worked out and I'm using it without no issues!
Thanks to you all.
Sergio.

---

### Post by pointym5 on 2005-05-13
Error 18 means:
> 18 : Selected cylinder exceeds maximum supported by BIOS. This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).


---

### Post by transkinetic on 2005-05-14
I beleive the solution is to create a smaller partition at the beggining of the disk specifically for grub. Perhaps someone with more knowledge than me will be able to outline the procedure for you.

---

### Post by c_dog on 2005-05-14
The underlying cause of this is that GRUB polls the BIOS to get information about the drives attached. Some buggy BIOSes do not translate the sizes of the drives right or really see Big drives properly. The best first step in this case is to find out if there is an updated BIOS available for your motherboard or drive controller from the manufacturer. Everything you do to side step this problem may come back to bite you later.

---

