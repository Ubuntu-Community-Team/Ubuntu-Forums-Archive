---
title: "Install Ubuntu Old Laptop"
date: 2013-06-03
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2013-06-03
Want to install Ubuntu in an old laptop, but cd drive is not working. I could, however, remove the HDD and connect it to my main PC via USB. Is it possible to install Ubuntu OS in this manner? or what do you guys recommend?

Thanks for all your great work.

---

### Post by snowpine on 2013-06-03
What are the specs of the laptop?
Why not install from a USB thumb drive?
Is it possible to repair the broken DVD drive?

---

### Post by tgalati4 on 2013-06-03
Yes you can.  You can also install the the disk drive internally in another machine and install it or if the laptop has a USB port, you can make a Live USB stick and boot off of it, then install it to your hard disk.  The USB acts just like a CD drive.  You might need to activate the "Boot from USB" in the BIOS or change the Boot priority to include USB.  Some older laptops do not support booting from USB.

---

### Post by mayagrafix on 2013-06-04
> **snowpine said:**
> What are the specs of the laptop?
Why not install from a USB thumb drive?
Is it possible to repair the broken DVD drive?

Its a HP Presario 2100 with AMD Athlon XP-M 2400+ and I think the USB thumb drive is a good solution. Not worth the time or money to repair DVD drive, just plan to use it as a extra word processor (read: typewriter) for my home office.

Thanks for ur input, will get on it right away:p

---

### Post by mörgæs on 2013-06-04
You can not run Ubuntu at a usable speed, but Lubuntu 13.04 is an option.

---

### Post by Mark Phelps on 2013-06-04
I would be surprised if your Presario 2100 will boot from USB drive.  I have an old (now "retired") Presario 2580 and it did NOT boot from USB drive.  We're talking about 10-year old laptops, and back then, booting from USB was not a standard practice.

---

### Post by mayagrafix on 2013-06-04
> I would be surprised if your Presario 2100 will boot from USB drive
Huhhh ... the thought had crossed my mind. Well then, hoz 'bout I remove the HDD, put it in an external USB case, and install the OS (Lubuntu) that way? does it have to be tethered to mobo in order to configure correctly?

---

### Post by mayagrafix on 2013-06-15
Our story so far: I extracted the HDD from ye ol' laptop and hooked it up to my main PC via an external USB enclosure. Proceeded to install Ubuntu 12.04 (32 bit) and after some dillydallying with mount points, partitions and formating, got it right enough for the install to proceed. After returning HDD to original laptop, it booted up nicely and seems to work well with only 51% of the available 430 megs of RAM (no SWAP used). Then proceeded with 565 updates (!¡). I did get a message asking me where to install GRUB, seems to be a bit of problem because of the UN-orthodox earlier installation. Says it might no be able to boot - but so far so good, I have successfully rebooted and getting ready to finish set up. It is funny to see Floppy Drive in the Nautilus file manager. Works well enough for what I want it to do. 

Thanks to all for great help and advice.

---

