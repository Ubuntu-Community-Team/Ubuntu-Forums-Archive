---
title: "Dual boot, lot's of hard drives, Error 21 (Grub)"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by Standy on 2008-05-14
Hi! i am pretty new to ubuntu.. i've installed it on my laptop and there it works alright... I want to install Ubuntu onto my desktop compute, but dual boot with windows xp. 

So.. i install Windows xp, with it's partition first on the hard drive, and leaves about 15 gb free space after this for ubuntu. I start live cd, everything works perfectly fine, i choose install from desktop, get to the partition part, and marks the "take the free space"... now.. after this if i press advanced i can choose where to install the Boot Loader (Grub). i've tried to let it be standard (hda0) if i am not totally mistaken, and i've tried to boot from the windows partition, and ive tried from the partition i am installing ubuntu too.. but when i restart i get Disk Boot Failure, Error 21; (in grub), or win xp just boots up... 

On this computer there is two raid sets, there are also two hard drives connected to ide... i want to install to one of these ide hard drives... but i think (hda0) is one of the raid hard drives... does this make any sense?

---

### Post by nicedude on 2008-05-14
While I can't tell with the supplied info what you have done, I would suggest that in future you just either physically unplug or in Bios unenable all the disks you don't want to install a OS on and then with just one IDE drive hooked up you can install windows and then Ubuntu. Then you just plug up or enable all your other disks. For your info I will break down the hd?? system below

hda0  

hd means hard drive

"a" means disk 1  - b would mean disk 2 c=3 d=4 and so on

"0" means partition 1 - 1 would be partition 2 - 2=3 3=4 and so on

So hda2 would be hard drive 1 partition 3 & hdb1 would be hard drive 2 partition 2 - hope you follow :-)

sda0 means same thing but sd part is supposed to mean SCSI disk but isn't always correct and sometimes it still could be IDE not SCSI

you should also have some others disks such as hdb hdc or sda & sdb 

Basically grub installs to a boot partition and then also installs the rest of its settings to your partition where you installed Ubuntu in the directory /boot/grub/ settings you need to look at are in the file named menu.lst which has all the settings for grub to function.

If you figure out what you put on what drive but still can't solve this you can PM me and I will try to figure it out for you but if you learn about grub menu.lst you should be able to solve this yourself - you will just need to use the live disk to boot up and access everything.

Hope you figure it out its worth the learning curve to be empowered.

---

### Post by Standy on 2008-05-14
Thank you very much... ubuntu is now up'n running.. four five years ago i always pulled them out before i started formatting... getting lazy over the years... :) tnx again=)

---

