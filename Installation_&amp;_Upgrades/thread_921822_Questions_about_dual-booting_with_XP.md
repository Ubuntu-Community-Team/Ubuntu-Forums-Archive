---
title: "Questions about dual-booting with XP"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by andrewwg94 on 2008-09-16
I'm confused about what i have to do on the partition screen. right now, this is how my computer is partitioned:

Hard Drive #1 (80GB):
-Windows Partition (42 GB)
-Partition (30 GB)
-Recovery Partition (5GB), hidden

Hard Drive #2 (17.2 GB):
-Partition (16 GB)

I don't understand all that stuff about root, home, and swap partition.

also, will I be able to set the boot loader so that windows starts automatically unless i press a button to bring up the menu?

and how can i remove Ubuntu if something goes wrong?

---

### Post by Pumalite on 2008-09-16
Get Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it. Shrink XP (right click on XP, choose 'resize' from the menu)
In the new space, make 3 'New' partitions:
10 GB for '/'
The size of your RAM for /swap
The rest for /home.
Remove Gparted. Stick in your Live CD, go 'Manual' and use the already prepared partitions.
Backup everything before you start

---

### Post by andrewwg94 on 2008-09-17
> **Pumalite said:**
> Get Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it. Shrink XP (right click on XP, choose 'resize' from the menu)
In the new space, make 3 'New' partitions:
10 GB for '/'
The size of your RAM for /swap
The rest for /home.
Remove Gparted. Stick in your Live CD, go 'Manual' and use the already prepared partitions.
Backup everything before you start

why do I have to backup everything? Is this going to format the hard drive?

---

### Post by Bucky Ball on 2008-09-17
Nope. But better to be safe than sorry, huh? Just rule of thumb when you are doing this in case of user error (eg, you do *accidentally* format the wrong partition). In theory, only the Windows XP partition is being shrunk and 3 new partitions are being added in the empty space, if I read Pumalite correctly.  :)

---

### Post by andrewwg94 on 2008-09-17
> **Bucky Ball said:**
> Nope. But better to be safe than sorry, huh? Just rule of thumb when you are doing this in case of user error (eg, you do *accidentally* format the wrong partition). In theory, only the Windows XP partition is being shrunk and 3 new partitions are being added in the empty space, if I read Pumalite correctly.  :)

is it possible to leave the windows partition alone?

---

### Post by Pumalite on 2008-09-17
You can do that if you have enough space.

---

### Post by Bucky Ball on 2008-09-18
[quote=andrewwg94]is it possible to leave the windows partition alone?[/quote]

Yep, but that is an awful lot of Windoze and programs on that 42Gb partition. If you are keeping important personal data on there as well, understandable, but not ideal - reason: if you need to re-install Windoze for any reason you are gonna need to fish your data out of there, but if the partition dies, that will not be possible. I try to keep Windoze on its own partition but that is my personal bent - when I actually used it a lot I used to reinstall it a lot! Means you can just kill that partition (wipe clean) and slap windoze back on easily, without having to go through backing up the valuable stuff on that partition/drive.

Hard Drive #1 (80GB):
-Windows Partition (42 GB) 
-Partition (30 GB)
-Recovery Partition (5GB), hidden

Hard Drive #2 (17.2 GB):
-Partition (16 GB)

You could plop Ubuntu on your Hard Drive #2 (17.2Gb), or you could make space on Partition (30Gb) on Drive #1 and plop it there. Up to you.

---

### Post by Nuuk on 2008-09-18
Andrew, you need to make two partitions out of free space on your hard drive. (One for the OS and the other is a SWAP partition)

So to make free space, identify that empty partition (30 gig in your case) and delete it. Yes, it's OK to do that.

You will then be shown that you do have some free space on your hard drive. You will now make your two partition out of that.

Right click on FREE SPACE and then select NEW PARTITION

I subtracted around 512 meg from the total free space and used that figure to format the / partition. Leave the other details as EXT3 and name it /

The hard drive is then rescanned.

Right click on FREE SPACE again to make the SWAP partition.
Accept the remaining space for the size, select SWAP as the type of folder, name it 'SWAP' and click APPLY.

You should now be able to proceed with the Ubuntu installation.

---

### Post by Bucky Ball on 2008-09-18
> **Nuuk said:**
> So to make free space, identify that empty partition (30 gig in your case) and delete it. Yes, it's OK to do that.


***Not*** if there is valuable data on it. Warning: if there is, back up as mentioned earlier on. See? Like we said: good idea to backup anything you don't want to loose, just in case. :)

---

### Post by Pumalite on 2008-09-18
Backing up is a matter of good practice in the installation of ANY NEW OS.

---

