---
title: "Grub problem: Always showing boot menu"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by Farinet on 2012-11-01
Since a while i've a problem with grub: On boot (or also on waking up from hibernate) it always shows up the boot menu. Moreover boot process seems very slow to me (i'm on a - fast! - Samsung 535 u3c with lubuntu 12.10 amd64).

What i did: I tried to tweak following the instructions the '/etc/default/grub' file but it is without any effect - seems like there would be some other script/file overruling that one (but where? And which one? I'm clueless . . .). I tried even to activate the boot sound, cancelling the outcommenting "#" of that line, but nothing. Boot process still is quiet and boots into the grub menu (choice of kernels and memtest as well as recovery options etc.).

Anyone out there has an idea? Thanks in advance.

---

### Post by Bashing-om on 2012-11-01
Farinet; hi ! 

Appears your edits caused grub to default back to the boot menu. How about editing back as to the standard install and carefully editing again ? (always make a backup - prior to editing files)

These links will get you straightened out ...and links to how-tos for lots of grub edits within the links.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Remember:
```
sudo update-grub
``` for any changes to be written !
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

