---
title: "[SOLVED] Safe to uninstall old kernels?"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by Fernanddo Saenz on 2008-11-30
Hello,
I have a Dell Vostro 1000 laptop running 8.04 (dual boot with XP). My grub menu has grown a bit long now, since it has all kernels since 2.6.24-16, including -18, -19, -21 and now runs 2.6.24-22. Question is: Can I safely uninstall everything related to kernels -16, -18, -19 without thrashing anything? I'd like to keep just the previous kernel, besides the current. Counting the linux-headers, generic kernel, restricted modules, etc., they're taking up 515MB. I'd like to clean up a bit since I have only 40GB for Ubuntu
Thanks

---

### Post by NumPy on 2008-11-30
...indeed it is safe, as long as you need not boot to the old ones.

---

### Post by logos34 on 2008-12-01
You can uninstall the old ones using synaptic.  Next, clean up grub
[B]
gksudo gedit /boot/grub/menu.lst[/B]

edit kernel options line:

> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
[COLOR=Red]# howmany=1[/COLOR]

[COLOR=Red][/COLOR]Then

[B]sudo update-grub

[/B]The old entries should be gone.

---

