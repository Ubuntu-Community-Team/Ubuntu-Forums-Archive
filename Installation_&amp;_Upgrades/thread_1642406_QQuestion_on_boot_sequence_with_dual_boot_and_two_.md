---
title: "QQuestion on boot sequence with dual boot and two drives"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by Buffalo_Guy on 2010-12-10
I recently sent up another computer as follows:  Two sata drives.  Windows 7 was installed on the first drive (sda) and booted successfully.  This drive was disconnected ( I have had some installs where Unbuntu wipes out the existing C drive eventhough I am installing to D) and Ubuntu was installed to the second drive (sdb). At one point I had to rebuild the grup on the Ubuntu drive and was careful to make it installed on the Ubuntu drive. To my surprise when the PC booted up I saw the Grub menu with a menu entry for Windows.   The Windows drive was always the primary drive before the Ubuntu install.  I was planning on the Windows drive being the boot drive and using a boot manager to determine where to go from there.  If I utilize the BIOS boot option (F12) I can boot each drive  individually.  I cannot in BIOS set a particular drive to boot - just a hard drive.  Everything is working  I am just curious why the primary drive does not boot first.  IN BIOS the Windows drive is a primary SATA with a lower number that the Ubuntu drive which is listed as a secondary drive.

---

### Post by oldfred on 2010-12-10
If your BIOS/motherboard supports SATA you have a choice on which drive to boot. Sometimes it is part of the selection of boot device - HD, floppy, CD etc and you have a submenu under HD. Other times it is a totally separate BIOS menu entry on which HD to boot.

Only old BIOS with only IDE, would boot just the primary master which you set with jumpers on HD or by cable select location on cable. SATA has no selection, so it is in BIOS.

---

### Post by Buffalo_Guy on 2010-12-10
Thanks oldfred I will check that out.  I didn't think there was a way to set it in BIOS.  THis is relatively new motherboard.

---

### Post by Buffalo_Guy on 2010-12-10
Oldfred:

I have been at t his game for a long time.  I feel like an idiot.  You are indeed correct.  I have found the option in bios that alters the boot order for the hard drives.  When I disabled the C drive to install Ubuntu , by default the D drive moved up in order.  Thank you for pointing this out.  I have to go hide now.

Steve

---

### Post by oldfred on 2010-12-10
Glad you found it.

It took me a long time to figure out how to boot my flash drive. My MB has many USB boot options including USB-HDD. I created a bootable flash for installs instead of writing CDs all the time. But it would not work. I tried every USB option. I tried flash drive on my portable and it worked. I gave up. Later I had flash plugged in for some reason but was rebooting and changing hard drives. Well one more hard drive appeared as my flash drive. No where in my manual does it say that. Who knew. We find out things all the time. Even oldfreds can learn new tricks.:)

---

