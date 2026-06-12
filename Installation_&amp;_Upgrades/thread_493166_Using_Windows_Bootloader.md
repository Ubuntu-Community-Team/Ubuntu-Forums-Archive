---
title: "Using Windows Bootloader"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by tylermenezes on 2007-07-05
In the Windows Dual Boot tutorial on the wiki, it says I may opt to gracefully let the Windows Vista bootloader have the MBR, in case I should need to fix the MBR later. I've had to do this twice before, so I'd like to do this. Can anyone tell me how I could use Windows for the bootloader, assuming I already have Vista installed and have not yet installed Ubuntu?

---

### Post by silverdarkness on 2007-07-11
Get a ubuntu cd and go through the usual install (with grub). Once ubuntu is installed boot into vista and install a free program called easyBCD. 

Once easyBCD is installed you can use it to replace grub with the vista bootloader and follow their instructions to add ubuntu as a boot option in the vista bootloader. Since i have not used easyBCD before i cannot post more detailed instructions but if you google "easybcd" or visit their website you will be able to find exact details...

---

### Post by louieb on 2007-07-11
Not sure about VISTA but if its like XP [Booting Using NTloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=351692")

---

### Post by aysiu on 2007-07-11
Have you considered using Wubi?
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by confused57 on 2007-07-11
> **tylermenezes said:**
> In the Windows Dual Boot tutorial on the wiki, it says I may opt to gracefully let the Windows Vista bootloader have the MBR, in case I should need to fix the MBR later. I've had to do this twice before, so I'd like to do this. Can anyone tell me how I could use Windows for the bootloader, assuming I already have Vista installed and have not yet installed Ubuntu?
I think this may be what you're looking for:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

