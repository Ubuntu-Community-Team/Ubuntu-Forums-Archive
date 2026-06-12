---
title: "Install Ubuntu on USB Device, boot into it using the HD Device without BIOS changes"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by Miki800 on 2009-12-08
first I'd like to state that the whole problem I have is with wanting not to change anything in the bios in order to boot ubuntu from another HD device.



alright, I think I can see the solution, I just don't quite know how to get it done.

I've installed Wubi into my external HD - a USB Device.

the image is there and all is good, one problem -
wubi did not update the NTLDR nor the already installed grub loader (wubildr*) with needed information on how to boot from the other HD.

the boot instructions I have there are relevant for the old wubi I've installed on that first internal HD.
when I try manually grub command like linux and initrd

I can only point to files located in any partition of my internal HD, like:

linux (hd0,1)/ ... or initrd (hd0,6)/ ...

there is nothing else, if I try "(hd1," and then press TAB nothing happens

it does not recognize that external USB HD.
which is very lame since I really want to be able to boot into that external HD without needing to reinstall that wubi into my first internal HD.


so I thought, maybe I can put the kernel/linux/initrd files in my first internal HD in a way that will allow grub to proceed with booting,

and then make it so that /etc/fstab will tell Ubuntu that root '/' is in that other secondary external USB HD.


but I'm really not sure how grub works as to what files exactly it needs to boot into a system that can process and finally work and understand /etc/fstab and then really boot the Ubuntu I know and love.


if you guys think of another, better or worse solution to my obvious problem I'd love to hear your thoughts since I think this isn't a trivial problem.


assistance would be greatly appreciated.

---

### Post by darkod on 2009-12-08
I have no experience with wubi so I'm not sure if you can do this. But if you used ubuntu install then even if the grub2 on the ext hdd is not directly bootable, you can connect to it from the grub2 on the int hdd (called chainloading).

PS. You should be able to do what you want playing around with the windows bootloader on your int hdd. It's used to load wubi from your int hdd anyway. It needs another entry for the ext hdd wubi. I just wouldn't know to give you the exact comands and the way to do it because I don't know that much about windows bootloader. It's much easier with grub. And you also need to specify your windows version because it makes a difference for the bootloader, how to do it.

---

### Post by darkod on 2009-12-08
If I understood correctly you have a functioning wubi on the int hdd too. If you copy the bootloader entry for that wubi, I can help you figure out how to create entry for the ext hdd wubi. It will be easy.

---

### Post by Miki800 on 2009-12-19
ok I talked to a friend of mine and he said that grub 2 should be able to identify my 2nd HD and it's wierd that it doesn't.

the reason should be because it is not grub 2, I have right now grub 1.97 beta, xp and unbootable wubi.

I guess I need to install, actually upgrade my grub to grub 2 using a live cd.

the question is how do I do this the fastest, safest and best way to assure me I will not damage the ntldr or existing working grubldr MDR datas...

---

### Post by Miki800 on 2009-12-25
bump

---

