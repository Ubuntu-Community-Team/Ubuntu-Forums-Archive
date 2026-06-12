---
title: "Installing Ubuntu 8.04 on Flash drive"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Loolykinns on 2008-04-26
I've been trying to install Ubuntu 8.04 on my flash drive.

My laptop is Toshiba L20-149 and it enables USB booting.
My flash drive is Kingston DataTraveler 4GB

The installation is done and everything, but i cant boot. I installed grub on sdb (which is my flash drive) and the system boots from it before the HDD (my hard drive)... and whenever i choose (ubuntu 8.04) grub gives me error 17...

Here's the important stuff in my GRUB menu.lst:
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c8db8673-d804-4ce6-8761-59910b022326 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c8db8673-d804-4ce6-8761-59910b022326 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin



Hope you could help me with that...

---

### Post by Lori700698 on 2008-04-26
quick fix would be at grub hit e, then e again and change h1,0 to h0,0 then enter then b.  this will boot it and you can change it perm. but I need to look up those directions.

---

### Post by Pumalite on 2008-04-26
Backup your file first. Then:
gksudo gedit menu.lst

---

### Post by Loolykinns on 2008-04-26
I changed the hd1 to hd0 and i got to the login screen... it just hangs when i log in... (i doubt my resources... after all my laptop isn't that good)

is there anythin' i could do to make it actually gets to the desktop and all? or should i just install xubuntu?

---

### Post by Pumalite on 2008-04-26
If you have 256 MB of RAM or less, Xubuntu is the way to go (Xubuntu Alternate CD).

---

### Post by Loolykinns on 2008-04-26
My RAM is 1GB and my HDD is 40GB... I downloaded Xubuntu and i'll give it a shot tomorrow and fill you with updates

---

### Post by Lori700698 on 2008-04-26
good luck with that, I never got past the the dreaded hang on tan/brown screen!  I went back to 7.10!  if you figure it out shoot me a message!

---

### Post by Loolykinns on 2008-04-30
> **Lori700698 said:**
> good luck with that, I never got past the the dreaded hang on tan/brown screen!  I went back to 7.10!  if you figure it out shoot me a message!

Guess what? It worked!!

I installed Xubuntu and worked like a charm... I'm sure there's something wrong in my Ubuntu and CD Drive... but Xubuntu worked well

Hope telling you that Xubuntu worked help you decide what to do

---

