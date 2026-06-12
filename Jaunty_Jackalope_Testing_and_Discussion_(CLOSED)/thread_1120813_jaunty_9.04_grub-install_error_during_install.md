---
title: "jaunty 9.04 grub-install error during install"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dougggg on 2009-04-09
I installed jaaunty 9.04 beta on a HP laptop and when it installs I get a grub-install fatal error during install. When I boot all I get is the Grub prompt.  I tried to get grub to install manually from the CD and got a menu.lst in boot/grub but still no menu on startup so I cant boot windows or ubuntu.  I had previously had 8.10 and it worked fine.  I am not a linux expert but if I look at Gparted the mount points for everything is 'Target' and I dont why that is I didnt do it (gremlins maybe).  there is a Target folder when I look in the root. is there a way to maybe tell grub the mount point is 'Target' but I would prefer that not be the mount point. Does anybody know a solution?

---

### Post by oldos2er on 2009-04-09
You're more likely to get help with Jaunty here: [http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

---

### Post by Bakon Jarser on 2009-04-09
> **oldos2er said:**
> You're more likely to get help with Jaunty here: [http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

The correct procedure is to hit the report button on the bottom left of the post and report that the thread should be elsewhere.  He now has duplicate threads in jaunty testing.

Just to get things booting temporarily try using a super grub disk.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by dougggg on 2009-04-09
Thanks I will try the super grub disk,  I did post over on the 9.04 board after reading the 1st response thanks

Doug

---

### Post by Bakon Jarser on 2009-04-09
If it hadn't been so early I would have suggested that you try to install grub from the live cd.  Next time I'll wait til I've had my coffee before I post :)

[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

---

### Post by dougggg on 2009-04-09
Update It is probably not a Ubuntu issue other then it appears to caused by me trying fedora before installing ubuntu 9.04 so the problem I guess is fedora didnt want me to use ubuntu.  I re-installed fedora and the booting is ok.  Is there something fedora did to the bootsector that messed it up?  I liked ubuntu better :) teach me to play around

---

### Post by dougggg on 2009-04-10
Solved,  It appers that fedora made a boot partition and for some reason because of that ubuntu was going to have to have a boot partition,  anyway I re-installed ubuntu with a small boot partion and it worked ok,  I didnt have a boot partition before with ubuntu oh well:popcorn:

---

