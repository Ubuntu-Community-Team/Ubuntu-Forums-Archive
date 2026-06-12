---
title: "tty1-tty6 broken in edgy"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by alanpotpot on 2006-10-28
I just installed Edgy on my laptop(Asus A8Ja) and I noticed that tty1 - tty6 is broken. All I see is a multi-colored screen. I did a clean install. Does anyone knows the solution to this?

Before I installed the ATI drivers tty1-tty6 is all black. After the installation of the drivers it became a multi-colored screen.

Laptop Specs:
Dual Core T2300
ATI x1600
100GB hdd
1024 Mb RAM

---

### Post by Drife on 2006-10-28
Sorry I don't have the solution but the same problem. However the consoles is working with vesa-driver so pretty sure it has something to do with the ATI-drivers. 
I have an Acer laptop with ATI X1600 and running the 8.29.6 drivers.
Has anyone tried with older drivers?

/Drife

---

### Post by alanpotpot on 2006-10-28
Its good to know that I am not the only one having problems with X1600 and Edgy.

---

### Post by Daniel15 on 2006-10-28
I'm having the same problem with an ATI X1400
[http://www.ubuntuforums.org/showthread.php?t=285872](http://www.ubuntuforums.org/showthread.php?t=285872)

EDIT: I fixed this problem by editing the resolution that the framebuffer uses. Edit **/boot/grub/menu.lst** (by typing 'sudo nano /boot/grub/menu.lst' in a terminal), and find the 'kernel' line for your kernel (it will be towards the end of the file). Add this to the end of the line:
```
 vga=0x318
```
For example, my kernel line now looks like:
```
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro quiet splash resume=/dev/sda8 vga=0x318
```
Reboot, and check if it worked.

The only problem I found was that the Ubuntu splash screen doesn't look proper (the Ubuntu logo is not centered). Apart from that, everything appears to be working fine :)

---

### Post by alanpotpot on 2006-10-29
Thanks man! It worked for me :)

---

