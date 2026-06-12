---
title: "Goofed up Grub"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by mtdave on 2010-05-01
Hi, I ran the upgrade from 9.10 to 10.04 last evening. When it got to the part where it was configuring Grub it asked me to check the partition to do that. I think I goofed up and checked the wrong one. Now my Grub is not displaying my operating systems. I don't know how to boot to any of them. I have Windows XP installed on the first partition I think and Ubuntu the next.

How can I fix my Grub?

Thanks

Grub Loading.
error: the symbol 'grub_puts_' not found
grub rescue>

---

### Post by mtdave on 2010-05-01
I got Grub reinstalled and got booted to 10.04.

Found the fix in this thread:
**     [SOLVED] upgrade to 10.04 and I'm stuck at a grub prompt**

---

### Post by oldfred on 2010-05-01
From a liveCD run 
```
sudo fdisk -l
```

That should show you your Ubuntu partition.
Then reinstall grub or grub2 whichevery you are using. Make sure to install the correct version of grub as mixing them causes even more confusion.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

