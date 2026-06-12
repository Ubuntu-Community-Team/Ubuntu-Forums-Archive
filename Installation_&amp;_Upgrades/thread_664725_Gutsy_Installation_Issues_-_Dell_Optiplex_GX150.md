---
title: "Gutsy Installation Issues - Dell Optiplex GX150"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by dmessier on 2008-01-11
I'm having issues installing Ubuntu 7.10 on a Dell Optiplex GX150. 996Mhz, 512GB RAM. It might be related to the display, but I am not sure.

When I use the Desktop CD install, I can boot to the first menu where I have the option to press F1 for advanced options, or ENTER for the default live system. I've used the same CD to install on two other machines with no problem, and I have not seen this menu before. After pressing ENTER, it spits out several messages and eventually gets to a prompt. Among the messages are "usplash: Setting mode 640x480 failed" and "screen init failed". It never reaches the desktop from which the install option is available.

Using the Alternate Install CD, I can boot to the first menu where I have the option to press F1 for advanced options, type "cli" for command line interface install only, or press ENTER to do the normal install. After I press ENTER to do the normal install, the screen goes blank. the monitor light goes from green to yellow, as if it is not even getting a signal.

Any help would be appreciated.

---

### Post by Pumalite on 2008-01-11
Graphics? Chipset?

---

### Post by dmessier on 2008-01-11
I should have mentioned that initially.

Graphics card is an AGP PowerVR 250. 32MB.

---

### Post by Pumalite on 2008-01-11
Post:
lshw

---

### Post by dmessier on 2008-01-11
*-display
    description: VGA compatible controller
    product: PowerVR Neon 250 Chipset
    vendor: NEC Corporation
    physical id: 0
    bus info: pci@0000:01:00.0
    version: 04
    width: 32 bits
    clock: 66Mhz
    capabilities: pm agp agp-1.0 vga bus_master cap_list
    configuration: latency=64

---

### Post by Pumalite on 2008-01-11
Better use the Alternate CD to install. You might have to use some boot parameters to install, but first try to install the old fashion way.
[http://ubuntuforums.org/showthread.php?t=118359&highlight=Dell+Optiplex+GX150](http://ubuntuforums.org/showthread.php?t=118359&highlight=Dell+Optiplex+GX150)

---

### Post by dmessier on 2008-01-11
I have tried with the alternative CD as well.

Using the Alternate Install CD, I can boot to the first menu where I have the option to press F1 for advanced options, type "cli" for command line interface install only, or press ENTER to do the normal install. After I press ENTER to do the normal install, the screen goes blank. the monitor light goes from green to yellow, as if it is not even getting a signal.

Any idea what parameters I should change?

---

### Post by Pumalite on 2008-01-11
I'll give you a guide and a collection to try. Try them one by one:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)

---

### Post by dmessier on 2008-01-11
I posted that last reply before you added in that link.

I checked it out and the recommendation was to disable the AGP video card through the BIOS and use the onboard video.

I did that - and now I'm into the Ubuntu Desktop CD Setup - farther than I was before. I believe the problem is solved.

Thanks!

---

### Post by Pumalite on 2008-01-11
You are welcome. Good luck.

---

