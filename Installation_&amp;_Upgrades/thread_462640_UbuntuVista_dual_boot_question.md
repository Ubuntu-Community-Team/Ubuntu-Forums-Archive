---
title: "Ubuntu/Vista dual boot question"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by treesurf on 2007-06-02
Thanks to these most excellent forums I found the following link which has a good howto with instructions on installing Vista after Ubuntu.

[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)


However, I have one question I was hoping to get some advice on.  This howto ends up using Vista's MBR every time you start up.  I'm assuming you then have to select Ubuntu if you wish to boot it.  I would much rather have GRUB be used and have Ubuntu boot automatically, and then to go into the GRUB menu for the infrequent times I would have to use Vista.  

Is this possible?  If so, how?  I'm a linux dummy so please be easy on me!

thanks.

---

### Post by confused57 on 2007-06-02
> **treesurf said:**
> Thanks to these most excellent forums I found the following link which has a good howto with instructions on installing Vista after Ubuntu.

[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)


However, I have one question I was hoping to get some advice on.  This howto ends up using Vista's MBR every time you start up.  I'm assuming you then have to select Ubuntu if you wish to boot it.  I would much rather have GRUB be used and have Ubuntu boot automatically, and then to go into the GRUB menu for the infrequent times I would have to use Vista.  

Is this possible?  If so, how?  I'm a linux dummy so please be easy on me!

thanks.
You could use the live cd to reinstall grub to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

You would then need to add an entry to boot your Vista partition:
```
title  Windows Vista
rootnoverify  (hd0,1)
savedefault 
makeactive
chainloader +1
```
You'll need to run "sudo fdisk -l" to determine your Vista root partition, so root would probably be different from (hd0,1).

I don't know about Vista, but it's difficult to boot XP from grub, if XP is physically located on a partition after Ubuntu....guess if it doesn't work, you can restore Vista's IPL  to the mbr.  Just thought I'd mention this, if it's also true for Vista.

---

### Post by treesurf on 2007-06-03
Thanks for the advice, confused57.

So it sounds like using the Windows boot manager is a safer bet than trying to load Vista from grub.  Is there any way to configure the windows boot manager to load Ubuntu automatically by default?

---

### Post by treesurf on 2007-06-03
bump!   :)

---

