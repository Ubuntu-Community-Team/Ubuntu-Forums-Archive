---
title: "how do i remove Ubuntu?"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by naeemzahid on 2010-01-22
hi all.

i have an acer aspire one. it came with windows xp. It does not have any optical drive.
it was kinda slow so i installed ubuntu hoping it would be faster, but ubuntu is ten steps back for my acer... the GMA 500 driver is so baaad....

but anyways...

i decided to uninstall Ubuntu, but i dont know how...

I have read alot of threads about using the windows cd, but i dont have a windows cd, i dont even have a cd drive. i have an Acer-recovery program in windows, but that requires a reboot, and when i reboot i only come back to grub.... not to the Acer-recovery 

i have dual boot, and cant delete any partition either... and i dont know how i should remove grub... i cant get in into recovery console so i cant run fixmbr/fixboot... 

i feel kinda stuck... 
is there anything i can do?

---

### Post by C.S.Cameron on 2010-01-22
If you can get a hold of a 2GB or better flash drive you can use System/Administration/USB Startup Disk Creator to make a Bootable Pendrive with Ubuntu on it. You should make it persistent so you can download ms-sys to it.
You can use gparted to reformat the Ubuntu partitions and ms-sys to fix the Windows MBR.

---

### Post by kansasnoob on 2010-01-22
> **naeemzahid said:**
> hi all.

i have an acer aspire one. it came with windows xp. It does not have any optical drive.
it was kinda slow so i installed ubuntu hoping it would be faster, but ubuntu is ten steps back for my acer... the GMA 500 driver is so baaad....

but anyways...

i decided to uninstall Ubuntu, but i dont know how...

I have read alot of threads about using the windows cd, but i dont have a windows cd, i dont even have a cd drive. i have an Acer-recovery program in windows, but that requires a reboot, and when i reboot i only come back to grub.... not to the Acer-recovery 

i have dual boot, and cant delete any partition either... and i dont know how i should remove grub... i cant get in into recovery console so i cant run fixmbr/fixboot... 

i feel kinda stuck... 
is there anything i can do?

Can you still boot both Windows and Ubuntu?

---

### Post by naeemzahid on 2010-01-23
yes i can boot into both windows and ubuntu.

i could delete the partition.... but how would i boot into windows after that, i am stuck with grub....

---

### Post by darkod on 2010-01-23
This is what kansasnoob usually recommends but I'll jump in. :)

[COLOR=Red]IF[/COLOR] you have a single hard disk, first boot your ubuntu and in terminal do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

That will remove grub from the MBR and install windows MBR on it. In other words, when you reboot it should go straight into windows.

Then from windows just delete the ubuntu partition and format that space as ntfs partition so you can use it with windows. Because you have XP I'm not sure if it's worth trying to expand your XP partition instead of creating a new one. You can corrupt it.
You could just create the new ntfs partition and use it like that.

---

