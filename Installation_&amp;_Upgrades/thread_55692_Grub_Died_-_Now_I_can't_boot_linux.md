---
title: "Grub Died - Now I can't boot linux"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by TiMBuS on 2005-08-09
So I had a set up where I could boot windows, and linux from seperate HDD's. Pretty standard. It was going fine till my latest reboot, where all of a sudden there's no option to even attempt to load windows. Like the top half of my menu.lst just vanished. Now, if I try to load the linux option I get a massive amout of errors regarding the fact the 'filesystem is read-only.' - lotsa dev/null errors. I mean LOTS of /dev/null errors guys
Recent things I've done:
Changed the fstab so that my windows partition loads with write privelages (uh, was just testing it to see what happens) -.-
Editing /etc/init.d/'forgotten name' - something about misc. boot commands - I added a few required modules, cos they dont hotplug.
Updated the while system with apt-get (60 new updates.. took a while.) - I left it going overnight.

What I dont understand is how grub's config just 'disappeared' - I've also had a few modules corrupt themselves for no apparent reason. If you ask me thats not normal. Suggestions? 
How can I get back into linux.. I'm thinking about trying this windows driver, one that lets me write to ext2 so I can edit stuff from windows, but it would be real nice to know exactly what to fix. Honestly I dont think that the fstab change could be the source of error.

---

### Post by PeP on 2005-08-09
apply standart plan B:
boot from live CD
fsck
chroot to your former root partition
restore grub or replace it with lilo just for one boot

---

### Post by TiMBuS on 2005-08-09
yeah but the problem is that even though the 'windows loader' part of my grub config isnt there, the rest of the setup is just fine.. i dont think its a grub issue... but of course i'll give it a shot when i get back home

- maybe i should add that i used the app 'explore ext2fs' to pull menu.lst out and i saw that the setup was fine, minus the windows bit.

---

