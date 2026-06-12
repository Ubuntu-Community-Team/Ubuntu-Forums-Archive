---
title: "Ubuntu 18.04 newly installed stuck at boot"
date: 2019-11-12
forum: Installation &amp; Upgrades
---

### Post by leboone on 2019-11-12
Hi,
I did a new install of Ubuntu 18.04 from a DVD on an empty partition in my hard drive. Previously, the empty partition had Windows and it also had Ubuntu 12.04 and 14.04.

This is what fdisk shows:

| partition 1  |  partition 2 | partition 4 | -----extended partition 3------ |
|-------------|------------ |-------------|partition 5 | partition 6 (swap) |

Ubuntu 12.04 is in partition 5. Windows used to be in partition 1+2+4. Carved out partition 4 for Ubuntu 14.04. 
I have tried using both partition 1 and partition 2 for installing Ubuntu 18.04.

After install I can't login, I am stuck at booting, which seems to be a repeat cycling of the messages "failed to start network manager", "failed to start login service", "failed to start system logging service" and "failed to start GNOME display manager".
From the GRUB menu I can still login to Ubuntu 12.04, but for Ubuntu 14.04 it just shows a blank screen. I have no connection to a network.

---

### Post by mörgæs on 2019-11-12
Both Ubuntu 12.04 and 14.04 are out of support and hence a security breach. Why do you keep them?

Would it be an option to install 18.04 and erase the entire hard disk in the process?

---

### Post by leboone on 2019-11-14
Are you saying it won't boot because of the old OS?
I have some programs written that I haven't ported to the latest OS and would probably take quite some time to do so.
My other option would be to buy a new hard disk.

---

### Post by mörgæs on 2019-11-14
Sooner or later you have to port the programs I guess.

I can't say why it doesn't boot. More testing is necessary. The error messages you mentioned in original post do not sound like hardware errors.

---

### Post by oldfred on 2019-11-15
What brand/model system? What video card/chip?

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by leboone on 2019-11-19
Hardware: Intel i7-3770 CPU, ASUS P8Z77 motherboard, NVIDIA GTX680

To add some more details...
It's stops at "Started Hold until boot process finishes up","Started Terminate Plymouth Boot Screen" for a long time
Previously I mentioned Ubuntu 14.04 just boots into a blank screen. Now it can boot if I go into the advanced menu and select the right option.

---

### Post by oldfred on 2019-11-19
About same as my Asus with GT620.
I have to make multiple settings in UEFI to have it work. And after every UEFI update redo most of them. Have had some issues where too many boots of flash drive that failed or sdc (I have ESP on 3 drives & every flash drive), and it gets confused. I have had to reflash flash drive & only drive that booted was my emergency boot flash drive with rEFInd.
My newer Gigabyte board seems better, but I only have two drives & same flash drives.

With Asus I have to use nomodeset to boot, or just use my Intel video turning off nVidia & reconnecting to motherboard video. I found my Intel video was spec'd slightly faster than GT620.

Have you updated UEFI to newest available?

Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by leboone on 2019-11-24
the prospect of spending countless more hours on this made me just go and buy a new hard disk. 
installed in under 30 minutes and boots up fine.

---

