---
title: "Usplash is broken - blank screen on boot"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by matthias_k on 2007-10-23
Hi,

I think this Ubuntu's usplash is broken, it won't show when booting Gutsy. I played around with various options in /boot/grub/menu.lst and /etc/usplash.conf, but the settings look just fine to me (a solid 1024x768 resolution setting for usplash and "vga=792 quiet splash" as kernel options. I also tried to replace the ati driver with fglrx (which completely f*cked up my system by the way), but no luck.

Usplash does show up when shutting down by the way.

Help appreciated.

---

### Post by matthias_k on 2007-10-23
bump

---

### Post by qwerty12 on 2007-10-23
> **matthias_k said:**
> Hi,

I think this Ubuntu's usplash is broken, it won't show when booting Gutsy. I played around with various options in /boot/grub/menu.lst and /etc/usplash.conf, but the settings look just fine to me (a solid 1024x768 resolution setting for usplash and "vga=792 quiet splash" as kernel options. I also tried to replace the ati driver with fglrx (which completely f*cked up my system by the way), but no luck.

Usplash does show up when shutting down by the way.

Help appreciated.


Hi,

I got the same problem with a samsung on a ATI Radeon Express 200. Except my monitor says it is out of the refresh rate. Although my shutdown is broken as well.

I'll see if I can find a solution as well :D.

---

### Post by kOna on 2007-10-23
Same problem here on a Compaq nx8220 which has a Mobility Radeon X600 :(

---

### Post by felyduw on 2007-10-23
I also get the blank screen on boot. 
Weirdly enough, through the installation cd it did appear the usplash but stretched and weird.

Maybe this is a resolution problem ?

EDIT:

Solved.

I installed Startup Manager (package: startupmanager) and changed the boot resolution from 640x480 to 1024x768. It worked.

---

### Post by Sensenseppl on 2007-10-23
Same problem with my Mobilit Radeon x1600.

Edit: Startupmanager solved this problem. Changed boot resolution from 640x480 to 1024x768.

---

### Post by Lager_Monster on 2007-12-26
On my HP nx8220 boot times are sped up by monitoring the loading of the OS ie <Ctrl><Alt><F1>
Not touching any thing will load Ubuntu, but will take 5 minutes plus.

On my first attempt to install 7.10 I managed to get dual screens working but broke it all trying to get Compiz working.
After reinstalling I have not yet managed to get dual screens back :confused:

I had better results with the driver from the ATI site rather than the restricted driver.

---

