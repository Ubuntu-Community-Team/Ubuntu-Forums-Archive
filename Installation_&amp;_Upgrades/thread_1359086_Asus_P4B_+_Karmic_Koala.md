---
title: "Asus P4B + Karmic Koala"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by Ubidia on 2009-12-19
I'm a newbie but I've already installed 9.04 as parallel intallation on my machine twice without any problem. 
Now I tried on a friend's machine with a Asus P4B Mobo and failed.
The installation do run, but when restarting I get "GRUB_" and that's it.
Somewhere I read that sometimes could take up to 5 Minutes on a old machine for Grub to start, so I waited well above 5 min to no avail.
I tried the parallel installation and than Ubuntu Karmic Koala alone.
Windows XP do work as work a Ubuntu Live CD.
I tried creating the partitions myself (I follow the instructions found somewhere on the net - could I possibly have done something wrong with it) since I read somewhere that could be a problem with Linux unable to read after the 1024 cylinders.
The partitions I created were /boot little less then 1MB, /home 10GB, / 15GB and a Fat32 partition in the hope to install there later on XP.
Still got exactly the same issue.
I search the net for issues with that Mobo and Linux but I didn't find anything.

Do my friend have to give up to enjoy Ubuntu?

Are maybe other distro friendlier with such a Mobo?

After I created the partitions I just installed Ubuntu. I'm not sure if during the installation Ubuntu would install automatically the "/boot" in the /boot partition (and so on) that I created or if I have to "point" to it after the installation.


In case that could make any difference the HD is a 160GB Maxtor. 

If I've forgotten some important infos, please let me know.
Thanks!

---

### Post by lmarmisa on 2009-12-19
I recommend you to define 3 partitions:


[LIST=1]
[*]Root / - 10 Gbytes.
[*]Home /home - your choice.
[*]swap - 2x the size of your RAM memory.
[/LIST]
Best regards,

Luis

---

### Post by Ubidia on 2009-12-19
> **lmarmisa said:**
> I recommend you to define 3 partitions:


[LIST=1]
[*]Root / - 10 Gbytes.
[*]Home /home - your choice.
[*]swap - 2x the size of your RAM memory.
[/LIST]
Best regards,

Luis
Hallo Luis,

thanks for your reply!

I forgot to mention that I created a swap partition too and thanks for the explaination about the dimention of the swap partition.

Has anyone any more idea?
especially would I like to understand why I have problem with Grub when on my machine (old too - MSI KT3 Ultra2) I didn't even have to bother with the partitons and I let Ubuntu do all the hard work.

---

### Post by Ubidia on 2009-12-19
If I interpreted correctly what is written here: [http://ubuntuforums.org/showthread.php?t=1359083](http://ubuntuforums.org/showthread.php?t=1359083) Ubuntu 9.04 and 9.10 have different Grub version. 

Could be that the issue?

---

### Post by lmarmisa on 2009-12-19
Yes, Ubuntu 9.10 includes the Grub2 version.

---

### Post by Ubidia on 2009-12-19
I've been looking at the info page on GRUB2 [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
but I'm not able to understand if that could have an influence on the installation on a old machine or not.

Has got anyone any clue?

---

### Post by Ubidia on 2009-12-19
Here the situation tided up for easy read:

unable to install Karmic on a Asus P4B Motherboard with a Maxtor 160GB brand new HD.

Parallel install and simple install hang at "GRUB_".

Tried creating partitioning manually before installation since I read that old Mobos can have some problem when the /boot exceed the 1024 cylinders.

The other created partitions were /, /home, swap, fat32.

All to no avail.

Has anyone got any other clue on where the problem could be?
and especially the solution....:P


Thanks!!!!!

---

