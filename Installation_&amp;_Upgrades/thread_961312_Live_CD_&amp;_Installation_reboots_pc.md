---
title: "Live CD &amp; Installation reboots pc"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by losadel on 2008-10-28
Well what the title says.

If I boot from the live cd the progress bar almost gets to the end before the screen turns black. The cd-rom still reads for a couple of seconds before the system reboots or simply hangs.

I've done the Memtest and checked the disk for any errors but all seems fine.

Any ideas or suggestions on what might cause this?

---

### Post by Pumalite on 2008-10-28
Did you do md5sum on the iso? Did you burn at 4x or less? Do not use CD-RW

---

### Post by losadel on 2008-10-28
md5 is good.
I'll write a new disc and let you know if it worked or not.

Thanks.

---

### Post by losadel on 2008-10-28
New disc same problem.

I ran the livecd in "non quiet" mode and the PC reboots right after or while loading "command scheduler crond" which doesn't really make sense. 

What is suppose to load/happen after that module?

---

### Post by Pumalite on 2008-10-28
Post your specs

---

### Post by oilchangeguy on 2008-10-28
> **losadel said:**
> Well what the title says.

If I boot from the live cd the progress bar almost gets to the end before the screen turns black. The cd-rom still reads for a couple of seconds before the system reboots or simply hangs.

I've done the Memtest and checked the disk for any errors but all seems fine.

Any ideas or suggestions on what might cause this?

computer specs, please.

---

### Post by losadel on 2008-10-28
Found the problem but not the solution. Boots fine with onboard graphics but as soon as I install the graphics card it gives problems.

PC Specs:
P4 2.4c cpu
MSI PM8M-V (MS-7104) motherboard
Legend 6800GS agp
1gig something or other memory
WD 80gig IDE HDD

---

### Post by Pumalite on 2008-10-28
Try the Alternate CD

---

### Post by losadel on 2008-10-28
Cool, will do.

---

### Post by losadel on 2008-10-29
I installed the alternate cd and it still reboots just before the login screen.

booted into safe mode and tried to install nvidia drivers but can't do it in runlevel 1 so I had to remove gdm from runlevel 3
sudo update-rc.d -f gdm remove did the trick
nvidia driver complains about libc and kernel headers....
so I do sudo apt-get install build-essential xorg-dev pkg-config linux-headers-$(uname -r)
and nvidia drivers install yay but still can't get into X wtf?!

what next?

---

### Post by Pumalite on 2008-10-29
Do you see Grub?

---

