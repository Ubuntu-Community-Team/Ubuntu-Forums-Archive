---
title: "Big Windows/Ubuntu Installation problem"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by DrGiggles420 on 2011-10-31
Okay, I have a HUGE problem. I installed Linux on my Dell Laptop alongside a Windows Vista Partition. The Windows caught a virus and needed to be reformatted. So I forced it to take me to the start-up repair wizard and ran that. It said it couldnt repair, so I said other system tools and reformatted my Windows partition to factory state! YAY!
Wrong... Upon reboot the system tells me:
Error: No such Disk 2A8AD90C8AD8D583
Error: No such Device

Pretty much like that. My Ubuntu started PERFECT! And I can even SEE the windows files on my Ubuntu, and I can SEE that it DID what it was supposed to. But Grub wont bring me to it D: Ahhhh!!! Help meeee!


I simply cannot afford to fall further behind in what I Was working on >.<! Luckily I backed up my beats and stuff I was making for a local performer and can get those back but now I have to re-install FLStudio and everything! The sooner the help the better!

---

### Post by ajgreeny on 2011-10-31
You probably need to simply run ```
sudo update-grub
``` in terminal from your Ubuntu OS to add windows back in to the grub menu.

The reformat of the windows partition will mean that the UUID etc etc, of that partition has changed, but grub will still be looking for the old UUID.  Updating grub should put everything right again.

---

