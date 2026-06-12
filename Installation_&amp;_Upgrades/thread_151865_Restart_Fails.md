---
title: "Restart Fails"
date: 2006-03-28
forum: Installation &amp; Upgrades
---

### Post by mnl88 on 2006-03-28
I tried to install Ubuntu 5.10 (32 bit version) on my machine (Athlon 64 3500+).  Everything looked to be going well, as I installed the copy of Ubuntu on my second hard drive.  GRUB installed successfully (or so it claimed), and finally I was prompted to restart the machine.  I did so, and Windows loaded, with no option whatsoever to get into Ubuntu and continue my installation.  I got no error messages throughout the install, and really don't know what went on.

Any ideas?

(As a side note, I had previously tried installing the 64 bit version, and the GRUB process failed altogether.  No error messages, the progress bar simply never got past 0%.  Again, I'm in the dark.)

---

### Post by zovres on 2006-03-28
It seems that wherever GRUB gets installed is not what the bios looks for when it boots the OS.
You can try telling grub to install on the MBR or the first track of the first hard drive (something like that). Or change your settings in the bios to make sure that it loads the place where Grub has been installed.

---

### Post by mnl88 on 2006-03-28
I told GRUB to install on the MBR, and the bios is set to look to the hard drive first.  I still don't get why GRUB doesn't start up...the computer loads the MBR first, right?

EDIT: Problem solved, thanks.

---

### Post by zovres on 2006-03-29
just out of curiosity how did you solve it? :)

---

### Post by uzd4ce on 2006-03-29
I've got the exact same problem.  How'd you fix it?

Uzd4ce

---

