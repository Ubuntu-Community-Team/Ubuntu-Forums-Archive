---
title: "Black Screen"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by Sanctus Messor on 2007-08-16
System Specs:
Intel C2D 6750 2.66GHz
4GB RAM
500GB HDD
8800 GTX nVidia

I can use the boot disk fine, I have to change the VGA setting to 1280*1024 before I boot it though. My monitor has a max resolution of 1920*1200. The boot disk works fine, then the partition and install go smoothly too. But after rebooting I cant get the OS to Start. GRUB launches and the normal "Kernel Alive" text flashes and then.... Black...

Help please?
Thanks,
Sanctus

---

### Post by Pumalite on 2007-08-16
Try Ctrl+Alt+F1. Then if you get a command line:
sudo dpkg-reconfigure xserver-xorg. Most defaults are OK. Choose 'vesa' as your driver. Then: 'startx'

---

### Post by Sanctus Messor on 2007-08-16
Pressing CTRL + ALT + F1 did not yield a command line. It made the black screen worse. Before the screen was black but my monitor registered there was (some kind of) signal but now the monitor isn't even picking up on anything displaying that there is no signal.

---

### Post by Sanctus Messor on 2007-08-16
Furthermore, while in black screen with monitor detecting (some kind of) signal, I typed my User and Pass like I normally would and that too threw it out of range (or w/e). To me it seems that it did log in but the screen res is not automatically being detected or something.

---

### Post by Pumalite on 2007-08-16
I agree with you is the display. But without command line is very little more that it occurs to me. You could try other combinations with F2, F3, etc.

---

### Post by merlinus on 2007-08-16
Can you boot into Recovery Mode from the grub menu?  Does that get you to a command line?

-merlin

---

### Post by Sanctus Messor on 2007-08-17
For me the problem was with the splash screen that tries to fire up after GRUB loads. To resolve the problem i did the following

1. Startup in Recovery Mode (Option in the GRUB menu)
2. Type the following once logged in:

Code:

sudo vi /boot/grub/menu.lst

3. Scroll down till you see a section "## ## End Default Options ##"
4. A few lines below this you will see something like

Code:

title		Ubuntu 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=aa5decf1-4785-4eba-9433-6d7b3fc6c1c1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

On the line starting with "kernel" remove the word "splash", so it looks like:

Code:

title		Ubuntu 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=aa5decf1-4785-4eba-9433-6d7b3fc6c1c1 ro quiet
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

5. Save your changes by typing the following and then pressing return.

Code:

:x

6. Reboot

Code:

sudo reboot

Hope this helps.

---

