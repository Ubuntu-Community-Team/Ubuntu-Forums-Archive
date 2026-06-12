---
title: "FrameBuffer Boot Bug Fixed"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-10-16
Ya :)

We now can use high resolution vesa framebuffer modes during the kernel boot and in tty sessions.

---

### Post by scradock on 2008-10-16
> **Nullack said:**
> Ya :)

We now can use high resolution vesa framebuffer modes during the kernel boot and in tty sessions.

And the way to do this would be?????

?putting vga=791 or something similar in the boot line of menu.lst?

?hand-crafting a config file?

?making a choice from a list in a configuration utility?

....?

---

### Post by FuturePilot on 2008-10-16
Yes, how can I do this now?

---

### Post by Nullack on 2008-10-16
add vga= to your kernel boot command line with the value you want.

For me, I use

kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=blahblah ro quiet vga=0x31B

To get 1280x1024 24bit colour

---

### Post by FuturePilot on 2008-10-16
> **Nullack said:**
> add vga= to your kernel boot command line with the value you want.

For me, I use

kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=blahblah ro quiet vga=0x31B

To get 1280x1024 24bit colour

Thanks. Would you happen to know the one for 1280x800? Or is it limited to certain resolutions?

---

### Post by autocrosser on 2008-10-16
Yes--that part of it is fixed (finally), but you still can't use "splash" instead of "quiet splash"--That part of it is still a regression...I would really like to be notified via boot text whilst in usplash......

---

### Post by Nullack on 2008-10-16
Futurepilot google is your friend with vesa framebuffer mode tables

---

### Post by FuturePilot on 2008-10-16
Ah yeah found it. Apparently wide screen isn't supported. I'll try the other ones though. :)

---

