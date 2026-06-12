---
title: "Lost ubuntu after xp install - solution"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by noswal on 2006-06-10
In an effort to use Steam and play half life with less problems I installed winxp over my win98 partition, the other partition holding ubuntu. And so XP installed fine but there was no unbuntu menu showing (GRUB). After reading through forums and search here [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows), tried the install cd and the live cd method but niether worked. (though did use Gparted to locate partion entries).

I found this little program the simplest editor which worked in XP to create Grub  w32grub.zip  found at [http://www.skyjammer.com/files/knoppix/](http://www.skyjammer.com/files/knoppix/)

Rereading through wiki and forums to remember what my kernal number was:  Ubuntu 5.10    linux-image-2.6.12-10-386

Searched to see what the Grub (start up menu) should look like, found here:
[http://ubuntuforums.org/showpost.php?p=1119061&postcount=4](http://ubuntuforums.org/showpost.php?p=1119061&postcount=4)

Adjusted the numbers for my pc where xp is hda1  = hd0,0 and ubuntu is hda2 = hd0,1

and it worked for me.

Now there was probably something I should have read before installing xp which I'm sure someone will add. ;)

---

