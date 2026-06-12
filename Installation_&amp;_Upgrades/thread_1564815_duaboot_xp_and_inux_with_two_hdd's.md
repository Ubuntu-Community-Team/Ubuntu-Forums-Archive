---
title: "duaboot xp and inux with two hdd's"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by dimi_tris on 2010-08-31
i have read many tutorials but i cat find that what i need.
i have a hdd with xp. 
have a new hdd where i want to install ubuntu 10.04.
one  way is to disconnect xp and then install mint, but there is not going  to be a boot option witch OS can &#953; choose. and i must use then the f12  to boot from deferent devises. 
is there a solution?

---

### Post by lechien73 on 2010-08-31
There are several options. I'm presuming that XP is the first hard disk and Ubuntu the second, so I'm going to call the XP disk sda, and the Ubuntu disk sdb.

Firstly, you could leave the XP disk connected and install Ubuntu to sdb. During the installation process, choose to install Grub (the bootloader) to the MBR of sda. You will then be able to choose between XP and Ubuntu when you start up.

Secondly, you could decide that you don't want to modify the MBR of your Windows disk - just in case. You can then disconnect the XP disk and install Ubuntu and Grub to sdb. After installation, you can follow the instructions here: [http://uri.tl/t](http://uri.tl/t) to add Ubuntu to XP's boot menu.

Finally, you can continue as you already suggested. Press F12 (or whatever it is on your system) to boot from whichever disk you want.

---

### Post by dimi_tris on 2010-08-31
thank you very much for your answer.
i will try it.

---

### Post by sikander3786 on 2010-08-31
> **lechien73 said:**
> During the installation process, choose to install Grub (the bootloader) to the MBR of sda.

+1 It will be better to install Grub to the MBR of Windows HDD. And if windows HDD is sda, select Advanced at the last step of Ubuntu installer (think it is the 7th step, just after personal information page and before the start of installation) and select sda from there.

Regards.

---

### Post by Mark Phelps on 2010-08-31
I would differ in saying it would be better to disconnect the XP drive and install Ubuntu and GRUB to the other drive.  Then, reconnect the XP drive, boot from the Ubuntu drive, open a terminal and enter "sudo update-grub".

This approach has the advantage that you do NOT mess with the MBR on the XP drive, thus, you can continue to boot that drive on its own.

---

### Post by sikander3786 on 2010-08-31
> **Mark Phelps said:**
> I would differ in saying it would be better to disconnect the XP drive and install Ubuntu and GRUB to the other drive.  Then, reconnect the XP drive, boot from the Ubuntu drive, open a terminal and enter "sudo update-grub".

This approach has the advantage that you do NOT mess with the MBR on the XP drive, thus, you can continue to boot that drive on its own.

Not bad either. Then he just need to change his Bios Settings to boot from the second HDD.

---

### Post by lechien73 on 2010-08-31
> **sikander3786 said:**
> Not bad either. Then he just need to change his Bios Settings to boot from the second HDD.

True, but the OP's question was how to avoid that scenario :)

For users who don't want to modify the MBR of their Windows disk (e.g. sda), I think that installing Grub to the MBR of sdb and then modifying the Windows boot menu to choose between either Windows or Ubuntu is the safest option.

---

