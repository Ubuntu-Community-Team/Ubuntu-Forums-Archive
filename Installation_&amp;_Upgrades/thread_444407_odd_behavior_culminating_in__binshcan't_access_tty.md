---
title: "odd behavior culminating in  /bin/sh:can't access tty;"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by Gogonov on 2007-05-15
I't been a long process so far but i'm sticking with it.  I have an hp dv5218 laptop and a western digital external 160gb my book drive.  The laptop has xp home with an ntfs file system.  The Wester Digital external has the ext3/swap partition on it.  At first I kept getting grub error 21 at boot.  I fixed this by setting the bios boot delay to 10 seconds.  This gave the Wester Digital time to be recognized before the grub loader looks for it.  But now i have an odd problem which has caused me to reinstall 6.06 3 or 4 times now.  If i run ubuntu and shutdown no problem.  I turn on again and choose ubuntu still no problem.  I'll shutdown again.  If on power-up i choose windows xp, windows loads ok.  But now when i shutdown and restart, it is possible for windows to load but ubuntu gives me error->  /bin/sh:can't access tty;   It only does this after i've shutdown from windows and on the restart.  If i shutdown from ubuntu, it'll start right back up in ubuntu.  So each time i run windows, i've had to reinstall ubuntu.  What is this?

---

### Post by jerrylamos on 2007-05-16
You may get some more information if you do Applications, Accessories, Terminal, sudo gedit /boot/grub/menu.lst (where l is lower case L).  Look for the first line that starts "kernel" and ends with "quiet splash".  Delete the word "quiet".

This should give you tons of messages as Ubuntu starts up, including some rather harmless messages.  Do your best to see if there's some useful error message you can post here.

Puzzled, Jerry

---

