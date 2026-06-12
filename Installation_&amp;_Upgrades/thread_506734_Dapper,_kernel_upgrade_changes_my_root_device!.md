---
title: "Dapper, kernel upgrade changes my root device!"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by garton on 2007-07-22
I have a dapper installation that works perfectly fine in every way except one: each time there's a security update and I get a new kernel from automatic updates, my root device in grub is changed.

This is how it looks in /boot/grub/menu.lst

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

And every time I have to go in an manually change hda to hde, since that's my root device, so that it looks like this instead:

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hde1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

This machine is a home server and does not have a screen or a keyboard. I'm getting sick and tired of having to carry a monitor and a keyboard into the small room where this machine sits, plug things in and manually edit menu.lst.

Why does this happen? Is there any way I can fix this so that /dev/hde1 is the root device each time a new kernel gets installed?

---

### Post by 5-HT on 2007-07-22
Yup, just make sure that hde1 instead of hda1 is listed in the kopt line nearish the beggining of your menu.lst (default kernel options for update-grub script).
cheers,

---

### Post by garton on 2007-07-22
Thanks! I'll try that and see how it works out in the next kernel upgrade,

---

### Post by 5-HT on 2007-07-22
No need to wait! You can always run 'sudo update-grub', and either 1)take a look at your menu.lst or 2)reboot to see if that does the trick.
cheers,

---

### Post by louieb on 2007-07-22
Also check your **groot** statement in the automagic section. That sets the GRUB root.

---

### Post by garton on 2007-07-22
> **5-HT said:**
> No need to wait! You can always run 'sudo update-grub', and either 1)take a look at your menu.lst or 2)reboot to see if that does the trick.
cheers,

That did indeed seem to work fine! Thank you very much.

---

