---
title: "&quot;error: the symbol 'grub_puts_' not found&quot; message after Lucid upgrade from Karmic"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by avada on 2010-04-21
After upgrading to 10.04 Lucid Lynx grub loading failed the message in the title. Tried booting from rescue mode, but got the same error. Tried installing grub from the Karmic disc I still have got "Could not find device for /boot: Not found or not a block device."
So I'm out of ideas at the moment.

While upgrading I was asked to choose the partition wich I did, I chose the ubuntu partition as always (second from the three). I was also asked if I wanted to keep the configuration wich I kept.

How can I fix this?

---

### Post by MrWylbur on 2010-05-05
This is exactly what happened to me today,  Installed 10.04, but the grub configuration is throwing an error.  

Anyone?

---

### Post by avada on 2010-05-07
> **MrWylbur said:**
> This is exactly what happened to me today,  Installed 10.04, but the grub configuration is throwing an error.  

Anyone?

Unfortunately I couldn't fix this even after I found [super grub disk]("http://www.supergrubdisk.org/") and was able to boot the OS's on the HDD. I tried reinstalling grub but I always got a warning that grub is installed to a partition instead of mbr and that is not recomended, and I still couldn't boot.
So I just reinstalled ubuntu from disk. Its just awesome how smoothly updates go in the ubuntu world.

---

### Post by oldfred on 2010-05-07
Often reinstalling grub to the MBR fixes this. If you were getting the partition message you selected sda1 - partition (PBR) not sda -  drive's MBR. You almost alway want to install grub to the drive and computers only boot from the MBR of the drive selected as boot in BIOS.

---

### Post by CRIMPS on 2010-05-17
wow, what a mess.

---

### Post by kansasnoob on 2010-05-17
Look here:

[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)

---

### Post by avada on 2010-05-18
Wish I had this guide then. Although I still would have had to download the karmic cd wich I didn't have because I thought it would be simpler just to upgrade...
I was wrong. I still wonder what was actually the cause of this problem.

---

### Post by rwjussel on 2011-02-19
> **kansasnoob said:**
> Look here:

[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)

Great Guide.  This resolved the problem for me.  Thanks!

---

