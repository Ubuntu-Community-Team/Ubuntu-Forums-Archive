---
title: "trying to boot mepis from iso."
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by Kalidor on 2008-01-20
I'm trying to follow these instructions to install mepis without using a cd. I'm currently using ubuntu in dual boot with windows vista. [http://www.mepis.org/docs/en/index.php/Boot_from_ISO](http://www.mepis.org/docs/en/index.php/Boot_from_ISO)
I actually put the files to be moved in the C:/directory on the windows partition. Then edited grub as suggested, adding:
title MEPIS ISO
kernel /mepis/vmlinuz init=/etc/init apm=power-off vga=791 quiet
initrd /mepis/initrd.gz
I did not mount the iso image in the requested directory but in media/temp, using gmount. At reboot, choosing the mepis iso option it doesn't work. What is it that could be wrong? My current disk setup is:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10711    86036076    7  HPFS/NTFS
/dev/sda2   *       10712       19095    67344480   83  Linux
/dev/sda3           19096       19457     2907765    5  Extended
/dev/sda5           19096       19457     2907733+  82  Linux swap / Solaris

Did i misedit grub? Did i have to mount on mnt/temp? Thanks in advance, really.

---

### Post by banewman on 2008-01-20
Why not just follow the post and get it mounting then play around some?

---

### Post by Kalidor on 2008-01-20
I actually got the iso mounted in /mnt/temp, always with gmount. But at reboot it says error 15: file not found. I guess grub can't find the mepis folder in the windows partition? Do i have to write something before /mepis  in the grub entry written above, in order for grub to know where to look for the files?

---

### Post by Kalidor on 2008-01-20
> **banewman said:**
> Why not just follow the post and get it mounting then play around some?

You mean mount it and install mepis directly from ubuntu? I don't think i can do that, I need to install it in the actual ubuntu partition.

---

