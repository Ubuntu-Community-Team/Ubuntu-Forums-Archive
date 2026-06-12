---
title: "Ubuntu 7.10 Blank screen after GRUB menu. Ati Mobi. X700."
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by Mohammad_Khalid_Hussain on 2007-10-29
Here is my laptop: Acer Ferrari 64-Bit 1.8Ghz. 512mb Ram, Ati Mobility Radeon X700.

My problem: Installation works like a charm, impressed with the new drivers during LiveCD, it even detects bluetooth! At the end, it asks for reboot, I say yes.. Computer reboots, GRUB menu appears, I can see everything, I choose ubuntu, screen goes blank, harddisk light flashing from a time and then nothing, I feel like its doing nothing.

Notes: I can install it perfectly and the LiveCD always works flawlessly. Please explain solutions clearly as I am very new ( as in I might start learning more if Wi-Fi works)

REply Soon. Thanks.

---

### Post by ReconIsense on 2007-12-28
as far as I know linux and broadcom arent very friendly. but hey if you can find a way to make wireless work plz let me know.

---

### Post by ThaRabbit on 2007-12-28
> **Mohammad_Khalid_Hussain said:**
> Here is my laptop: Acer Ferrari 64-Bit 1.8Ghz. 512mb Ram, Ati Mobility Radeon X700.

My problem: Installation works like a charm, impressed with the new drivers during LiveCD, it even detects bluetooth! At the end, it asks for reboot, I say yes.. Computer reboots, GRUB menu appears, I can see everything, I choose ubuntu, screen goes blank, harddisk light flashing from a time and then nothing, I feel like its doing nothing.

Notes: I can install it perfectly and the LiveCD always works flawlessly. Please explain solutions clearly as I am very new ( as in I might start learning more if Wi-Fi works)

REply Soon. Thanks.

While in black screen, try [Alt + F1 / F2]

I too have a x700 mobillity and my screen too reverts to black... the boot procedure, however, does continue. Those alt combinations should revert you back to a prompt showing you the proceedings of the boot procedure.

Try and explain to us what that shows :)

---

### Post by glantucan on 2007-12-29
Hi

I'll try to explain as easy as possible. First of all, when grub loads, press 'e' on the menu item you use to start ubuntu, you should get something as follows:
```

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=06745143-a3ed-405d-94a
a-f2d4a6ea20f1 ro _quiet splash_ locale=es_ES
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

Don't panic, we are interested on removing those underlined "quiet" and "splash" options from the line starting with "kernel"

Select the kernel line and press 'e' again, then you can go right and delete those words. Press enter and then press 'b'. Now you should be able to start your system without problem.

**But,**  we are not finished yet. This didn't change grub configuration permanently. to do so, once in your gnome or kde session, you should open a terminal window and type the following:

```
sudo gedit /boot/grub/menu.lst

```
in gnome, or
```
sudo kate /boot/grub/menu.lst
```
in kde.

This is the grub configuration file. You must find the "kernel" entry corresponding to the menu item for starting ubuntu (scroll down almost to the bottom of the file) and then remove again those "quiet" and "splash" options. 

With this you loose the splash screen but it's better than nothing, right? :)

Hope to be clear enough
Cheers

---

