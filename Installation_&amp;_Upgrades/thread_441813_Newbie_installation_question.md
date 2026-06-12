---
title: "Newbie installation question"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by SixStringSW on 2007-05-12
I know DOS/Windows well, but I'm fairly new to Linux.

I tried installing the Ubuntu server from the CD image.  It seemed to install fine, but I get a "GRUB 1.5 loading" message followed by an immediate reboot (ad infinitum). I'm re-building an old box: K6/550, 40gb drive, 384MB ram.  I noticed Ubuntu ignored my partitioning request (100mb mounted at /boot, 8gb at /, and 30gb at /home): it put everything back into /media/....

So, on advice from a friend, I gave up on Ubuntu and burned the Xubuntu 7.04 Desktop disc image.  This does not appear to be a bootable disc (at least my PC will not boot from it).  Is the Desktop Installation not bootable?  If not, what image do I need, Alternate?  (And where is it documented)?

Thanks,

Already Frustrated

---

### Post by FuturePast on 2007-05-12
In the first case, that Grub error indicates that grub was not installed/configured properly.

All the installation images should be bootable (how else could you install anything ;)
How did you burn the disc?

---

### Post by SixStringSW on 2007-05-14
I downloaded the iso and burned it with Nero, with validity checking enabled.

I have Windows discs that aren't bootable...they assume you have an installation already and run setup.exe from a command line.  I was worried that this might be similar.  Guess I'll try re-doing the whole process.

---

### Post by newlinux on 2007-05-14
Try burning a very slow speed as well...

---

### Post by SixStringSW on 2007-05-15
Okay, I downloaded again and burned with Roxio, and this disc boots.

New problem (sigh): I get an error "Failed to start the X server."  Following up on that, I find an error: "No screens found."

After that, the install seems to continue, but it appears as though it thinks the GUI is up and running, but all I have is the text screen.  I can hit <enter> to add blank lines, but there's no command prompt or anything. If I <ctl><alt><del>, it goes through the standard Linux shutdown process, so I think it's waiting for me to interact with the GUI.

---

