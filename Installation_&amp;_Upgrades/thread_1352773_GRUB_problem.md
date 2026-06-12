---
title: "GRUB problem"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by OO_Donut on 2009-12-12
Ok, here is my situation. (Also I dont know where this would fit in,m I assumed install because it happened after installing ubuntu.)

I have 3 HDDs in my computer, a 20 gb for ubuntu, an 80 GB for windows XP and a 200GB for windows 7.
[EDIT: If it matters the 80 and 20 GB are IDE and the 200GB is sata] When I loaded ubuntu onto the 20 gb HDD everything seemed to go good. but when I wanted to get back to windows it would load the GRUB. This was my first ubuntu distro so I am completely new to it, and I dont mind it. Other than when i unplug my 20 gb hdd and start my computer. It wont load because of something to do with the GRUB.  even tho the bios says that the windows 7 partition is the boot partition it still tries loads the GRUB. I cannot get to windows unless i plug the drive back in. Once again still not a big problem untill my 20 gb dies, it is very old, not sure how much life is in it.

Did linux write over my MBR?

How do I fix it so the grub doesnt load? I dont even need windows to recognize ubuntu or windows XP, I am completely fine with going into the bios and changing the boot order if I want to switch OS.

As i said I am kinda new to ubuntu so any advise would need to be fully explained.

Please help! Thanks,
Nathan

---

### Post by pedja_portugalac on 2009-12-12
> **OO_Donut said:**
> Ok, here is my situation. (Also I dont know where this would fit in,m I assumed install because it happened after installing ubuntu.)

I have 3 HDDs in my computer, a 20 gb for ubuntu, an 80 GB for windows XP and a 200GB for windows 7.
[EDIT: If it matters the 80 and 20 GB are IDE and the 200GB is sata] When I loaded ubuntu onto the 20 gb HDD everything seemed to go good. but when I wanted to get back to windows it would load the GRUB. This was my first ubuntu distro so I am completely new to it, and I dont mind it. Other than when i unplug my 20 gb hdd and start my computer. It wont load because of something to do with the GRUB.  even tho the bios says that the windows 7 partition is the boot partition it still tries loads the GRUB. I cannot get to windows unless i plug the drive back in. Once again still not a big problem untill my 20 gb dies, it is very old, not sure how much life is in it.

Did linux write over my MBR?

How do I fix it so the grub doesnt load? I dont even need windows to recognize ubuntu or windows XP, I am completely fine with going into the bios and changing the boot order if I want to switch OS.

As i said I am kinda new to ubuntu so any advise would need to be fully explained.

Please help! Thanks,
Nathan

GRUB has overwriten MBR on your first disk. It's not big problem. You can insert your windows 7 disk and repair that but then you'll have to reinstall GRUB on 20GB disk if you want to use Ubuntu. Leaving all disks hooked, all the time, is not problem. You can chose each time which system you want to boot. And check this thread for more [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by OO_Donut on 2009-12-12
Thanks for the quick response.

But it didnt work, I first reinstalled the boot loader for 9.10 then I tried the fix mbr and no dice. It still comes up with the GRUB. Im not really sure what to do. I am going to try it again. hopefully it will work. =] keeping my hopes up high. 

I really dont know why it didnt work after the fixmbr. It should have erased the bootloader and put on the windows 7 boot loader. so it all should have worked fine =[

Ill keep ya posted. 

Any other Ideas?

Nathan

---

### Post by OO_Donut on 2009-12-12
update:

When I restarted with the windows 7 install disc in again, it said that it found a problem when I went into the repair console. a window came up saying there was a problem with the windows boot something or other, so i clicked fix and restart

it restarted and booted into windows xp. I dont know why. The boot order is "1. Windows 7 Sata, 2.  Storage HDD sata, 3. 80 gb windows XP master IDE, then 4. 20 gb ubuntu Slave IDE. 

How would it boot to windows XP if windows 7 is above it? Does IDE have anything to do with the boot order?

Ok, I tried unplugging bothe IDE HDDs then upon boot GRUB had the "no such disk error" so my system is behaving the same as it did before I tried anything

Im just confused,
Enough for one night, I will try again tomorrow.

Final thoughts for tonight: Boo You GRUB and being a pirate taking over my windows 7 MBR.

Is there an option to not take over the MBR when installing ubuntu?

---

### Post by darkod on 2009-12-12
> **OO_Donut said:**
> update:

When I restarted with the windows 7 install disc in again, it said that it found a problem when I went into the repair console. a window came up saying there was a problem with the windows boot something or other, so i clicked fix and restart

it restarted and booted into windows xp. I dont know why. The boot order is "1. Windows 7 Sata, 2.  Storage HDD sata, 3. 80 gb windows XP master IDE, then 4. 20 gb ubuntu Slave IDE. 

How would it boot to windows XP if windows 7 is above it? Does IDE have anything to do with the boot order?

Ok, I tried unplugging bothe IDE HDDs then upon boot GRUB had the "no such disk error" so my system is behaving the same as it did before I tried anything

Im just confused,
Enough for one night, I will try again tomorrow.

Final thoughts for tonight: Boo You GRUB and being a pirate taking over my windows 7 MBR.

Is there an option to not take over the MBR when installing ubuntu?

All you had to do is make the ubuntu disk first in boot order before installing. And with multiple drives ALWAYS check where grub will be installed, you can do this on the last screen before clicking Install, click on Advanced button and it will show you where it's planning to install grub.
Windows bootloader also installs itself on the disk set up as first in boot order.
If you make your win7 disk first in boot order and then you restore the bootloader with the win7 dvd, it should restore it on the MBR of the disk.
It's not a problem to reinstall grub2 to any disk you want.

---

