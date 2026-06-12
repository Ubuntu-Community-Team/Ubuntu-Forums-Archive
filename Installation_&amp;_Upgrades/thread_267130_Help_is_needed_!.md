---
title: "Help is needed !"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by DesignerX on 2006-09-28
I just bought a 80GB fujutsi hd for my laptop/noteboook computer.
Firstly I installed a non-linux OS on the first 50GB, leaving 30GB dead space (unpartitioned) for the ubuntu 6.06.
I download from the ubuntu.com site the ubuntu 6.06 installation image, burned it on a cd, and tried to install it on my laptop (I did all on my PC ofcourse) 
When I tried to install ubuntu 6.06, on the mounting root file system phase, I got kicked to the terminal with a message saying somthing like "bash: Cannot access tty..".
Ok, so I installed ubuntu 5.04. Which went just fine. (I thought that maybe the dead space made problems with 6.06) 
Right after the 5.04 installation I tried installing the 6.06.
The mounting root ... phase went fine , but just after it, on the "Adding Live cd user" phase I got kicked to the terminal but with messages like "Buffer I/O error, logical block 9095" and than the same message with 9096 , and so on......  

Does it mean the HD is damaged ? (cause the ubunto 5.04 didn't make any trouble). I just bought it !!!
Is it something with the 6.06 installation (altough it passed all phases on my Home PC)

Does anybody else encoutered similiar problems ???

thx for any help you can get...

---

### Post by croak77 on 2006-09-28
It's could just a bad burn. What non-linux OS did you install? Can you check the HD for errors from that OS?

---

### Post by DesignerX on 2006-09-28
The other OS is winXP.
I have just upgraded ubuntu 5.04 to breezy (5.10) and things work great.
I'm just afraid of finding these bad blocks later.

Do you know of a good program for scanning an entire HD for bad blocks ?

thx.

---

### Post by croak77 on 2006-09-28
You can use fsck but only use it on filesystems that are not mounted.

---

