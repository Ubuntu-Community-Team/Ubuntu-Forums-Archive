---
title: "Dual Boot Ubuntu and Xubuntu- Grub problem"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by cmulax on 2007-02-16
So I have a perfectly stable and running hard drive with ubuntu on it, and I wanted to give xubuntu a try on my second hard drive.  I successfully installed xubuntu on it using the 6.10 live cd, however grub only shows the xubuntu os.  I know for a fact that everything in my first hard drive is intact, as I can mount it and use everything in it, but I am at a loss as to how to fix grub to add my first hard drive back into it.

Any help would be appreciated!

---

### Post by confused57 on 2007-02-16
> **cmulax said:**
> So I have a perfectly stable and running hard drive with ubuntu on it, and I wanted to give xubuntu a try on my second hard drive.  I successfully installed xubuntu on it using the 6.10 live cd, however grub only shows the xubuntu os.  I know for a fact that everything in my first hard drive is intact, as I can mount it and use everything in it, but I am at a loss as to how to fix grub to add my first hard drive back into it.

Any help would be appreciated!

What you can do is write down your menu.lst entries to boot Xubuntu...then use the live cd to reinstall your Ubuntu grub to the mbr:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

then add your Xubuntu grub entries to the very bottom of your Ubuntu /boot/grub/menu.lst file.

---

