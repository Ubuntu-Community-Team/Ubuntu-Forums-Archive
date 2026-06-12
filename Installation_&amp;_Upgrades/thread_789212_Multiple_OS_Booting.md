---
title: "Multiple OS Booting"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Chucar on 2008-05-10
I'm new to Ubuntu, but not to linux and windows. I have an Amd 3800 dual core machine, with plenty of ram, etc. I wanted to put the recent Ubuntu OS on my system and be able to boot it with the windows xp and other linux systems on my machine. I also run System Commander.
   Well, I found that Ubuntu wants to install Grub and overwrite my MBR, keeping me from using the other linux OS. When I reinstall System Commander, it will no "recognize" the Ubuntu install, but will the other OS's on the machine. I went to the System Commander website and they indicate that Ubuntu will not work with System Commander. Can anyone tell me how to overcome this situation?

---

### Post by confused57 on 2008-05-10
> **Chucar said:**
> I'm new to Ubuntu, but not to linux and windows. I have an Amd 3800 dual core machine, with plenty of ram, etc. I wanted to put the recent Ubuntu OS on my system and be able to boot it with the windows xp and other linux systems on my machine. I also run System Commander.
   Well, I found that Ubuntu wants to install Grub and overwrite my MBR, keeping me from using the other linux OS. When I reinstall System Commander, it will no "recognize" the Ubuntu install, but will the other OS's on the machine. I went to the System Commander website and they indicate that Ubuntu will not work with System Commander. Can anyone tell me how to overcome this situation?

I'm not familiar with System Commander, but you could try installing grub to Ubuntu's root partition, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
read the instructions in the howto, but it would be something like:
```
root (hdx,y)
setup (hdx,y)
```
substitute the output of "find /boot/grub/stage1" for (hdx,y).

---

