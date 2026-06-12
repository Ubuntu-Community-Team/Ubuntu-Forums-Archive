---
title: "Grub2 broken"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by AmpersUK on 2010-01-09
I am using 9.10.

I have Win7 and Ubuntu 9.10 installed.

Had an abortive attempt of triple booting with Kubuntu 9.10 which has left the Grub2 not working in any way.

**IMPORTANT**
I cannot load up Win7 or Ubuntu 9.10 from my computer at all.

Any help has to either rely on me loading up the original Ubuntu Installation CDROM (I have loaded this up to send this message) or typing meaningful commands into the Grub recovery which will open up when I try to access an operating system.

I hopefully await any help whilst I indulge in my usual practice of tearing my hair out, by the roots!

Ampers

---

### Post by oldfred on 2010-01-09
When you installed Kubuntu its grub took over booting. If you unstalled it the grub in the MBR is pointing to a partition that now does not exist.

You should just need to reinstall grub so it links to your current install.

Several versions essentially the same but some alternatives if one way does not work:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) 
Reinstall grub
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by AmpersUK on 2010-01-09
[quote=oldfred;8636834]When you installed Kubuntu its grub took over booting. If you unstalled it the grub in the MBR is pointing to a partition that now does not exist.

You should just need to reinstall grub so it links to your current install.

Reinstall grub
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) 

Thanks very much indeed, I used the middle suggestion, as edited above.

It was very clear and simple to understand once I used the second way of identifying my partition that the link provided.

Ampers.

---

