---
title: "Grub Error"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by merlinus on 2012-04-27
After what seemed like a successful install of 12.04, upon rebooting this error message appears with a grub rescue prompt:

the symbol 'grub_xputs" not found

---

### Post by zdeuyo on 2012-04-27
> **merlinus said:**
> After what seemed like a successful install of 12.04, upon rebooting this error message appears with a grub rescue prompt:

the symbol 'grub_xputs" not found

Hello,

Please visit this thread,

Link:[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Please let me know if this solves your problem.

All the best.

---

### Post by mvampire on 2012-05-05
I have the same problem.

Such problems are completely unacceptable. First, when I tried to upgrade from 10.04 to 12.04, it hanged. And rescue with 'dpkg --configure -a' didn't help (apt-get also couldn't fix packages). As a result the system was broken without any chance to be repaired.

Now, when I decided to make a clean install (and reinstall all programs, restore data and configrations, etc.), it does not even boot!

Is it LTS or what?! WTF?!

---

### Post by mvampire on 2012-05-05
The right solution should be to reinstall grub:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

