---
title: "triple boot- now I have grub and grub2 at same time. help!"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by mb300 on 2010-09-23
Hello!

I mucked things up a bit--

1) I had only windows on my drive.

2) Using 10.04 on USB, I made a 10gb ext3 partition and a 1gb swap area and installed 10.04. No problems at all using grub2, and the GUI is nice for dummies like me.

3) I got antsy so I made an 8gb partition and installed 8.04 on it. It automatically installed grub (the old grub).

Now when I boot my machine the Old Grub loads, not Grub2. I can select 8.04, 10.04, or XP no problem.

When I select 10.04 and use the GUI I can see 10.04, 8.04, and XP, but things are in a different order (clearly the grub2 order).

Questions:
1) How can I get grub2 to take over booting? (I like the GUI)
2) I'd like to install puppy linux too, but I'm afraid of really screwing things up. Can someone recommend a safe way of installing it (besides just running from a USB- I've had mixed luck using USB OS's over long timeframes).

Thanks!!!

---

### Post by zvacet on 2010-09-23
First install Puppy on some empty space (ifi I remember corectly you have option not to install grub) and after that reinstall grub2 following [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Rubi1200 on 2010-09-23
> **zvacet said:**
> First install Puppy on some empty space (ifi I remember corectly you have option not to install grub) and after that reinstall grub2 following [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
+1 
just make sure to follow all the steps correctly, including installing GRUB to the MBR of sda and mounting the 10.04 partition.

Also, make sure to run ```
sudo update-grub
``` after rebooting.

---

