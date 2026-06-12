---
title: "Error 13 &amp; 17 in grub"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by Charles2008 on 2008-01-05
I am having a problem with loading o/s.  I installed super grub cd and now I get the error 13 and 17 in grub when I try to start windows xp and ubuntu, respectively.  I searched the forums and found a guide to fix error 13 and 17.
This is similiar  to what I did.
sudo grub

grub> find /boot/grub/stage1

grub's response: (hd1,0)

grub> root (hd1,0) 

grub> setup (hd0)

After following the guides it still doesn't work.

Please advise, 

Thanks in advance,


Charles

---

