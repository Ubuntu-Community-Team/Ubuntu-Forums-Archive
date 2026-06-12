---
title: "upgrade won't boot [GRUB] problem"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by nlz on 2010-04-30
I just upgraded to the new LTS from 9.10, the PC rebooted and now it says:
> 
GRUB loadin.
error: the symbol 'grub_puts_' not found
grub rescue>

whereas I'm really sure I installed grub on the proper partition (sda1) since I checked it in gparted .

What to do?

---

### Post by pauljwells on 2010-04-30
I had that error a lifetime ago and still haven't fixed it yet. I think there's something very wrong with the grub2 on Lucid.
I'm guessing you're dual-booting? I had to resort to reinstalling the Windows MBR so I could at least get XP back. I'm now on my third or fourth reinstall, recovery, tinker... cycle and still no luck.
Out of interest, do you have any recovery partitions or other things on your HD?

---

### Post by nlz on 2010-04-30
setting root, find, or starting normal grub (insmod etc) won't work...

---

### Post by nlz on 2010-04-30
> **pauljwells said:**
> I had that error a lifetime ago and still haven't fixed it yet. I think there's something very wrong with the grub2 on Lucid.
I'm guessing you're dual-booting? I had to resort to reinstalling the Windows MBR so I could at least get XP back. I'm now on my third or fourth reinstall, recovery, tinker... cycle and still no luck.
Out of interest, do you have any recovery partitions or other things on your HD?

no dual-boot, that's why I didn't expect any problems.. I think I'll start downloading the whole thing and then reinstall.. damn..

---

### Post by nlz on 2010-04-30
trying to fix grub with a 9.10 live CD, to no avail; 'selected disk does not exist..'

---

### Post by psusi on 2010-04-30
Grub should be installed on sda, not sda1.  I suggest doing a clean install of lucid.

---

### Post by oldfred on 2010-04-30
You can just install grub to sda.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by pognonec on 2010-05-01
I had the same problem, and fixed it by changing the order of my HDs at boot time, directly in the BIOS (press DEL at boot, on my PC. It may be different on yours).
Hope this helps!

---

