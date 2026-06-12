---
title: "Grub Error 22"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by emackey3k on 2007-12-20
Hello,

I have a Dell Dimension 2400 with 1 Gig of RAM.  My system was set up as a dual boot with XP.  I recently got another Dell computer with XP on it so I decided I no longer needed XP on my Dimension.  I used Parted Magic to delete the XP partition that was before my Ubuntu partition and moved the Ubuntu Partition to an external drive.  I then copied the Ubuntu partition back to my internal hard drive.  I now get the GRUB error 22.  

Out of frustration I did a clean install of 7.10.  I am not happy with it, and would really like to go back to my old Ubuntu which was 7.10 upgraded from Feisty.  

The old partition is on the external hard drive.  I have tried to use Super Grub Disk to repair but it only goes to the old Grub options and gives me the same error 22.

Is there a way to reinstall Grub on the partition on the external drive and copy it back to the internal drive so I can have my old system back or is it a lost cause and should spend my time on getting the new system better?

I have been using Ubuntu for around 6 months really like it and will continue to do so.

---

### Post by elliotjreed on 2007-12-20
Try:
[URL="http://ubuntuforums.org/showthread.php?t=24113"]
http://ubuntuforums.org/showthread.php?t=24113[/URL]

The HowTo worked for my GRUB Error 22! And so may work for you!

---

### Post by tech9 on 2007-12-20
could try super grub to repair the grub loader

---

### Post by logos34 on 2007-12-20
> **emackey3k said:**
> Is there a way to reinstall Grub on the partition on the external drive and copy it back to the internal drive so I can have my old system back or is it a lost cause and should spend my time on getting the new system better?

You can try copying the old ubuntu back to the main drive.  You shouldn't even have to reinstall grub.  But you need to edit the old /boot/grub/menu.lst so that 'groot' and 'root' lines point to the new partition # (hd0,**0**).  It used to be (hd0,1) right?

---

### Post by emackey3k on 2007-12-20
Thank you for your replies

I will be trying them shortly and will let you know how they worked.

---

### Post by emackey3k on 2007-12-20
I am writing this on my old system.  Super Grub did not work for me.  It kept repairing it to the way it was before. 

What worked for me was manually editing the old /boot/grub/menu.lst.  

Special thanks to all that replied.  You guys are what makes the Ubuntu community so great.

---

### Post by tech9 on 2007-12-21
> **emackey3k said:**
> I am writing this on my old system.  Super Grub did not work for me.  It kept repairing it to the way it was before. 

What worked for me was manually editing the old /boot/grub/menu.lst.  

Special thanks to all that replied.  You guys are what makes the Ubuntu community so great.

SG is nice, but doesn't always resolve the issue - worth a shot anyway!

your welcome - Take Care :)

---

