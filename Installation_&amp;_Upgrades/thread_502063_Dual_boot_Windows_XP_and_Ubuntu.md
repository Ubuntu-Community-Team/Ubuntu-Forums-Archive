---
title: "Dual boot Windows XP and Ubuntu"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by Andre M on 2007-07-16
Hi
I want to start using Ubuntu on my laptop but I would like to have the option to go back to XP if there is program I want to use that doesn't work on Ubuntu or something similar.
My laptop has 2 hard drives and I've deleted everything on the second one so I can put Ubuntu on. I searched for instructions and lots of them say you have to unplug the Windows hard drive which is impossible for me.
If someone could give me clear instructions that would be great.
Thanks in advance :)

---

### Post by constrictor on 2007-07-16
If you try and install it with the LiveCD you should be presented with the option to install Ubuntu on your second hard drive when you get to the partition manager. If you take note of what number your hard disk is for example hda1 or something similar. After the installation your bootloader should detect windows XP and make an entry for the windows XP option when you are booting up.

I effect you do not have to remove the other hard disk the partition manager should be able to detect the presence of other hard disks and give you the option to install Ubuntu to either of them

---

### Post by Andre M on 2007-07-16
I installed it and on step 4 i chose 'use entire disk' i selected the second but now when i try and boot up my pc it says:
```
GRUB Loading stage 1.5.

GRUB loading, please wait...
Error 21
```
so now im unable to boot into either xp or ubuntu :(
i used the livecd to boot and i found my 2nd hard drive (it cant find my xp hard drive for some reason) at /media/disk. I did some searching and it says you have to edit menu.lst to fix GRUB but i am unable to edit /media/disk/boot/grub/menu.lst using the live cd :S
please help :(
thanks

---

### Post by confused57 on 2007-07-16
> **Andre M said:**
> I installed it and on step 4 i chose 'use entire disk' i selected the second but now when i try and boot up my pc it says:
```
GRUB Loading stage 1.5.

GRUB loading, please wait...
Error 21
```
so now im unable to boot into either xp or ubuntu :(
i used the livecd to boot and i found my 2nd hard drive (it cant find my xp hard drive for some reason) at /media/disk. I did some searching and it says you have to edit menu.lst to fix GRUB but i am unable to edit /media/disk/boot/grub/menu.lst using the live cd :S
please help :(
thanks

If you have access to another computer, you might want to download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

First, you could try booting into your bios setup and check your slave drive controller & make sure it's set to "auto"(your bios may need to be set to "on" or "enabled"?).

---

