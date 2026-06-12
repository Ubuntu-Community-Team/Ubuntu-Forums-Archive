---
title: "Install 4.10 failed"
date: 2005-01-30
forum: Installation &amp; Upgrades
---

### Post by Stekkie on 2005-01-30
hi all,

a few days ago i installed ubuntu 4.10. I made a partition of 5GB and used that partition in the installation. I formatted it in ext3. after a few staps the installation asked me if I wanted a bootloader, i answered yes. Then my computer needed to make a reboot.

When the PC started up again and the bootloader needed to load I got an error:

"Cannot find any operating system"

After a few reboots I decided to run the installation again... without success #-o 

I put the HD in my brothers pc and i formatted the linux-partition. I tried to start up and I got again an error:

"Cannot load GRUB ......."

Now I formatted all partitions and installed Windows XP again...

Had anyone this problem too? Can anyone please help me to install ubuntu ?

With kind regards
Stekkie (Belgium ;))

---

### Post by K. Trout on 2005-01-30
[SIZE=4]I had the same problem, it seem that Ubuntu has its own way of naming partitions. hda1 /boot became hda4; hda2 swap became hda1, etc. The bootable flag on /boot was turned off after the change to hda4.

My suggestion is to shutdown before doing any customizing to make sure you can reboot into Ubuntu.
[/SIZE]

---

### Post by Stekkie on 2005-01-30
actually, i dont get the solution now... how can i fix it that all other partitions stay like before ? inclusive my windows xp partition... 8-[

---

