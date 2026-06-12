---
title: "[SOLVED] Hardy does not complete booting from HDD"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by quimico69 on 2008-11-03
Hello everybody,

I have a problem with Hardy.  Over this past weekend I installed Hardy on an old Dell Optiplex machine (41 GB HDD, 1 GB RAM) and, for some reason, it won't cold boot from the hard drive.  All I get is the GRUB notification that it is starting up (although I don't get a menu to choose the kernel to boot) and then the screen goes black to never come back (even after 1 hour waiting).  Funny thing: if I boot from the installation CDROM and pick "start from hard disk", then it boots normally.  Same thing happened with the Kubuntu CDROM.  The machine previously had WinXP (OEM installed) and did not have any problems booting.   Any ideas?  

Thanks for your attention
Victor

---

### Post by taurus on 2008-11-03
If you want to see the GRUB menu, you need to press ESC (you have 3 seconds to do that).  The kernel should already be highlighted.  Now, hit e to edit it and remove the last two options at the end, quiet splash.  Then, boot it with b and have a look at the output doing boot to see what's wrong with it.

---

### Post by quimico69 on 2008-11-03
OK, I'll try that as soon as I get back home.  Thanx, taurus.

---

### Post by quimico69 on 2008-11-03
OK, did as you said: chose the first kernel, edited the second line and erased "quiet splash". Still hung up.  Noticed that the last line after the initrd stuff was "quiet".  When I erased that, system booted normally, although a little slowly (it's an old machine: 5 yo).

How can I edit the boot menu to permanently get rid that little "quiet" line?  Is this the file /boot/grub/menu.lst?

---

### Post by taurus on 2008-11-03
Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by quimico69 on 2008-11-04
OK, that did it.  THANX

---

