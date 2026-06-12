---
title: "Trouble Accesssing UEFI 16.04"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by anon24 on 2016-04-27
After installing 16.04, I noticed that I was no longer able to access UEFI. 

Originally, I tried to install 16.04 through the Terminal.

This did not work, and I was forced to put Ubuntu on a USB with a separate computer.

I made the Ubuntu USB on a mac (my Ubuntu computer is a PC).

I turned off fast boot in the UEFI so that I could access said USB drive.

Everything installed just fine and it resulted in me being able to use the computer again.

However, now I want to turn fast boot back on and am unable to figure out how to access UEFI.

This screen pops up at the start of the booting process:

(I did try to hit Ctrl-I and there was no option to turn on fast boot)

---

### Post by oldfred on 2016-04-27
UEFI fast boot in effect turns off user access to UEFI thru keyboard.
Normal boot takes time to scan system for changes and gives you time to press a key. But fast boot assumes all hardware & configuration is identical to previous boot and jumps immediately to loading system.
With Windows there are ways to get to UEFI from Windows system.
And Ubuntu/grub has added a menu item to get to UEFI also.
```
### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}

```

But if no system boots then you have issues. My motherboard has separate settings for fast boot from cold boot, and warm reboot. So I set cold boot to normal and warm reboot to 3 sec delay, but fast boot otherwise.

You may be able to cold boot and immediately press correct key to get into UEFI. If laptop remove battery. And hold power switch to drain any left over power so total cold boot.
Some have to use jumpers on motherboard to reset UEFI, but then any changes you made to setting have to be redone. Others have to remove coin battery from motherboard to totally reset. Some laptops have a pinhole for reset on bottom of  laptop.
One brand with early UEFI had no way to recover and had to go back to vendor.

---

### Post by Bucky Ball on 2016-05-04
*Thread moved to **Installation & Upgrades**.*

---

