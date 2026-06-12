---
title: "Grub Error 18 after installing 2.6.17-11"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by neutro on 2007-02-20
Hi all -- I am posting to report a problem but also give the solution, just in hope this helps people in the same situation as mine. I am also curious to see if anyone got that problem too.

I installed the recent update to kernel 2.6.17-11 (ok I'm a little bit late) and rebooted. Grub presented me with choices for the new kernel and the previous one (-10). I selected the new one and got the following error:

```
Error 18: Selected cylinder exceeds maximum supported by BIOS
```

Which is odd since everything was fine before. I found out that the same error was issued when selecting 2.6.17-10. However, both kernels booted fine in recovery mode. This is especially odd since the only difference between a normal kernel entry and the recovery mode entries is the added "single" kernel option.

Moreover, booting in recovery mode, I could see that the only difference between my old /boot/grub/menu.lst file and my new menu.lst file was the addition of the new kernel stanzas.  Using the old menu.lst file (which only lists kernel 2.6.17-10), I was able to boot normally!

The solution to this highly incomprehensible situation was somewhat simple however: I just  re-installed Grub (grub-install /dev/hda if your boot disk is hda), and everything was fine afterwards.

I don't know what would have caused this problem (maybe the fact that I edited the menu.lst file manually, for instance in order to change the default selection?) but for sure, if that happened to a few of my friends, needless to say, the Ubuntu experience would have been over for them...

---

### Post by truck87bp on 2007-02-20
I had to change my Ribbon cable to the fine wires from the MoBo to the HD, and that took care of the problem.

---

