---
title: "Vista+Ubuntu DualBoot on one Laptop HDD"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by Clarke on 2008-01-01
Hi all. I've bought the new Samsung Q45 laptop with preinstalled Windows Vista. I realy like Linux, I use it as the only OS on my Desktop, but because of some reasons, I will need Vista on my laptop at least sometimes, so the only way out for me is dual boot.
 
I have already read so many guides about how to install Ubuntu, having preinstalled Vista,i but there are so many people, complaining that the Grub bootloader corrupt the whole system, making booting into Vista impossible. 

So is there a 100% working method how to setup dual boot system, having Vista allready installed? Because I need to be 100% sure that I'll be able to boot both Ubuntu and Vista before beginning installation. 

Maybe some people who installed dual boot on Samsung notebooks will share their experience here- it would be cool. 

On my laptop I have a single 160gb Sata HDD.

Thanks.

---

### Post by logos34 on 2008-01-01
> **Clarke said:**
> So is there a 100% working method how to setup dual boot system, having Vista allready installed? Because I need to be 100% sure that I'll be able to boot both Ubuntu and Vista before beginning installation. .

couple of tips: make sure to resize/shrink Vista partition using the latter's own disk management tool--don't let the ubuntu installer/gparted do it.  And don't install grub to mbr--use vista boot manager to boot ubuntu.  Grub usually will work, but occassionally won't, so if failure is not an option make sure to install grub to the bootsector of the linux root partition rather than mbr.  Then use EasyBCD to add ubuntu entry to vista bootloader.  

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
[http://neosmart.net/wiki/display/EBCD/linux](http://neosmart.net/wiki/display/EBCD/linux)

Happeee New Yearrrrr!!!

---

### Post by Clarke on 2008-01-01
Thanks, usefull guides. Could u plz say on what step of instalation can I specify the location of Grub loader? During the manual partitioning?

---

### Post by confused57 on 2008-01-01
> **Clarke said:**
> Thanks, usefull guides. Could u plz say on what step of instalation can I specify the location of Grub loader? During the manual partitioning?

Since logos34 isn't logged onto the forum....there should be an "Advanced" button that you can click, then you can type in your Ubuntu partition, in place of the default (hd0).

During the partitioning & install of Ubuntu, make a note of how your root partition is designated, for example /dev/sda2, /dev/sda3, etc.   Type this designation(/dev/sda2 or whatever) in place of (hd0) after you click the "Advanced" button.  I believe it's on step 7 of the install(lower right corner).

---

