---
title: "Keyboard stopped working at login screen"
date: 2010-01-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by whoop on 2010-01-05
My keyboard does not seem to work any more when I am at login screen (entering characters does not add them to password field, pressing enter does not execute login attempt).
Keyboard works in grub and works when I enter recovery console...

Did I miss something? If not, anybody else experiencing this?

---

### Post by Reiger on 2010-01-05
And do you, by any chance, have an ATI card? And do you find that some tty (1, 2, or whatever number it pleases the driver) contains/spits out a bunch of messages about errors to do with interrupt and/or I/0? (Using Ctrl+Alt F1, F2 and other F- keys). 

If so, booting with radeon.modeset=0 appended to the kernel line might work.

---

### Post by whoop on 2010-01-05
> **Reiger said:**
> And do you, by any chance, have an ATI card? And do you find that some tty (1, 2, or whatever number it pleases the driver) contains/spits out a bunch of messages about errors to do with interrupt and/or I/0? (Using Ctrl+Alt F1, F2 and other F- keys). 

If so, booting with radeon.modeset=0 appended to the kernel line might work.

No, I am not using an ATI card. I am running it from VMWare server. 

I also tried to login in via recovery console and startx the keyboard stops working as soon as GNOME is loaded (in that situation)...

---

### Post by tim1 on 2010-01-06
The keyboard stopped working for me too.

I can login with the console and do startx, but it doesn't work in Gnome either, extremely annyoing.

---

### Post by jmdsdf on 2010-01-06
I don't know if this is the same problem that I'm having. My computer now boots to tty1 with a login console, after logging in, and loading kdm manually or running startx it loads X and the keyboard and mouse is unresponsive. I wish I knew what packages to roll back to fix this problem.

---

### Post by whoop on 2010-01-06
> **tim1]
The keyboard stopped working for me too.

I can login with the console and do startx, but it doesn't work in Gnome either, extremely annyoing.
[/QUOTE]

[QUOTE=jmdsdf said:**
> I don't know if this is the same problem that I'm having. My computer now boots to tty1 with a login console, after logging in, and loading kdm manually or running startx it loads X and the keyboard and mouse is unresponsive. I wish I knew what packages to roll back to fix this problem.

Guys, are you getting this with a vmware client install or on non-virtual hardware? ATI cards?

@jmdsdf: My mouse is still responsive...

---

### Post by tim1 on 2010-01-06
I am getting this on my dell XPS m1330 laptop.

This is a machine that's sold with Ubuntu, and it has a NVidia graphics card.

---

### Post by whoop on 2010-01-06
> **tim1 said:**
> I am getting this on my dell XPS m1330 laptop.

This is a machine that's sold with Ubuntu, and it has a NVidia graphics card.

Interesting...

I just solved my problem via doing a dist-upgrade (although it removed 16 packages), so I'm not sure if I should recommend it but it seems to have worked for me.

---

### Post by jmdsdf on 2010-01-06
I'm running an nVidia 8200 with a 32-bit install, not virtualized. Doing a dist-upgrade removes my nvidia-glx-190 drivers, but I will try it later.

---

### Post by jmdsdf on 2010-01-06
Problem solved! I'm back in business, minus my nVidia drivers. :(

UPDATE: I installed SevenMachine's ppa for the 195 drivers, everything is back to normal (minus KDM not starting automatically)

UPDATE #2: KDM should start automatically again thanks to this thread: [http://ubuntuforums.org/showthread.php?t=1373554]("http://ubuntuforums.org/showthread.php?t=1373554")

---

### Post by garvinrick4 on 2010-01-06
Keyboard and USB mouse stopped working in 10.04, touch pad working. How do you manage
dist upgrade without typing password to complete action? Only have GUI version available with
terminal not accepting keyboard.

---

### Post by garvinrick4 on 2010-01-06
Recovery keyboard worked fine. Went to Shell to update 10.04 but repositorie's were on the fritz.
Will just try at later time. Can go back to 9.10 partition for a while.  Same mirror anl.gov in
the United States works well in Karmic.

---

