---
title: "Lilo installed with recent update - how to recover grub?"
date: 2009-01-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rockyrobin on 2009-01-18
I installed Jaunty a few days ago but made the mistake with a recent update of following its instructions to configure lilo which came down with the update :/

If anyone could help point me in the right direction to reinvoke grub would be very grateful.

Thanks,

RR

---

### Post by caljohnsmith on 2009-01-18
If Grub wasn't actually uninstalled, the following should work to reinstall Grub to the HDD's MBR so that you can use Grub again:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Note if you have multiple HDDs, the instructions above install Grub to the same drive Ubuntu is on. If you have Ubuntu installed to a different drive than your internal sda drive, and you are instead booting your internal sda drive on start up, you would want to use "setup (hd0)" instead of "setup (hdX)" above. Anyway, how about giving it a shot and let me know how it goes.

---

### Post by rockyrobin on 2009-01-18
caljohnsmith - Thanks for your help. Got grub up and running first attempt with your instructions :)

Appreciated,

RR

---

### Post by caljohnsmith on 2009-01-18
Glad to hear that's all it took to get Grub back again; cheers and have fun with Jaunty. :)

---

