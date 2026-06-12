---
title: "MBR does not load the proper grub"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by ardent on 2009-11-27
So, I created a Moblin OS on a new partition a while back which used GRUB legacy and would not link to my Ubuntu OS, and thus not allow me to start Ubuntu. I read online that you had to change Moblin's menu.lst, but the problem was that my laptop could not even boot up Moblin so I decided that I would remove Moblin from my laptop, by destroying its partitions. Now whenever I boot up my computer, I get to the grub command line, and I'm not sure how I will be able to boot into GRUB, the one which would show Ubuntu 9.04. 

I have the menu.lst (changed it to menu.txt, for some reason I can't upload the menu.lst directly) for the Ubuntu GRUB. 

Is there any way in the Grub Command line, where I might be able to get the MBR to direct itself to the Ubuntu GRUB?

---

### Post by ardent on 2009-11-27
Never mind. I got it to work using one of the guides posted to reinstall Grub for 9.04.

---

