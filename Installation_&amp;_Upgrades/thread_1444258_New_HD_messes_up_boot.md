---
title: "New HD messes up boot"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by centrum on 2010-04-01
I have an external HD. When I have it plugged in via esata, and powered up, it messes up the boot process. Ubuntu was installed on sdb5, but when the external is powered up sdb5 becomes sdc5.

I'm running Ubuntu 9.10 and Windows 7. I used EasyBCD/Grub 2 to get everything booting properly. I'm typing from my Ubuntu installation right now. I just have to turn off the external drive to get in here. 

Any help with alleviating this problem is greatly appreciated. I'm kind of a noob, so bear with me. 

Thanks

---

### Post by oldfred on 2010-04-01
My three drives are ordered based on the sata port numbers on the motherboard. 
Is you esata set up on the first port, if so I would move it to a port after your internal drives.

---

