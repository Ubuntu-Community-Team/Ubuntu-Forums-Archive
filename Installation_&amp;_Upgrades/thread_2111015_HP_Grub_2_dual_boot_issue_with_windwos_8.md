---
title: "HP Grub 2 dual boot issue with windwos 8"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by bmc2013 on 2013-01-30
Same problem here. New laptop with Windows 8. Installed ubuntu 12.10, but only windows would load. Tried the recommended settings from boot-repair. Now I get an error from the multiple instances of Windows 8 in the really long grub menu. 

here's my link:
[paste.ubuntu.com/1592214]("http://ubuntuforums.org/paste.ubuntu.com/1592214")

Thanks for all of your help :)

~ Brian

---

### Post by oldfred on 2013-01-31
Moved to your own thread.

Clickable link.
[]("http://ubuntuforums.org/paste.ubuntu.com/1592214")[http://paste.ubuntu.com/1592214/](http://paste.ubuntu.com/1592214/)

Somehow you have a second efi partition as sda9. You can only have one efi partition. Use gparted from live installer and change flag from efi or delete partition sda9.

Not sure which or if all of the HP boot files are required. Some UEFI have all the repair efi files in another hidden partition that is not flagged as efi but they must change it or can use it somehow.

So if you get grub menu, you may need video or other boot options. What video do you have?
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
Another HP that worked.
       HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

---

