---
title: "can't boot into 10.04 anymore"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by raptorhunter on 2011-10-27
My MBR got borked so I tried to run boot repair. Now grub just dumps me a the terminal and I don't know what to do.

Here is my pastebin from the boot repair program

thanks! :)

[http://paste.ubuntu.com/721283/](http://paste.ubuntu.com/721283/)

---

### Post by raja.genupula on 2011-10-28
> **raptorhunter said:**
> My MBR got borked so I tried to run boot repair. Now grub just dumps me a the terminal and I don't know what to do.

Here is my pastebin from the boot repair program

thanks! :)

[http://paste.ubuntu.com/721283/](http://paste.ubuntu.com/721283/)

you mean grub prompt like "grub>" 
then check this out 
[https://help.ubuntu.com/community/Grub2#A.27.27grub.3E.27.27_Prompt_Booting](https://help.ubuntu.com/community/Grub2#A.27.27grub.3E.27.27_Prompt_Booting)

---

### Post by raptorhunter on 2011-10-28
It doesn't work.

When I type linux /vmlinux root=/dev/sda1 ro it says file not found.

---

### Post by raja.genupula on 2011-10-29
> **raptorhunter said:**
> It doesn't work.

When I type linux /vmlinux root=/dev/sda1 ro it says file not found.

go with this 

[http://blogs.deepal.org/2009/06/how-to-fix-mbr-using-ubuntu-live-cd.html](http://blogs.deepal.org/2009/06/how-to-fix-mbr-using-ubuntu-live-cd.html)

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

all the best.

---

