---
title: "uninstalling ubuntu"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by sera on 2006-12-19
I was wondering how to uninstall ubuntu and use XP fully.  I have a dual boot of both.  Thanks. :)

---

### Post by bulldog on 2006-12-19
Just format the ubuntu partitions in what ever you want and it's gone.
GRUB is remove able with the windows install cd in the recovery mode console.

---

### Post by Sef on 2006-12-19
> Just format the ubuntu partitions in what ever you want and it's gone.

Use [GParted]("http://gparted.sourceforge.net/livecd.php") to format the disk.  It's on the LIve CD (under Applications > Accessories, I believe) or just download [GParted]("http://gparted.sourceforge.net/livecd.php") and burn it to a disk.

---

### Post by sera on 2006-12-20
I can't find a way to format the partition with ubuntu, nor can i change the menu.lst in the grub folder to set windows as the default, since it says i don't have the authority to save the file after i alter it.  ](*,)

---

### Post by Waitrose Carpark on 2006-12-21
I'd like to uninstall Ubuntu as well.

Do I take it I use an XP disc, start the recovery console and do a 'fixmbr'??

---

### Post by bigken on 2006-12-21
ok do this 1st delete your ubuntu partitions using the gparted liveCD
then boot from your windows xp cd when prompted select R for repair console 
select the windows partition usually 1 at the prompt type fixmbr enter then fixboot enter lastly type exit and your pc will reboot into windows ;)

---

### Post by Waitrose Carpark on 2006-12-21
Yep, works perfectly. Just boot off the XP disc.

---

### Post by bulldog on 2006-12-21
> **sera said:**
> I can't find a way to format the partition with ubuntu, nor can i change the menu.lst in the grub folder to set windows as the default, since it says i don't have the authority to save the file after i alter it.  ](*,)

To change the menu.lst you have to use ```
gksudo gedit /boot/grub/menu.lst
```
Change what you want and save it.
You can format your ubuntu partition with windows as well as far as I know.

---

