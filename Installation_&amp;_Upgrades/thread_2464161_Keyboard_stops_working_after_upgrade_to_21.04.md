---
title: "Keyboard stops working after upgrade to 21.04"
date: 2021-06-25
forum: Installation &amp; Upgrades
---

### Post by zeezam on 2021-06-25
Hello,

Installed Ubuntu on my Pi 4 Model B via Raspberry Pi Imager.

Everything works fine until I upgrade to 21.04, then keyboard stops working after I sign in.
Mousepad still works. I'm using a Logitech K400 keyboard with bluetooth usb adapter.

Tried sudo *apt-get install xserver-xorg-input-all* but same problem remains. Also tried removing first with --purge.
If I reinstall Ubuntu - everything works fine until upgrade.

Anyone who ran into this kind of problem and was able to solve it?

Maybe running an old version Ubuntu is the solution but then the graphic driver causing wrong resolution.

Cheers.

---

### Post by monkeybrain20122 on 2021-06-25
Are you on Wayland? Try to log into the xorg session (choose this from the login screen) and see if it makes a difference.

---

### Post by MAFoElffen on 2021-06-25
Did it do a kernel update?
```
uname -a
```
Can you still see it in the USB dev's
```
lsusb
lsusb -t
```
If you interupt the Grub Menu, select other, and use an earlier kernel does it work?
On other, what Graphics Server are you using? Xorg or Wayland?

---

### Post by zeezam on 2021-06-26
> **monkeybrain20122 said:**
> Are you on Wayland? Try to log into the xorg session (choose this from the login screen) and see if it makes a difference.

It works with xorg session :)
It's now default. I can just use Ubuntu xorg session instead of Ubuntu?

Thank you!

> **MAFoElffen said:**
> Did it do a kernel update?
```
uname -a
```
Can you still see it in the USB dev's
```
lsusb
lsusb -t
```
If you interupt the Grub Menu, select other, and use an earlier kernel does it work?
On other, what Graphics Server are you using? Xorg or Wayland?

I havn't tested this yet. Seems to work now with xorg so I maybe not need to do this.
There is no grub on raspberry pi. It doesn't boot that way.
See my answer above for Xorg/Wayland.
Thanks.

---

