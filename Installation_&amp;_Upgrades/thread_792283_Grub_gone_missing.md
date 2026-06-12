---
title: "Grub gone missing"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by averageidiot on 2008-05-12
My setup is windows XP on one hard drive and ubuntu on another. i had it working so that grub would come up everytime i booted and i had the choice b/t ubuntu and XP. now i removed my ubuntu drive, and reinstalled XP on my XP drive. I put my ubuntu drive back in hoping that everything would still be the same but now grub doesnt come up when i boot it, it boots straight into XP. how can i fix this?

---

### Post by Rallg on 2008-05-12
Not sure if I understand your setup. The Ubuntu drive is external, or another partition on the same hard drive as XP?

I am not familiar with tricks for an external hard drive. If the setup involves partitions, try this: Boot to the Ubuntu live CD (nearly any Linux will do), mount your drive, and launch GParted from the live CD. Then, look to see which partition has the "boot flag." If necessary, move the flag.

---

### Post by averageidiot on 2008-05-12
two seperate internal hard drives. one has XP and one has ubuntu.

---

### Post by meierfra. on 2008-05-12
This link explains how to restore grub:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

