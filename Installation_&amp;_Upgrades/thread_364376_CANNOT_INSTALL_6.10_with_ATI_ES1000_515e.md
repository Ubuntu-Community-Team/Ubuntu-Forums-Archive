---
title: "CANNOT INSTALL 6.10 with ATI ES1000 515e"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by gian on 2007-02-18
Hello,

I am not able to install Ubuntu 6.10 on my PC with an ATI ES1000 515e video card.

Tried:

1. safe graphics install
2. VGA
3. 1024x768x16
4. 640x480x16

When the system boots, the display flickers and is unusable.
I can install Dapper, although the video card is not recognized.

thanks for your time and advice...

-Gian

---

### Post by SPPaintball on 2007-02-18
I have the same problem with my 7800GT.

It acts like it's going to boot, but when it gets to the Ubuntu splash screen it's covered in artifacts and the system freezes there.

---

### Post by willc0de4food on 2007-02-18
when it first goes to the livecd before booting and you're at the boot options screen, press F6 with the default selection (start or install ubuntu), and backspace everything through splash and quiet
as it boots you'll now see what's going on. if there's errors, could you post them? otherwise see if it drops you to a command line.
also, does pressing ctrl+alt+F1 bring you to a command line?
you may need to manually edit the xorg.conf file to use a different driver from the default one (i've had to do this ever since 5.03 w/my ATi video cards)

---

### Post by gian on 2007-02-18
willc0de4food,

thanks for your kind reply.

I did not spot any error (browsed dmesg), and yes, ctrl-alt-F1 gets me to the command prompt.

-G

---

### Post by gian on 2007-02-18
I have added break=bottom to the F6 command line, and now I can see where it hangs:

BusyBox v.1.1.3 Debian ... Built-in Shell (ash)...
.....
/bin/sh: can't access tty; job control turned off
(initramfs)

---

### Post by gian on 2007-02-18
this is Dapper working xorg.conf:

---

### Post by gian on 2007-02-18
the only difference between the Dapper/Edgy xorg.conf is in Section "Device", driver "vesa" / "ati".

Changing Edgy xorg.conf to Dapper's doesn't make it work...

---

### Post by gian on 2007-02-21
somehow, I managed to have a successful install.

I opened a console with Ctrl-Alt-F1, then
sudo su nano /etc/X11/xorg.conf
changed driver from "ati" to "vesa"
sudo shutdown -r now

Surprise ! the desktop came up correctly and I could install Edgy.

---

