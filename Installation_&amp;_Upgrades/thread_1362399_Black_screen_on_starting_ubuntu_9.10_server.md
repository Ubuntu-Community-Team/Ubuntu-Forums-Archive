---
title: "Black screen on starting ubuntu 9.10 server"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by peverix on 2009-12-23
Hello

I'm now trying a few days to install a ubuntu 9.10 server on a embedded miniITX board with intel Celeron M and intel i915 chipset.

The installation itself goes without any problem but after reboot for the first time into the new installation i always get the same symptoms : booting , see message the filesystem is clean and than the screen goes away , with message "no signal from monitor".

Strange because i just installing a text base system , no x or whatever.

Anyone an idea what going wrong ?

Regards
Peter Everix

---

### Post by peverix on 2009-12-23
Found self something , when booting the same disk on another board its booting and working.
But i see the font is changing to some graphic text mode.
The strange is this board is with same chipset / cpu .

How can i  disable this text mode and use normal commandline font ?

---

### Post by prshah on 2009-12-23
> **peverix said:**
> after reboot for the first time into the new installation i always get the same symptoms : booting , see message the filesystem is clean and than the screen goes away , with message "no signal from monitor".

It is probably because your monitor (not an Ubuntu error message) cannot handle a particular refresh rate for a particular text mode. You can change this default mode by specifying it as a kernel parameter.

To find the correct kernel parameter, add the kernel option "vga=ask" to the end of the kernel boot line during the grub bootup screen. 

To do it temporarily (recommended): Press esc to enter the GRUB menu (during bootup); scroll to the usual booting option, but press "e" instead of enter. Scroll down to the second (?) line (the one that starts with "kernel") then press "e" again to edit it. At the end of the line, add a space and add any **one** of the following phrases
```

vga=771
``` == OR == ```

vga=ask
``` 

then press enter; then "b" to boot.

If you find that it solves your problem, post back for advice on how to make it permanent.

"ask" will give you a list of modes usable in text mode. Choose a suitable mode and see if it solves your problem, otherwise reboot and then select another mode. You do not necessarily have to match the selected mode to your specific resolution; you can try (at your own risk!) them in line until you hit a suitable one (771 works in almost all cases).

---

### Post by peverix on 2009-12-23
hi

yes i found this on several places on the internet.
But i installed with grub2 and this vga=771 seems not supported anymore with grub2 because it gave some error.

I now doing a new install and will choose grub-legacy at setup.

Regards
Peter

---

### Post by peverix on 2009-12-23
Hi again

With some googling i found how to fix.
I need to change quit splash with quit nomodeset and then my system started just fine on the new board.

Now i'm searching on how to makes those changes pernament because grub2 change in this way

Regards
Peter

---

