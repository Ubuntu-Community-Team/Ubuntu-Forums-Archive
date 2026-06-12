---
title: "Kernel panic"
date: 2018-01-14
forum: Installation &amp; Upgrades
---

### Post by fattyz on 2018-01-14
Hi, I stuck my old HDD in my new Dell Inspiron and got it working on dual boot by switching between legacy and UEFI boot.  They in an effort to get wifi working I found this, [https://askubuntu.com/questions/657774/how-to-get-my-intel-wireless-3165-to-connect-on-15-04](https://askubuntu.com/questions/657774/how-to-get-my-intel-wireless-3165-to-connect-on-15-04) and followed the instructions to update the kernel.  Then I tried to update the drivers and everything becasue the system was crawling, the compiz effects were happening at about a frame a second.  So, i did ubuntu-drivers autoinstall and now I'm rekt.  I tried advanced boot options from grub but got the same thing, kernel panic.  Can I roll back the kernel or should I try something else?  Thanks please help I've been working on this forever and I'd hate to lose it now I'm so close!

---

### Post by RobGoss on 2018-01-14
You mention you're dual booting but you don't say which operating systems you have on this machine

Most likely this was caused by something that was changed in the system

Seems to me rolling back to a early kernel might work but could be just a temporary fix

If you have to switch between UEFI and Legacy, it's probably because you've install  Ubuntu incorrectly that's why you are not seeing the grub menu at startup

---

### Post by fattyz on 2018-01-14
WELL, it was too far gone so after IDK how much work I borked my install with compiz and emerald and now I have to start all over but it was not for lack of trying. It's amazing how much damage you can do with a couple terminal commands.

Thanks,

---

### Post by RobGoss on 2018-01-14
> It's amazing how much damage you can do with a couple terminal commands

Yes you're correct, not knowing what a command can do can be catastrophic and will break any system. You should always run only the commands you feel comfortable with and are aware of what they can do

---

