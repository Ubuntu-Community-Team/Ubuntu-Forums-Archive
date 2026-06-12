---
title: "ssd and fresh install/ upgrade"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by 1rancid11 on 2012-03-25
Recently I added a sata 2 ssd to my ideapad. Dont think there is any reason to use sata 3 being it was fast w/7200 rpm hdd. To the point now. The first ssd i put in it im not sure how but I tanked it . I think trying to reload version 10.10 too many times . The 2nd one worked out. Now I wanna upgrade from 10.10 to 11.10. I want it to be a fresh install. Well cant seem to find any info on fresh install. Dont wanna make the same mistake. If the reloading too many times was the mistake.Thanks, Jay
Specs idea pad 
8 gigs ram
sata 2 ocz 120 gigs 
i7 processor
Let me know if u need more spec info.](*,)

---

### Post by oldfred on 2012-03-25
With an i7 processor, your motherboard is probably UEFI/BIOS. Many are having difficulty with UEFI but eventually get it to work. I only have BIOS but used gpt as recommended by the Arch site for my SSD with a bios_grub partition and it works just like any install.

Have you backed up all of your /home or have it on a separate rotating drive? Did you add a lot of apps and want to make a list to reload? Or is it just a clean new install?

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)


Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.


[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

