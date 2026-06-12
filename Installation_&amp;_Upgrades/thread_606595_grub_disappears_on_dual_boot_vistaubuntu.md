---
title: "grub disappears on dual boot vista/ubuntu"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by aerris on 2007-11-08
Hey Everyone,
I had a working dual boot vista/ubuntu machine running perfectly off a partioned 200gb SATA HDD.  I wanted it faster though so upgraded my machine with motherboard, processor, ram... well... everything ;) and now after reinstalling vista and ubuntu the exact same way as before the grub bootmanager screen only flashes up for about 0.0005 seconds and boots into Vista straight away.

Last install i edited the /boot/grub/menu.lst in ubuntu to change the timeout, default os and menu entries but im not really sure whats going on this time?  

There is another 80gb IDE  hdd running as primary slave but this is just for documents in windows.  The ubuntu primary and swap partitions are on the 200 gb sata.

any ideas?

thanks!

---

### Post by bulldog on 2007-11-08
Wild guess,but did you tell grub to install on hd1 or did you let it install on the default place?
Default means hd0 and in most cases the IDE hdd is hd0 not the Sata.
Try to boot from the IDE and see what you get.

---

### Post by aerris on 2007-11-08
bingo bango. job done thanks.

---

