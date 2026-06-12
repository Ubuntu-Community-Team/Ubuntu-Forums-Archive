---
title: "XP will not boot from grub"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by conormiller23 on 2010-06-13
I installed ubuntu 9.10 on my desktop. It installed fine and i upgraded to lucid, which is also running fine. When i was installing ubuntu I used gparted to make a new partition for ubuntu. My desktop has two drives, one xp system drive and a storage drive. I chose to use the storage drive. Now, when i try and boot xp from grub all i get is a blinking cursor in the top left corner. Can anyone help me? Heres fdisk -l and update-grub

---

### Post by darkod on 2010-06-13
You can try to get more detailed information by running the boot info script, but I think when the upgrade process asked you where to install grub2 you also selected the XP partition.

If that is true, you can use this procedure to remove grub2 from /dev/sda2, so that's partition #2 on disk /dev/sda:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by conormiller23 on 2010-06-13
darkod, thank you for replying so quickly. i did what you suggested. It didnt work, but something did change. I can now boot into /dev/sda1, which seems to be a recovery partition. Recovery software starts, does its thing, asks to restart and... nothing. same deal. Cane boot into windows, just get the blinking cursor. I though i knew what i was doing, but im still so new to this, but willing to learn, that i just need some more help. Any more ideas?

---

### Post by darkod on 2010-06-13
Are you sure you did it for partition #2 and not for partition #1?

If you are, run the boot info script and post the content of the results as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

That should give us more details.

---

### Post by conormiller23 on 2010-06-13
Oh what a cruel twist of fate. Ok, the whole point of this was to move entirely to ubuntu, seeing as i'd done it myself and thought that my dad could benefit from it too. Move and forget. He uses outlook express, the username and password of which was forgotten a looong time ago. Thanks to the wonders of automatic sign in. The only thing i way i could see of getting his mail was to boot back into windows, set outlook to forward his mail to gmail and forget about it. When i used testdisk on the first partition, it successfully booted into the recovery partition, which i used, to recover windows. The twist of fate being that you'now helped me to get into the primary windows partition. I'm looking at it right now. Restored to factory settings and said username/password forgotten. It was all for nothin. With that password gone, there was no point to any of it. I cant thank you enough though. I've learned something new and isn't that what its about sure. Thank you anyway darkod. Its been a pleasure, conormiller23

---

### Post by oldfred on 2010-06-14
I converted to thunderbird so long ago I have forgotten how. I do not know if this asks for a password or just converts.

[http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Migrate_from_Outlook_Express](http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Migrate_from_Outlook_Express)

---

