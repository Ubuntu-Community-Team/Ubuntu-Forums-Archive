---
title: "Toshiba Satellite 1800-412 Power Down"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by rjeeves33 on 2005-08-09
Hi

I've just installed Hoary on my laptop and so far pretty much everything works great.  One thing I have noticed though the laptop doesn't Power Down.  If I choose to Shut Down the Hard disk blinks then the screen goes black but the laptop doesn't actaully power off.  ONe interesting thing is the Laptop will shut down correctly if I choose the Hibernate option.  Where would I begin troubleshooting this issue/which log files to check.

Thanks in advance

---

### Post by GavinX on 2005-08-09
In a terminal do the following:

sudo gedit /boot/grub/menu.lst

Look for the following section:

title        Ubuntu, kernel 2.6.12-6-386 
root        (hd0,0)
kernel     /boot/vmlinuz-2.6.12-6-386 root=/dev/hda1 ro vga=791
initrd       /boot/initrd.img-2.6.12-6-386
savedefault
boot

At the end of the line which begins with "kernel" insert the following "acpi=off" (without the "")

Save the file and reboot.

---

### Post by rjeeves33 on 2005-08-09
Awsome. Thanks very much for your help.  Works like a charm.

Rob

---

### Post by GavinX on 2005-08-09
Kool. Take care.

---

### Post by michael_j on 2007-10-10
Thank you - acpi=off as the last entry on  the 'kernal' line of /boot/grub/menu.lst   (on all lines that begin with 'kernal' ((no guotes)) if you have upgraded your system) works on my new Toshiba Satellite A135-S4527.

Before, the machine continued to draw power after shutdown in Ubuntu 7.04.  Even the power switch would not work and I had to resort to pulling the battery (and replacing it as the machine powered off).

This simple addition to the 'kernal' line of the /boot/grub/menu.lst works like a charm.

---

### Post by hornetcoach on 2007-12-29
acpi=off didn't work for my toshiba A55-S326 laptop.  Before modifying /boot/grub/menu.lst file the output of lsmod showed a "toshiba_acpi" process started.  The shutdown would end with a blank screen and my harddrive activity light on.

After the mod - the toshiba_acpi process is absent and the shutdown hangs up on the ubuntu spash screen and no harddrive activity...so it's better, but not best!

I am basically having the same issue the others in this thread had - I can only power the laptop down using the hard power button.
Thanks in advance for any help!

---

### Post by dscotese on 2008-07-03
HornetCoach,

I bought an 8800 mAh battery called PA3357-1BRL.  This battery was designed for the Toshiba Satellite A50 and A55.  The shape and connector and electrical characteristics are compatible with my Toshiba laptop, but I can’t open the laptop when the battery is installed. Oops!!

I would like someone who can use this battery to have it.  This is a free battery that cost me $70.  It would be nice if you sent me some $$ once you receive it, but I’ll send it to anyone who says they can use it.

---

