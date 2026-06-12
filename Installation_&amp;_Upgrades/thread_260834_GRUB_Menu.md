---
title: "GRUB Menu"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by acmethunder on 2006-09-19
I have been using Ubuntu for about 2 months now and I am still trying to get used to it.

I just ran an upgrade today, which upgraded the kernel.  Why is there still an option for the previous kernel in the GRUB menu, and can I get rid of it?  (if so how?).

What is the reason to having the option of a previous kernel in the boot menu?

Thanks.

---

### Post by tjvdberg on 2006-09-19
You can remove it by removing the old packages with synaptics. And edit the grub menu.lst file
 ```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by NetworkGuy on 2006-09-19
> **acmethunder said:**
> What is the reason to having the option of a previous kernel in the boot menu?

Having the old version of the kernel still available allows you a safety net in case the new kernel "breaks" something. The old kernel gives you something to go back to that you know was working, instead of having a dead system or piece of software.  It's always a good idea to have at least one kernel back from the current available just for emergencies.  If you are sure everything is working fine and you are short on disk space, then you can remove the older kernel from your system.

---

### Post by bulldog on 2006-09-19
If you want advice,don't remove them to soon.

It's really handy when you can't boot the newest kernel,by what reason,you can return to a previous kernel.

If you are absolutely sure you want to remove them you should do so,but another option could be to comment # them,so they are invisible when you boot.

I would leave them there.

This is an example why an older kernel could be handy,

[http://ubuntuforums.org/showthread.php?t=260723](http://ubuntuforums.org/showthread.php?t=260723)

Just think before you do :D

---

