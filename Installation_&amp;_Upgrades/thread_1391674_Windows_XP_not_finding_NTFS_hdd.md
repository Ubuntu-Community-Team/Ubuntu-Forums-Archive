---
title: "Windows XP not finding NTFS hdd"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by samuraitor on 2010-01-27
hey guys,

I have reformatted my 320 GB and creating a separate NTFS partition for Windows XP.

When I boot with the CD and proceed to the setup window, Windows does not recognise any HDD on my laptop, hence cannot install it.

I have attached two  screen shoots of my partitions. Can anyone tell why XP is not finding the NTFS partition?

---

### Post by darkod on 2010-01-27
Because XP by default does not have SATA drivers to recognize SATA disks. Welcome to windows. :)
You might have received a floppy with the sata drivers with the board/computer. Or just create one for your board model, they should have the drivers on manufacturer website. After booting the XP installer you have to press F6 and use the floppy with the drivers.
If you don't have a floppy drive I'm not sure you can do it with drivers on cd because the XP install cd is in the drive.

Another option is embedding the sata drivers for your board into the XP install image. Using program called nlite for example. Google for it and how to use it. But you still need to find the drivers for your board.

---

### Post by Leppie on 2010-01-27
that's for buying the retail version... ](*,)

---

