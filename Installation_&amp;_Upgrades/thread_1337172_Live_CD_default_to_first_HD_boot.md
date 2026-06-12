---
title: "Live CD default to first HD boot"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by cesarbrod on 2009-11-25
I am facing a problem where my Ubuntu on a HP Proliant ML110 server just won't boot grub unless I boot from the live CD and ask it to boot from the hd (the first hd). I have researched all around to overcome this problem and, actually, if I could build a live CD that would just have isolinux defaulting to hd instead of "live" my problem would be solved. Any hint?

---

### Post by cesarbrod on 2009-11-25
Ok! I first use remastersys to do a Distcdfs, then I edit grub/menu.lst on the remastersys ISOTMP directory and then do a Distiso! :-D

---

