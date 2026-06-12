---
title: "Reinstall GRUB from scratch? - I deleted the contents of /boot/grub"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by sparrowt on 2009-11-18
Hi, I accidentally deleted the contents of /boot/grub because i had mucked up my grub...
...I wanted to start from scratch and thought that installing grub again would put new stuff in this folder.
But it didn't!!

I managed to get a few files like my menu.lst but /boot/grub/stage1 is mucked up because when I try installing GRUB it says "file /boot/grub/stage1 not read correctly".

Any ideas where i can get a proper 'stage1' file from or how i can get my grub to work again without reinstalling?

I have tried booting the live CD and installing GRUB from there but it does the same, and there is no folder 'grub' in /boot on the live CD from which i could copy anything.

Basically i want to be able to setup GRUB from scratch like the installer does originally at the end of the install process, when installing from the live CD but without reinstalling.

Any help would be very much appreciated!! :)

---

### Post by wojox on 2009-11-18
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by darkod on 2009-11-18
The above link is actually for grub2. The OP is asking about legacy if I'm not mistaken.
You have instructions here, scroll down:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

PS. Actually if you have Karmic you should have grub2 unless you did an upgrade with keeping grub1. Anyway, now you have links for both versions.

---

