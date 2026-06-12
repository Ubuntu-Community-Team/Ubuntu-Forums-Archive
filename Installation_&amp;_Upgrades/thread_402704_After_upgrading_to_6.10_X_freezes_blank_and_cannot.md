---
title: "After upgrading to 6.10 X freezes blank and cannot access console"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by mundus on 2007-04-06
Ok, I'm in a quite a trouble here. I have 6.10 installed but when booting I just get a blank screen. The situation gets worse as Ctrl-Alt-F1 does not take me to console! I have tried to hit ESC during reboot to get to rescue mode but that didn't work either. Neither do I have sshd configured correcly, so that's a dead end also.

So what can I still try to do to get console access and figure out why X isn't working? Can I gain console access using a CD? [http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html#gainrootinstallcd]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html#gainrootinstallcd")

Or do I have to do a re-installation from the CD and just make sure I don't format /home?

Thanks.

---

### Post by mundus on 2007-04-06
Ah, finally got to rescue mode from GRUB. I had to change BIOS settings to use BIOS to support USB-keyboard instead of OS. Now I just have to figure out why X is not starting...

---

### Post by wislon on 2007-04-06
mundus, I ran into the same problem when I upgraded to edgy. check out this thread:

[http://ubuntuforums.org/showthread.php?t=356579](http://ubuntuforums.org/showthread.php?t=356579)

turning off quiet and splash in the grub boot menu for the entry I use let me see what was going on under the hood while it was starting, and I was getting a weird kernel panic not syncing error. using 'acpi=force' in the grub entry for my kernel fixed the problem

---

