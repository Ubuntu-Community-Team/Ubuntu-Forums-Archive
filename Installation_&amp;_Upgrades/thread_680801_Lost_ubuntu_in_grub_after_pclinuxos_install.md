---
title: "Lost ubuntu in grub after pclinuxos install"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by mgm2rr on 2008-01-28
Hey,  I had some extra space on my laptop that was dual booting XP and Gutsy, so I decided to try PCLinuxOS just for fun.  I installed it using the suggested installation settings, and now I can boot into XP or PCLinuxOS, but the boot menu does not offer an option of booting Gutsy.  I did not erase it from the partition it was on (2nd partition of the HD), and I can still access my files from Gutsy when using PCLinuxOS, but I just want to change my boot menu so that I can start Gutsy again.  I am also asking for help from the PCLinuxOS forums, but I trust these forums much more for sound advice.  Any help would be greatly appreciated.

-Matt

---

### Post by PmDematagoda on 2008-01-28
Not sure if Ubuntu advice can apply to PCLinuxOS as well, but I can be rather confident that the following piece of code should not hurt bit.

First, post the output of:-
```
cat /boot/grub/menu.lst
```

---

### Post by mocoloco on 2008-01-28
First some info on what's going on.  GRUB installs it's main stuff in the MBR (Master Boot Record) on the HD.  However it can't fit everything it needs there, so it will then check in the /boot/grub of your Linux install. When you install a second distro, in this case PCLOS, it overwrites the MBR to tell Grub to look in the /boot/grub of your PCLOS partition.  There are a couple of ways to go about getting what you need, here's the simplest and what I would do.
From your PCLOS install, make a BACKUP COPY of /boot/grub/menu.lst.  Then as root pull it up for editing, in Kate or whatever you want to use.
Now Open your menu.lst file on your Ubuntu partition, probably something like /media/hda1/boot/grub or something, I'm sure you'll find it since you can access your Ubuntu partition.  In that file find the sections similar to this:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=64e15bf7-916d-46a0-a9cf-b1f1f5ebd831 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=64e15bf7-916d-46a0-a9cf-b1f1f5ebd831 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
```
The just copy and paste them into your /boot/grub/menu.lst on your PCLOS partition.  The first OS listed will be the default that boots after 10 seconds, depending on how your grub is set up.

Be aware that since these two aren't seeing each other, when either distro has updates to the kernel and subsequently updates grub you'll have to do some work, after PCLOS kernel updates you'll have to re-add Ubuntu to grub, and after Ubuntu kernel updates you'll have to re-add the newest kernel info to the right menu.lst

Note: I haven't used PCLOS for a while, but I'm pretty sure they use grub.  If they're using Lilo as a boot manager you'll have to update it, or conversely reinstall the Ubuntu grub info to the MBR and update grub.

Hope that all made sense. :)

---

### Post by zvacet on 2008-01-28
I belive you will find answer [here](http://docs.pclinuxos.com/Boot_loader_FAQ).

---

### Post by mgm2rr on 2008-01-29
Thanks all, I was able to find the Ubuntu Grub entry and fix my PSLinuxOS to include it.  Now I have all my OS's running smoothly, and I have learned a bit more about Grub.

---

