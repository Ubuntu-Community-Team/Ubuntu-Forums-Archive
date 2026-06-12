---
title: "Big problem on feisty upgrade"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by burakerenn on 2007-09-24
I made dist-upgrade last night. But it haven`t been succeeded. It always gave me error like this:

invoke-rc.d: initscript bluetooth, action "stop" failed.

It`s not specific about bluetooth or action `stop`. If I stop bluetooth by deleting bluetooth script in /etc/init.d, then it gives me initscript dbus, action `start` failed.

Now I can`t make my ubuntu work. Any idea about how to override this problem?

---

### Post by jnorthr on 2007-09-24
you could try to reboot using the 'recovery' kernel version which avoids starting a lot of drivers and just gives you a minimal set, then use dmesg to look for kernel error messages near the bottom of the list. If you have grub (or lilo?) as a boot manager, you should see the -recovery choice on that first menu just after you power on and re-boot.

---

### Post by burakerenn on 2007-09-24
Recovery choices and old kernels don`t work too. Well it`s normal cos I have too much lib files, which are not loaded yet. Dist-upgrade stops because the problem I have said before. I must override that invoke-rc.d problem to make a clean dist-upgrade. After clean upgrade I`ll be able to start my ubuntu.

But why that stupd initscripts give that error??:confused::confused::confused:

---

