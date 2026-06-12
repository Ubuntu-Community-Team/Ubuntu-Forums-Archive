---
title: "Nvidia 190.53 released and working in Lucid"
date: 2009-12-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-12-12
horsford@horsford-desktop:~$ uname -a
Linux horsford-desktop 2.6.32-7-generic #10-Ubuntu SMP Sun Dec 6 13:54:12 UTC 2009 x86_64 GNU/Linux

[32 bit](ftp://download.nvidia.com/XFree86/Linux-x86/190.53)
[64 bit](ftp://download.nvidia.com/XFree86/Linux-x86_64/190.53)

my xserver is up to date :)

---

### Post by donniezazen on 2009-12-12
> **Regenweald said:**
> horsford@horsford-desktop:~$ uname -a
Linux horsford-desktop 2.6.32-7-generic #10-Ubuntu SMP Sun Dec 6 13:54:12 UTC 2009 x86_64 GNU/Linux

[32 bit](ftp://download.nvidia.com/XFree86/Linux-x86/190.53)
[64 bit](ftp://download.nvidia.com/XFree86/Linux-x86_64/190.53)

my xserver is up to date :)

+1. working perfectly.

---

### Post by hikaricore on 2009-12-13
I wish they'd stick to a reasonable versioning system.
Currently I'm using 195.22 (beta) but I suspect that 190.53 (pre-release) is better.
>.>  They're just trying to make my head exploe.

---

### Post by Regenweald on 2009-12-14
Update, working with -8 kernel and latest xorg.

---

### Post by Taoye on 2009-12-14
Updated and working perfectly on my machine.

---

### Post by donniezazen on 2009-12-14
The latest update of xorg has broken nvidia 190.53. I can no longer get to login screen, I am just getting a command login. I reinstalled it and still it is not working.

How can i remove the graphic drivers and disable the visual effects?

Thanks.

---

### Post by jppr on 2009-12-14
> **Regenweald said:**
> Update, working with -8 kernel and latest xorg.

same but i use nvidia-glx-195 
[https://launchpad.net/~sevenmachines/+archive/nvidia?field.series_filter=lucid]("https://launchpad.net/%7Esevenmachines/+archive/nvidia?field.series_filter=lucid")
and system works fine :)

---

### Post by Regenweald on 2009-12-14
> **soham_1207 said:**
> The latest update of xorg has broken nvidia 190.53. I can no longer get to login screen, I am just getting a command login. I reinstalled it and still it is not working.

How can i remove the graphic drivers and disable the visual effects?

Thanks.

Thanks for the headzup. I'm grabbing the latest updates now, before I reboot I'll get the latest [64bit driver](ftp://download.nvidia.com/XFree86/Linux-x86_64/195.22/) and place it on my desktop in case I boot to a tty1 :)

Edit: good to go. Boot and graphics got faster :) No need for 195.

---

### Post by JBAlaska on 2009-12-16
As noted the 185 drivers broke Lucid, I'm using sevenmachines ppa 195.22 drivers, with no problema at all. Fast and stable so far with the -8 kernel.

---

### Post by dino99 on 2009-12-18
i've 195.22 from sevenmachines (nvidia+1) installed without errors, but Lucid don't see this driver & boot with nv in low resolution.

can't find a workaround as xorg.conf is no more used.

---

### Post by tad1073 on 2009-12-18
[http://ubuntuforums.org/showpost.php?p=8509573&postcount=8](http://ubuntuforums.org/showpost.php?p=8509573&postcount=8)

---

