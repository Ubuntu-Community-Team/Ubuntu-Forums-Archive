---
title: "[SOLVED] No login prompt - only (initramfs) command line"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by JBD88 on 2008-11-26
XP Media Center Edition w/SP3
Pentium 4 3.2 ghz
2 gb ram

Dowloaded 8.1 and created disk.  Menu came up but when pick Install Ubuntu, it never got passed the command line (initramfs):

Tried the 8.04.1 LTS disk that I had ordered.  This time got to the installer, created partitions, and it installed.  After rebooting, went back to the command line (initramfs).  Never launched.

(by the way, what is the typical file system to setup?  I used a free partition for / and put 4 gb for swap.  no idea if that was right)

So, I can't get it to launch.  Does not even come to the login prompt.

Thanks for help.
Joe

---

### Post by scottmac112 on 2008-11-26
Maybe too much swap space? : ) I usually use between 512 MB and 1 GB.

For a n00b, I would recommend either ext2 or ext3 for the root partition (/).

---

### Post by scottmac112 on 2008-11-26
Maybe too much swap space? : ) I usually use between 512 MB and 1 GB.

For a n00b, I would recommend either ext2 or ext3 for the root partition (/).

---

### Post by JBD88 on 2008-11-27
this sucks.  tried Linux Mint, too.  It does not even show up in the boot menu.  Ubuntu shows, but does not go to login screen, just the command prompt.  I guess I could wipe the whole thing, but kinda wanted to keep Win around until I was used to Linux.

anyone have other ideas?

Joe

---

### Post by forbajato on 2008-11-27
I have not had this problem during the install but have had it once installed and booting for normal use.  Have you tried hitting <ctrl>-d when the command line comes up?

Mine does this during a boot and if I give it a few seconds and hit ctrl-d the boot continues normally.  Best I can tell it is like the hard drive where Ubuntu lives is not quite ready (there is a message about needing to increase something called "boot delay").

It is a minor bug for me since I reboot only rarely (it is Linux afterall!) but is on my "figure this out and fix it someday" list.

---

