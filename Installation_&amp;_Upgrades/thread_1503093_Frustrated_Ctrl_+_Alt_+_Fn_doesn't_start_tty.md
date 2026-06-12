---
title: "Frustrated Ctrl + Alt + Fn doesn't start tty"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by Daddyo-613 on 2010-06-06
**The Problem:** I just upgraded to 10.04 from 9.10. I want to use the latest nVida driver for my card. Using System> Administration> Hardwar Drivers won't let me activate proprietary drivers. It tells me I don't have permissions but it's a stand alone machine just for me. Normally, I would just open a "tty" terminal "Ctrl + Alt + F(n)" and stop the gdm service and manually load the driver but I can't seem to open a tty terminal.

Have they changed something in 10.04? The answer should be pretty simple. Can anyone help?

**My System:**
OS: Ubuntu: Lucid 10.04
Gnome: 2.30.0 (Ubuntu 2010-03-31)
Kernel: 2.6.32-22-generic-pae
CPU: Intel Core2 Quad @2.40GHz
Video Card: nVidia GeForece 8600,GT
Driver: nVidia 173 but I want to install nVidia - Driver 195.36.15

---

### Post by Daddyo-613 on 2010-06-06
It turns out that I had logged onto my X session in failsafe gnome so the System> Administration> Hardware Driver, functionality was disabled. I logged back on in a full gnome session and I was able to update my driver using the Hardware Driver GUI.

But I still can't get a TTY terminal to open. Can someone tell me how to do it and while you're at it can someone also tell me why no one but me seems to read my threads or respond. Am I doing something wrong or do I have to register with some special secret club or what.

Inquiring minds want to know.

---

### Post by webaake on 2010-06-07
Can't get ctrl alt fn to work either on karmic, nothing happens. ctrl alt del works for the quit menu. getty IS running and sudo chvt N works as well, but not ctrl alt fN. Did work before some updates.

---

### Post by Daddyo-613 on 2010-06-07
It works on my office machine that is currently running 9.10. I'm embarrassed to say that I don't recall specifically if I recently used Ctrl + Alt + Fn on the other machine I was referring to in the post above, before I upgraded to 10.04. The method of accessing TTY level terminals however clearly works in 9.10.

I'm sure that there's some WIKI somewhere that would tell us how to start a TTY in 10.04.

Anyone?

---

### Post by Daddyo-613 on 2010-06-12
bump

---

### Post by webaake on 2010-06-12
Silly solution here: I switched USB ports for the keyboard and ctrl+alt+f1 works again! Might worth a try!

---

### Post by FuturePusher on 2010-06-12
Hi guys... another "sufferer" here ;)


In webaake's case, I suspect he boots with a USB keyboard connected as primary keyboard (I'm using a PS/2 keyboard)...
What happens when he disconnects it after bootup, and reconnects it in _any_ USB port (probably including the "original" port)... is that the driver used for USB keyboards is switched (to one with further key layout support), and consequently; function keys (& possibly other) which didn't work earlier, now works.
(At bootup, the kernel handles important/relevant hardware drivers, USB keyboards included usually... Distributions loaded on top of the linux kernel nowadays often load more capable drivers though, _unless_ as in this case the "boot" USB keyboard remains attached I guess - thus a driver change when disconnected and reconnected.)


**As for this thread's OP + most others posting:**

Has something changed in Ubuntu 10.04...?
OOOH yes, have things changed or what!?

To adress this threads specific issue:
I feel pretty certain You're having framebuffer issues...

The TTY consoles usually run on top of a framebuffer subsystem;
First, the kernel needs to run a properly functioning framebuffer driver (a commonly used for many is VESA framebuffer ("vesafb") (or well, _was_ due to changes in the newer GRUB (Grub2) bootloader.. there's some suffering to be had right there!)
Secondly, the kernel must properly activate the framebuffer console system ("fbcon"), quite dependent on a functioning framebuffer driver as described just earlier.

**So, to make this long story even longer:**

You probably have the kernel-built-in "EFI" framebuffer driver activated, as opposed to the better (IMHO) "VESA" framebuffer...
(Open "/var/log/dmesg" in a text editor, for instance, and search the entire log text for "efifb:" (no quotes)... if You get search matches, You have this plague... You can also check the file "/proc/fb" and see if You've got "EFI" in there.)

For an explanation as to why the "EFI" framebuffer driver is annoying the heck out of me... contrary to the "VESA" framebuffer, it doesn't seem as compatible with Nvidia (and possibly ATI) graphics hardware... in my case resulting in color artifacts on the TTY consoles, and less resolution compatibility.

In Your case, the "EFI" framebuffer probably initiates a graphics mode it "thinks" everything can handle, but obviously can't... so You get completely "invisible"/black consoles. In other words, only You as humans interfacing with the machine see something's wrong, while the system "thinks" everything is OK... and thus, You may actually _have_ working TTY consoles...(!) it just doesn't look like it, so to speak.

What can You do?
Well, I wouldn't threaten the Ubuntu developers with cow dung to sort things out, since this problem is something for the EFI framebuffer kernel developer (not working with Ubuntu specifically), Grub2 developers and the developers behind "Noveau" & Nvidia proprietary drivers (and possibly ATI related drivers) to handle.

However, maybe some Ubuntu developers or enthusiasts can figure out a circumvention solution to this...
So have hope, keep getting Your issues heard/seen... and wait a little.

Or if You have the know-how; try what's needed to instruct the EFI framebuffer driver to use a graphics mode, out of all available, that _IS_ compatible with Your graphics hardware.


In any case... You have my sympathy in Your suffering (it really is suffering!).
Personally, I will stick with my Ubuntu 9.04 (Jaunty Jackalope) until 10.04 seems _really_ solid... as this version seems to be the last one to _not_ introduce new graphics related issues to earlier well-functioning setups.

---

