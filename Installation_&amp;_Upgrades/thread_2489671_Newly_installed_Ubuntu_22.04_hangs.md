---
title: "Newly installed Ubuntu 22.04 hangs"
date: 2023-08-06
forum: Installation &amp; Upgrades
---

### Post by nocom2 on 2023-08-06
I installed Ubuntu 22.04.2 from a USB stick, see below for hardware. Installation went ok, though I had to switch on the CSM compatability mode, else install wouldn't proceed. After reboot the machine displays some error messages and hangs (see attachments). These same messages were displayed when the system booted from the USB stick but had apparently no problems with. After a lot of experimentation I discovered that two version of the kernel were available: 6.2.0-26-generic and 5.19.0-32-generic, both with and without recovery mode (see attachments). The only version that does **not** boot is the one with kernel version 6.2. Version 5.19 and both recovery modes do boot. In all versions I get to see the error messages when booting. 

I had noticed before that 6.2 and Ubuntu does produce boot problems on my Tuxedo Ubuntu 22.04 laptop. In that case i have to opt for version 6.1.0. 

Does someone know why ubuntu 22.04 with kernel version 6.2 hangs my systems and what I can do about it? Of course I can circumvent this by changing which version to boot from in Grub, but all this is a hassle and I don't know when a new version will worsen things. That's whu I would like to understand this. Any help would be greatly appreciated.

Hardware
- Asus Proart X670E Creator Wifi, BIOS version 1516
- AMD 7800X3D
- 64GB RAM
- NVidia 3090

---

### Post by ubfan1 on 2023-08-06
Did you try a virtual terminal (ctrl+alt+Fn3) for a text login?  Maybe just a video/driver problem, as indicated by the successful recovery mode bootup.  I see others with problems with the 6.2, but I got it a few days ago on an update, and am running a 3080 on driver 535.86.05 without problems.

---

### Post by nocom2 on 2023-08-07
The virtual terminal does not work. For me the trouble started at the moment my kernel was upgraded to 6.2. I attempted a clean install but that took me a day to no avail.

---

### Post by ajgreeny on 2023-08-07
Try booting to your previous kernel from grub; that may still work.

---

### Post by nocom2 on 2023-08-08
> **ajgreeny said:**
> Try booting to your previous kernel from grub; that may still work.

Trouble is, this is my install result, there is no previous version. It will not boot as it is installed on my machine. It took me the better part of a day before I had figured out that it was kernel version 6.2 that wouldn't boot. I am still curious as to why version 6.2 will not boot on my machine.

---

### Post by eduardofilo on 2023-08-09
I have the exact same problem since a days ago. My workaround is booting 6.2 kernel in recovery mode and then in the menu that shows up, selecting "resume". The system ends in the desktop with all drivers loaded, i.e. with all the functionality.

---

### Post by nocom2 on 2023-08-09
> **eduardofilo said:**
> ,,, The system ends in the desktop with all drivers loaded, i.e. with all the functionality.

I did so and it works indeed, thank you. However the system warns that graphic drivers might not have full functionality. I did not notice that, I tested some games and they ran allright. 

The weird thing is since then I can boot directly into 6.2 without recovery mode, as if the system has finally "settled" itself ot whatever explanation applies. Maybe some upgrades solved the problem. Anyway, thanks for suggesting this solution!

---

