---
title: "Brand new to ubuntu, need some help"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by thecashier on 2008-07-09
Can i install Ubuntu on my PC from the cd-rom drive, without creating a partition? i tried making one to have XP on one half, and linux on the other but when i started the partition process i left the room and came back later (30 mins or so) and nothing was done. And/or is it possible to partition a drive while in 
"use", the cds booting but using the c drive. Any help is GREATLY appreciated. Thanks

---

### Post by Het Irv on 2008-07-09
You can use Wubi.  Wubi installs Ubuntu inside of Windows.  Boot to XP and stick in your Ubuntu Disk.  When the prompt comes up select "Install inside of Windows" and follow the prompts.

---

### Post by keiffee30 on 2008-07-09
Well you could have a look in the Doc's that are on line. 

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

start here and see what you come up with. If no joy then please do come back
good luck

---

### Post by Pumalite on 2008-07-09
Get Gparted Live CD and 'shrink' XP:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
Right click on XP, choose 'resize' from menu. In the new space, make 3 'New' partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home
Remove Gparted Boot Ubuntu, install; go Manual and use already prepared partitions.
This way you have more control and you don't wipe off XP by mistake.

---

