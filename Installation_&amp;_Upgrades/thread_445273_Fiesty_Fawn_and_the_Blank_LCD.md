---
title: "Fiesty Fawn and the Blank LCD"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by erichswanson on 2007-05-15
Hi all,

I searched the forums for this, honest I did, but here I am posting after not finding anything that *directly * answered my issue.

I downloaded the ISO for Fiesty Fawn and ran a checksum which checked out. I burned it into a dvd and set my dvd drive as my primary boot device. 

The comp spins the cd up and recognizes it as a bootable device, but when it attempts to start whatever it's going to start, both of my LCD monitors go blank, as if not receiving a signal. 

Now, I've read about problems with ATI cards/drivers, and I am using an ATI x800xt. I've heard that changing some setting somewhere fixed this in installed situations, but I'm stuck with an uninstalled OS on a dvd. 

Can anyone help?

Thanks,
...erich

---

### Post by frankt on 2007-05-16
Same problem here. I managed to get the OS installed using the alternate CD. However, after the boot logo, my screen just goes blank, and receives no signal. I'm using an ATI X1900XTX.

---

### Post by erichswanson on 2007-05-23
bump

...anyone have any suggestions on this?

---

### Post by srt4play on 2007-05-23
I've seen this a few times on LCD monitors.

What you can do is append "vga=771" to the end of the kernel boot line.  If that doesn't work then try "vga=791".

From a live cd, you would hit F6 at the menu and add the above to the end of the line.

If it's on a system that's already installed, hit escape to get into the grub menu and highlight the top entry.  Hit "e" then highlight the line starting with "kernel".  Add the above to the end of the line and hit escape.  Then "b" to boot the entry.  If it works then you can make it permanent by editing the file /boot/grub/menu.lst

---

