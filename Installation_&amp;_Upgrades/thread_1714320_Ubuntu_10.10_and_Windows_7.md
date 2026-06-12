---
title: "Ubuntu 10.10 and Windows 7"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by zdeuyo on 2011-03-25
Hello Forum,

I am not sure if this question has been solved as of yet, but I have the following I would like to do.

I currently have Ubuntu 10.10 64 bit installed and I would like to reconfigure my partition so I can reinstall Windows 7 – 64 bit on my computer.

I have the recovery disk that HP sent me and I have tried Virtual Box and no luck, so just to avoid any problems I would like to spilt the partitions and set up the grub bootloader so I can have Ubuntu and Windows as a choice a start up. 

Is there an easy way to do this or do I need to completely reformat my hard drive?

Thanks in advance for your assistance forum. Have a great one.

---

### Post by Rubi1200 on 2011-03-25
If you install Windows to a partition after Ubuntu, it will overwrite the MBR leaving only Windows as a boot choice.

However, with 2 commands from the LiveCD and 1 more back in Ubuntu, you can be back in business dual-booting:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by zdeuyo on 2011-03-25
Hello,

Thank you for your expedite reply. I very much appreciate this and I will be looking into doing this. Thanks again!

---

### Post by Quackers on 2011-03-25
Just one thing to watch for, though.
A manufacturer's recovery disc may insist on using the original hard drive layout. In other words it may not run unless it can use the whole hard drive to install to. Some do this, but others will allow a smaller partition to be used. This would obviously mean you would need to re-install Ubuntu afterwards. You should make backups or even a clonezilla image of your Ubuntu partitions.

---

### Post by Rubi1200 on 2011-03-25
Good point Quackers and thanks for pointing this out.

I suggest you make backups/clone the partitions either way; you never know what can go wrong.

If you need more help, please let us know.

---

