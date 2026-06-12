---
title: "Help with the LABEL option in GRUB menu.lst"
date: 2006-03-15
forum: Installation &amp; Upgrades
---

### Post by DaBruGo on 2006-03-15
Hi folks,

 I have been trying to use the LABEL option on the root line (root=LABEL=mylabel) of the menu.lst file to no avail.

 I am wanting to use the LABEL option so that, whenever I remove my external USB drive and then re-attach it to my PC at a later time, I don't have to worry about the drive partition being different (sdb instead of sda etc).


Here are my details ...

I have Ubuntu installed on an external USB drive.
(Using my setup guide in my signature lines below.)

I edited menu.lst from within Ubuntu (sudo vim /boot/grub/menu.lst)
(I believe the root line included "root=LABEL=seagate" etc)

I edited fstab from within Ubuntu (sudo vim /etc/fstab)
(I believe my line started with "LABEL=seagate", [where the /dev/sda1 was originally written] and then there was a "/" in the next column.)

I used e2label (sudo e2label /dev/sda1 seagate) to assign a label (seagate) to the drive partition.  

I performed a complete shutdown and then started it back up

I make it all the way to the Ubuntu logo (past the loading modules phase) and it just sits there when saying "initializing dev".


Can someone steer me in the right direction on this one? Who else is using the LABEL option on their root line in menu.lst that is working correctly.


Any help would be greatly appreciated,

DAVE

---

### Post by DaBruGo on 2006-03-15
Can anyone help me to get this going?

---

### Post by DaBruGo on 2006-03-16
nudge, bump, bump

---

### Post by DaBruGo on 2006-03-17
nudge, bump, bump, bump

(I feel like i am playing a pinball game :D )


DAVE

---

### Post by DaBruGo on 2006-03-20
For the love of Ubuntu someone please help me with this, or point me to a good tutorial/howto on accomplishing this (using either LABEL or UUID option).
 
Thanks,
DAVE

---

