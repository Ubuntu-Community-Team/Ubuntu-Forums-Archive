---
title: "XP boot fails, as does Ubuntu"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by EdZ^2 on 2006-03-11
I just installed Ubuntu 5.10 onto a second partition of my primary drive, allowing it to install GRUB to my MBR. Upon rebooting, I was unable to boot to linux, getting the old Dev tty error again (had this error when I tried installing to a second HDD and leaving the MBR alone. LiveCD boots fine).
I'm not too worried about getting Ubuntu to work (I've tried before with the same error, and I now have enough spare parts to make a dedicated box), so I attempted to booot back into XP.
Got the splash screen for a few seconds, then the computer restarts. Same in safe mode. I popped in the install CD, and booted to the recovery console and run FIXMBR, then tried to boot again. Grub no longer loads (as to be expected), but XP has the same problem booting (splash screen, then reset).
I then bootedback to the recover console, ran FIXMBR again, then tried FIXBOOT. I get a 'target partition is unknown' error message. I then ran CHKDSK, and got the message 'the volume appears to contain one or more unrecoverable problems'.

Is there any way to fix whatever I've done and get XP booting again, or is a re-install the only thing left (I have a second HDD with most of my ducuments and other files stored on it, but all my programs and settings are still on the primary drive)?

::EDIT:: Tried to mount the windows drive under the 5.10 live CD, but it cannot tell what file system it is (shows the filesystem as 'unformatted', with a size of'84.81GiB (free space not available)'. This is the size my windows partition is/was). My documents drive mounts fine.

---

### Post by EdZ^2 on 2006-03-11
Re-installed XP, but my documents disk is unreadable by XP, though the live cd sees it fine. See [this thread](http://www.ubuntuforums.org/showthread.php?t=142936)

---

