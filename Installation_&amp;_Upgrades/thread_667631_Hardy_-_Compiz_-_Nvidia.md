---
title: "Hardy - Compiz - Nvidia"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by rianquinn on 2008-01-14
How do you install the nvidia drivers in Hardy. I installed the package

nvidia-glx-new

And nothing happened. So I went to add "nvidia" manually to my Xorg config file and nothing is there. Also, the restricted drivers module isn't there either.

What do I do to get Xorg to use the nvidia diver.

---

### Post by Partyboi2 on 2008-01-15
Have you tried going to System>Admin>Restricted Drivers  and enabling the driver?

---

### Post by hebetude on 2008-01-22
Restricted Driver Manager says my hardware does not need restricted drivers.

Compiz infintely loops, compiz-real 99% cpu usage.  I dropped compiz for metacity in the meantime.  I installed nvidia-glx-new verified the kernel modules were loaded, but compiz still fails to load. 

HP dv6775us 
nvidia 8600M

It's a fresh install, updated to Hardy.  I guess I will just reinstall Gutsy and redownload all the packages.

---

### Post by PmDematagoda on 2008-01-22
Did you try downloading the driver from the Nvidia web site and installing it manually?

---

### Post by hebetude on 2008-01-22
First I checked if it was even newer, they are the same version 169.07.  Then I checked the beta page ... its an even older version 169.04

Update: Just for poops & giggles, I loaded up metacity then used appearance to turn on compiz and it works fine.  Even with my custom config (which seemed to have been nuked).  It will probably be fubar when I reboot but who needs rebooting when youre running linux :)

---

### Post by Seamoneky on 2008-01-29
Same problem here. After doing a clean install of Gutsy and updating to Hardy, the process "compiz.real"  consumes 90% of cpu. I have downloaded the drivers from Nvidia and compiled them to 2.6.24-5-generic kernel..........As said before in this thread, there seems to be an infinite loop in the compiz.real process. I'll try to submit the bug.
In the meantime i'll stick to metacity which  seems to work just fine.

---

### Post by hebetude on 2008-01-29
As I previously said, you can unload/reload compiz and it usually works fine.  It deletes all your custom config settings though

huzzah!

You know Apple survives on a gimmick frontend and no backend, we have a great backend but a lousy frontend :/

---

### Post by Seamoneky on 2008-01-30
Reloading compiz didnt't work for me, cpu keeps looping turning unusable the pc.

---

### Post by breaking on 2008-02-17
I experienced a similar issue where the nvidia GLX module would not longer be loaded (grep libglx /var/log/Xorg.0.log turned up an error). The following commands fixed a link and compiz has been running fine ever since:

cd /usr/lib/xorg/modules
sudo ln -sf extensions/libglx.so.169.09 ./libglx.so

---

