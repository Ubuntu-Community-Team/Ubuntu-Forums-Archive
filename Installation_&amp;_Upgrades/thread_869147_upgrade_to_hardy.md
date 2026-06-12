---
title: "upgrade to hardy"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by heiNey on 2008-07-24
hi all,

ive been trying to upgrade to hardy, but the installation keeps telling me i need to free up 1.5 gigs of space.  i tried deleting programs i dont need, and cleaning up stuff, but cant free up that much space on my / partition, since i dont know what i can or cannot delete without breaking the system.  i only allocated 5 gigs to my / partition, and also have a /boot, /tmp and /home partitions.

i was wondering if i did a fresh install over the / partition, would i have to reinstall all the programs and themes and settings ive already installed?  or are they saved since i have a /home partition?  i want to upgrade, but i dont want to lose all my settings and programs.  anyone know of the best way to do this?  thanks!

oh, and im currently on gutsy.

---

### Post by tamoneya on 2008-07-24
you would lose the programs but keep the configurations if you did that.  Not the worst thing but it wouldnt be fun.  You would have to reinstall each program and then it would find its configuration files in your home folder and then it would set itself up like it was before.  What you should do is back your /home up.  Then try using gparted to increase the / partition size.  Then do the upgrade.  Otherwise do as you suggested above because it is your only other option.

---

### Post by GreenN00b on 2008-07-24
The settings for programs are saved in the /home directory for each user.
If you reinstall you will have to reinstall the programs again, but they will recognize the settings from home folders.

You can also create a new partition, copy the contents of / to the new partition and then edit /etc/fstab to mount the new partition as /.
You should do some more research before attempting this ...

---

