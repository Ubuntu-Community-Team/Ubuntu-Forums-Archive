---
title: "Install stops at reboot. Why is this?"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by SPC_Hall on 2007-09-30
I'm installing 7.10, 32bit. I'm attempting to dual-boot w/ XP and I'm having a problem. 

I've already partitioned everything out, setup the swap & fat32 drives, installed 7.10 from the LiveCD and created the ubuntu.bin file for dual-booting. The last step I did was add a line referencing Ubuntu.bin (which I copied to XP's C drive) to the Boot.ini file.

So the only thing left to do is reboot and select Ubuntu from XP's boot options and allow Ubuntu to finish installing itself. However, after selecting Ubuntu from the list, I receive a blank black screen with nothing more than a blinking cursor in the top left corner. It does not respond to any keystrokes. I've let it go for a good 10 minutes, thinking it was just loading the Ubuntu install but nothing happened.

Any ideas?

Thanks,
JH

---

### Post by Yoooder on 2007-10-01
Most people who dual-boot do away with the Windows bootloader and instead use Grub to boot both OSes.

What you're doing may be feasible--but at the same time I doubt that the Windows bootloader will let you boot a Linux OS.

If you search the forms for how to reinstall grub for a dual-boot environment I'm sure you'll get exactly what you're after.  It's a pretty common thing.

---

### Post by Stant0n on 2007-10-01
You can try the write up listed here:
[http://www.techspot.com/vb/topic76345.html](http://www.techspot.com/vb/topic76345.html)

---

