---
title: "Terminal screen garbled"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by Binraider666 on 2010-04-04
Hello Ubuntu community!

I am a new user, previously (fought) used Fedora, Windows XP & 7, and so far I am most impressed by Ubuntu's (relative) ease of installation.

I had a few minor grumbles with my soundcard (M-audio Audiophile 2496) and 3d-acceleration (ATi Radeon 5850) but they seem to be resolved thanks to some forum searches. Getting on to the point: 

When I swap to a terminal session (Ctrl-Alt-F1), I have no idea why, but when I do so the screen is horribly garbled. Occassionally the system crashes entirely (with no visual feedback) and reboots. Yet I can use XOrg with no problems, 3d-acceleration, etc. all working.

Is there something simple I can do to maybe change the screen mode that the terminal is trying to use to get around this? I had a play about with /boot/grub/grub.cfg adding vga=791 or similar, but this makes little/no difference.

Thanks

---

### Post by earthpigg on 2010-04-04
have you tried disabling compiz first?

> metacity --replace

***then*** do ctrl+alt+f_

---

### Post by Binraider666 on 2010-04-04
Just tried that, got the same problem I'm afraid.

---

