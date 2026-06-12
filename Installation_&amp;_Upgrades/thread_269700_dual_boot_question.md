---
title: "dual boot question"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by mrpixels0 on 2006-10-02
I want to install Ubuntu on a Sata drive that has an NTFS partition, now what i would like to know is:

when it asks to install Grub do i put it in the MBR or do i install it in a diffrent partion ?.

Now i do not think it will work if i install it in the MBR due to that being in NTFS format, so i would assume it must be installed in another partion but if i do that how do i tell the computer to load it at boot time so i can dual boot ?. 

is there some way of adding Linux to the windows boot menu ?.

I normally would not have a problem as I use fat32 but this is an install for a buddy of mine and i have not tried a dual boot from an MBR contained in an NTFS partion before and need help so as not to mess up windows or Linux after install.

thanks for your time.
MP0

---

### Post by Kateikyoushi on 2006-10-02
No you can not add linux to your windows boot menu.

On the other hand when you install ubuntu it will add your windows partition automatically to your grub menu.

[Dual boot help]("https://help.ubuntu.com/community/WindowsDualBoot").

Do you have only one hard drive ?

---

### Post by _teo_ on 2006-10-02
> **Kateikyoushi said:**
> No you can not add linux to your windows boot menu.

Actually, you can: ;) 
[http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why](http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why)

However I wouldn't do that.

---

### Post by Herman on 2006-10-02
The MBR is in the first sector of the hard disk.
The first track of the hard disk, 63 sectors, is not formatted with any file system.
The first partition does not begin until after sector 63. 
If you would like to verify this, just enter the following code into any Linux terminal (hard disk installed , or Live CD), ```
sudo fdisk -lu
``` So you do not have to worry about Grub touching your NTFS filesytem. 
Grub will work nearly as well with NTFS as with FAT32.
However, I do think that FAT32 is better than NTFS for a dual boot computer if it is possible to use it, because of the covenience of beng able to easily write to the FAT32 filesystem directly from Linux. 
Grub won't write anything to your Windows partition though.

Where you might have some trouble is with the sata disk, as opposed to IDE. Occasionally I read posts here in Ubuntu forums about people having either partitioning or bootloader problems with Sata disks. I those would only be a very small minority though, when you compare it with the number of people installing Ubuntu per day.

---

### Post by Kateikyoushi on 2006-10-02
That's new for me. Must be because I did not install win on that pc since I had gentoo on it.

Thanks for letting me know.

---

### Post by mrpixels0 on 2006-10-02
Thank you all for the information :), my buddy wants me to go ahead inspite of the possible dangers of losing data. and i told him i would later on tonight, he seems to want to try Kubuntu so i told him we would walk through it together from install to Package updating and compiling at least one application that way he can learn about make,./configure, make install Ect.

I just hope after it is all said and done he doe's not ask me to just remove it a few days later ;).

MP0

---

