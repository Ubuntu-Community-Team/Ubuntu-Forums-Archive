---
title: "Boot to OS not in root of CD-ROM! :/"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by deusdies on 2008-03-03
Hi!

I have a little bit weird problem...

Anyway, I want to install Windows Vista. However, when I burned the file downloaded from MS MarketPlace, I burned it to G:\WindowsVista\(vista files). So, now to root of my Vista disc is G:\WindowsVista

I've deleted the ISO file, and I can't download it again, since I have very slow internet

So, now when I select "Boot from CD-ROM" in BIOS, it won't work - simply because the bootmgr file has to be in the very root of the DVD.

So far, I've found some ways to make Grub boot to CD. The question is: how do I make grub to boot from specific file (folder) - in this case, how do I make Grub to boot to G:\WindowsVista\ instead of just to G:\ ?!?

Thanks!

---

### Post by dstew on 2008-03-04
It is possible in theory. You can give grub the root of the CD, like (hd3,0). Then, savedefault and makeactive as usual. The key is to give grub the correct block address of the CD's boot loader in the chainloader statement. I don't know how exactly to do that, but if you study on block addressing, maybe you can figure it out. See the [Gnu Grub Manual]("http://www.gnu.org/software/grub/manual/grub.html") for information on how grub uses block addressing.

---

