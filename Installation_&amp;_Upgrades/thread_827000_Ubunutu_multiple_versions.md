---
title: "Ubunutu multiple versions ?"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by jeremydazzo2004 on 2008-06-12
Ok heres the thing i have dual boot setup and i have ubuntu and windows xp pro when the menu comes up in grub to choose the OS i wanna use it shows 4 ubuntu versions it seems like every time ubuntu updates the kernel i get a new one can some one tell me how to get rid of the other ones or should i worry about it so far im not having any problems but im not to big on clutter on my machine. thanks

](*,)

---

### Post by pedro_orange on 2008-06-12
Kernel upgrades.

Remove them from your menu.list if they bother you that much.

```
sudo nano -w /boot/grub/menu.lst
```

Just # out the ones you dont want

---

### Post by jeremydazzo2004 on 2008-06-12
do i take them out what do you mean by # them out

---

### Post by Dale61 on 2008-06-12
Try this:

Go into Start-up Manager (System > Administration > Startup Manager), and click on the Advanced tab.

Limit the number of kernels in the boot menu.
               Number of kernels to keep = 1.

This way works for me, and I have two kernels (-17 & -18 ) installed, but only see one in GRUB.

---

### Post by issih on 2008-06-12
Often worth keeping 2 kernels, that way if an updated kernel happens to throw a hissy fit on your hardware configuration you can just boot the older one instead...Not necessary obviously, just a sensible precaution

---

### Post by jeremydazzo2004 on 2008-06-12
OH thanks guys i understand now i thought it was leaving left over junk but now i understand fully thanks so much for the help
ill keep them i have been having some lockups with the newest kernel so ill try the other two

---

