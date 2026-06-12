---
title: "Boot Loader's mainimage disppered in the list!"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by Abhihemu on 2011-08-31
Hii all :D

I am using Ubuntu 10.10 Maverick Meerkat , today i tried to change my plymouth theme, but i messed it up, now main boot kernel is disappeared and i see only Recovery mode kernel in the boot loader list and through which i am booting. But i don't know how the main boot kernel disappeared !!
Please help someone :(

How to restore my main boot kernel image in boot loader list?
Thanks in advance!

---

### Post by dino99 on 2011-08-31
very strange ;)

sudo grub-mkconfig
sudo update-grub

sudo apt-get install startmanager

then use it to set the boot OS order you want (if you have several OS installed)

---

### Post by Abhihemu on 2011-09-02
Sorry i was unable to find this my own thread lol :D
I read many threads on this forum and i found i had damaged my boot kernel with plymouth manager, don't know how it happened,I tried to restore my boot kernel but i am newbie and so i didn't get it, however it was a freshly installed ubuntu, so i did a reinstall and left the plymouth theme as it is.
Thanks for the reply :D

---

