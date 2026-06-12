---
title: "dual boot hardy &amp; XP problem"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by alicemoon on 2008-04-30
I have 2 sata drives running XP on one and loaded hardy on the other. Initialy Hardy loads fine (a few issues to sort out but essentialy ok)and I can choose to use hardy or XP without problems from the menu as long as I have the drive hardy is on as the first boot **But** if I swop and make the drive XP is on the primary drive then windows starts to load gets halfway through loading programs and crashes. If I then swop back to the ubuntu drive hardy loads ok but xp continues to crash until I disconnect the hardy drive. I have tried this with 2 different sata drives that I loaded hardy onto and the same thing happens with both.
Can anyone explain why?
I know I could just leave the primary as the ubuntu drive and never swop but I am worried it might not be stable and my xp will crash down the line. I want to make the swop to ubuntu but still need to run xp for a couple of programs until I can make the final leap.
Any help and explanations appreciated as I have no idea why this is happening.

---

### Post by Pumalite on 2008-04-30
Was XP installed first in first drive?. How did you install?

---

### Post by alicemoon on 2008-04-30
XP was already installed - I did not want any problems overwriting the drive so I changed the xp drive to secondary in the bios and  the empty sata drive became primary, rebooted and installed ubuntu from the cd onto the empty drive

---

### Post by Pumalite on 2008-04-30
That's your problem. You should have installed with XP connected as first drive and let Grub install to MBR.
Post:
sudo fdisk -l
cat /boot/grub/menu.lst

---

### Post by alicemoon on 2008-04-30
thanks - I will have a go installing that way round and see what happens.

---

### Post by Pumalite on 2008-04-30
Good luck.

---

