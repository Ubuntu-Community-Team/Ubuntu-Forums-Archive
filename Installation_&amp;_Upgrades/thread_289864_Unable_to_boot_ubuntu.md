---
title: "Unable to boot ubuntu"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by narayanb on 2006-10-31
i was using ubuntu 6.06, knoppix 5.01 and XP, of which Ubuntu is the latest installation and windows the oldest.
I was having two harddisks, one SATA and one ATA. all the OS were installed in SATA.
Recently i removed the ATA drive, which made my system freeze with no boot loader(it seems my GRUB was in ATA). So i booted from the Ubuntu live CD and then restored GRUB with the following statements:

[B]#sudo grub
grub>find /boot/grub/menu.lst
(hd0,2)
(hd0,7)
grub>root (hd0,7)
grub>setup (hd0)
grub>quit[/B]

(hd0,7) has my Ubuntu.
After this i rebooted my system..and the GRUB menu was restored to normal. Then i tried my Ubuntu option on the list, but it could not boot..
so i edited the option
it was given (hd0,6)..i changed it to (hd0,7) and tried to boot then it booted but when trying to mount the root system, it failed and the Busy box shell came.

then i tried Knoppix option..here also it failed first.. then i edited it and changed it from (hd0,3) to (hd0,2) and booted. Then  it started Knoppix..but again unable to mount root system and the  shell came...  

but when i try windows option, it works.

Please help me i hav tons of data in my linux partitions. I know the problem is something silly and could be fixed.

Sorry for the long post.

---

### Post by narayanb on 2006-11-01
after two days of experimentation i fixed it..
wat i did was i booted up ubuntu thru live CD.
now i mounted the older Ubuntu partition ( which was now sda8, when i had AtA it was sda7).
Then i opened  /boot/grub/ folder...in sda8 and edited the menu.lst file.
it contains lines similar to this.
[B]title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot
[/B]

in that the kernel line points to sda7 that caused the busybox at boot
so i changed it to sda8...also root was changed to (hd0,7)

repeated this for other entries.
Bingo!

---

