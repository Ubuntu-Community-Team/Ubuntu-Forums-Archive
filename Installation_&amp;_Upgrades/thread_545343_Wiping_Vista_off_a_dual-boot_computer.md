---
title: "Wiping Vista off a dual-boot computer"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by Old *ix Geek on 2007-09-07
How can I best eliminate Vista from a box that was set up to dual boot?  I don't want to shrink it, I want to wipe it altogether so its space on the drive can be used for file storage.

FWIW, the computer in question is running Feisty and has a 120GB drive.

---

### Post by daveshields on 2007-09-07
Just do a Ubuntu install and direct the installer to use the entire drive. If necessary, you can use the "manual" partition installation option to delete existing partitions.

---

### Post by LaRoza on 2007-09-07
> **Old *ix Geek said:**
> How can I best eliminate Vista from a box that was set up to dual boot?  I don't want to shrink it, I want to wipe it altogether so its space on the drive can be used for file storage.

FWIW, the computer in question is running Feisty and has a 120GB drive.

Just reformat that partition, and remove it from Grub if it is there. GParted in my sig, or use it from Feisty.

---

### Post by Vadi on 2007-09-07
I think this might help you, if you need to reinstall GRUB and have it point to ubuntu only:

[http://ubuntuforums.org/showthread.php?t=542683](http://ubuntuforums.org/showthread.php?t=542683)

---

### Post by Old *ix Geek on 2007-09-07
Thanks for the suggestions thus far.

I should've made clear that I **strongly** don't want to screw up the Ubuntu installation--including reinstalling it--therefore I don't think dave's suggestion to "*do a Ubuntu install and direct the installer to use the entire drive*" is a valid choice in this situation.  As with all my installations, it's taken a while to really get things EXACTLY the way I want them, and I simply have no desire to have to go back and try to recreate all the tweaking and customizing I've done.  (Which is considerable--just getting Compiz-Fusion tweaked the way I wanted it took days, because there are SO MANY possible combinations of options!)

LaRoza's suggestion to "*reformat that partition, and remove it from Grub if it is there*" sounds like the best choice so far.  I've used GParted before, so I'm comfortable with that aspect of it.

Finally, thank you Vadi for the link; I'm going to take a look at its info and keep it in mind...just in case!

---

### Post by Vadi on 2007-09-07
I was in the exact same situation as you; I did -not- want to mess up my Ubuntu. But just executing that one command from my ubuntu (it's at the bottom of my thread) worked perfect.

---

