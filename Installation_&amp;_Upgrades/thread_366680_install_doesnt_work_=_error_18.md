---
title: "install doesnt work = error 18"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by runebuntu on 2007-02-21
Dear all,
just new to ubuntu.
have tried installing the ubuntu 6.06 release today on my win xp laptop > everything worked fine during the installation, i created a separate partition for the system, installed the files and rebooted as told. 
at first boot the system halts and gives me an **error message no. 18**.
now, cant seem to find the proper documentation for error messages and im kind of stuck, since i cant get hold of my installed windows xp on the primary partition either. 
is this a known problem - and does any of you kind persons know how i might proceed from here?
with kind regards,
rune

---

### Post by mikewhatever on 2007-02-21
Does this help?
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

---

### Post by runebuntu on 2007-02-21
well, you directed me in a direction that might be right, since the I in the installation might have chosen an area of the disk for the new partition, that the bios couldn't find... 

i tried reinstalling into the preexisting main partitition instead - but when running the proces over, ubuntu somhow managed to **destroy **the socalled 'predesktop area' of my IBM laptop - meaning that i can't acces the bios setup! so now i'm really in a tight spot! no working OS and not able to direct my laptop to boot from the cd (it only has an external cd-rom drive)...

if anybody has any good suggestion as to what I might do - I'm all ears! this really gets me worried - i cant seem to find any solution to this...
if not, my brief encounter with ubuntu/linux ends really, really bad...

---

### Post by logos34 on 2007-02-21
wow, never heard of that happening...if all else fails you can try to reset the bios with the cmos jumper on the board, but with a laptop I imagine you'll have to take it apart to get to get to it.

---

### Post by runebuntu on 2007-02-22
by help of the ibm-support i found a way to enter the bios without going through the ibm predesktop area, so i was able to make it boot from the cd, and as i write these lines i'm on a new installation of ubuntu that so far seems to work.
what 'solved' my problem with the error 18 was to let the installation program erase all partititions and reformat my whole hd (fortunately i had backup) - which of course means that i'll have to go over installing windows again as i need it for some applications - and that i'm uncertain as to whether the same problem will reoccur... we'll se, but thanks for the comments.

---

### Post by mikewhatever on 2007-02-22
I am glad you've got it solved. Be aware, that reinstalling Windows after installing Ubuntu overwrites the MBR, so you'll then have to restore GRUB. [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

