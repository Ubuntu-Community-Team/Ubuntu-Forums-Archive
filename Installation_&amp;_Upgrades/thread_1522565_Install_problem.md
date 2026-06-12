---
title: "Install problem"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by Tethyrian on 2010-07-02
So I found that I had a new IDE HDD laying around and decided to install Ubuntu 10.4 on it. Everything was going fine until I got to step 4. The partition step. :S. The window that show the step shows the normal screen for setting up partitions except that there is nothing within the box for the partitions (What I was expecting since it is a new HDD basically). But, all the buttons on the window are grayed out (can't click them). All of them except for the forward, back buttons whatever. I clicked forward figuring it might do it itself but to no avail. How will I install Ubuntu onto this HDD? Any help?

---

### Post by dino99 on 2010-07-02
its easier to prepare the partitions with a good formatting tool like partedmagic

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by irv on 2010-07-02
Boot with the live CD goto System> Administration> gparted. find your new hard drive and format it with ext4. Is it the only drive you have installed in the computer? And are you going to dual boot? If you are, then you have to install windows first and then do the Ubuntu install and let it install side by side.

---

