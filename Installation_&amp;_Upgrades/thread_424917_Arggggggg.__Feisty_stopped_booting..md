---
title: "Arggggggg.  Feisty stopped booting."
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by ascus4 on 2007-04-27
My Feisty stopped booting.  It was working fine.  I installed a couple of things on the WinXP side and when I tried to reboot into Feisty it won't do it.  I can't imagine installin on the windows side would do this.

It starts to boot, gets to the Ubuntu screen and it turns off.  It does this in recovery mode as well.
I can't even get the system log for a look see.  

At one point I thought I saw something about not being able to start XServer but that's all I got.

If I boot off the live CD, what sort of things should I look for?  Can I access the system log this way?

Help.  I really don't want to start over again.

Thanks,

W-

---

### Post by ajgreeny on 2007-04-27
I assume you get past the grub screen, when you say " It starts to boot, gets to the Ubuntu screen and it turns off."

What do you mean by "it turns off"?  Do you just lose the usplash screen?

Try again and wait until nothing further happens for a minute or two, then Ctrl+Alt+F1 to see if you get a console screen.  If so login as usual with your username and password and see what happens if you try "startx".  You may get error messages that will help solve the problem in some way.

---

### Post by ascus4 on 2007-04-27
Sorry for not being more clear.  Yes, it does set past grub.  It goes to the screen that says ubuntu in large letters with the orange progress bar under it.  The compuer then powers off.  I was able to get it going again after several attempts.  
I then printed out the system log.

I had to power off and go to work.  I'm here and am about to see if I can get it to boot again.

---

### Post by ascus4 on 2007-04-27
And it boots just fine on the first try.

---

### Post by ascus4 on 2007-04-27
The system log says things like:

ACPI: Critical trip point

and

exiting on signal 15

---

### Post by ajgreeny on 2007-04-27
You could try editing your menu.lst file as root and adding **pci=noacpi** like this example to the third line for the kernel you are booting.
/boot/vmlinuz-2.6.10-5-386 root=/dev/hda6 ro **pci=noacpi** acpi_sleep=s3_bios

---

