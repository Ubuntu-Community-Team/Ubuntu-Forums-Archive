---
title: "Problem uninstalling Ubuntu"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by piloteer81 on 2008-09-29
Hi all. I recently got an Elonex Webbook that came with Ubuntu. I planned to install Windows XP on it and thought all I had to do was use windows to delete the partions and format the drive - how wrong was I! Grub came up with an error message as I'm guessing the OS is gone but I've been unable to get rid of it or install windows. 

I used a low level format program and also attempted to re-rite the MBR. Grub no longer appears during POST but the drive still won't appear during Windows setup and I'm also unable to access the drive via a bootable floppy/usb stick - c: simply doesn't exist. 

Anybody any ideas how I can wipe the drive clean of Ubuntu? Any help much appreciated!:)

---

### Post by Pumalite on 2008-09-29
Use Gparted Live CD. Delete everything in your drive. Format ntfs. Install Windows.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn iso to disk and boot from it

---

### Post by piloteer81 on 2008-09-29
Good little program but unfortunately it hasn't solved te issue! I deleted all partitions then formatted NTFS but windows still refused to identify the drive. I went back and created a new partition table and redid the above but this had no effect either. Did I miss something here? There were quite a few options in the program.

---

### Post by Pumalite on 2008-09-29
You might need to dban the drive before using Gparted Live CD:
[http://www.dban.org/](http://www.dban.org/)
OTOH; if you can boot a Live CD; post:
lshw

---

### Post by cariboo on 2008-09-30
Does your webbook have a sata hdd, if so you have to have windows XP sp2 or newer in order for the drive to  be detected.

Jim

---

### Post by piloteer81 on 2008-09-30
It does indeed have a SATA drive but I'm using an XP SP2 CD to boot from, that should be ok shouldn't it? I borrowed another 2.5" SATA drive of the same capacity from another laptop and it's detected fine but I can't get the drive that previously had Ubuntu on it to be recognised by several laptops during Windows setup, although they are shown in the BIOS.

---

### Post by bigken on 2008-09-30
you have press f6 during the install of windows and install the sata drivers or you might be able to change your sata settings in the bios


or take a look here 

[http://lifehacker.com/386526/slipstream-service-pack-3-into-your-windows-xp-installation-cd](http://lifehacker.com/386526/slipstream-service-pack-3-into-your-windows-xp-installation-cd)

---

