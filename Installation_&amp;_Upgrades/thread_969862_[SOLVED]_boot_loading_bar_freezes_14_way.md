---
title: "[SOLVED] boot loading bar freezes 1/4 way"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by tmray on 2008-11-03
I just did a clean install of Intrepid on my dell computer that has a nVIDIA card and after it was installed it shows the kubuntu splash screen and the loading bar gets to about 1/4 of the way and freezes up. I also tried booting in recovery mode and it freezes during the files needed to boot process.

Any ideas what I can do to get it to boot completely?

Thanks

---

### Post by Partyboi2 on 2008-11-03
Try removing the splash screen. When you boot and see grub loading.... press ESC then highlight kernel you normally boot into and press "e" then highlight the line starting with "kernel" and press "e" again then remove the word "splash" then press "enter" then "b" to boot.
Hopefully this will give some more info on where it is freezing.

---

### Post by tmray on 2008-11-03
after doing this it stops at this line:

init: rc-default main process (2403) killed by SEGV signal

---

### Post by Yumi on 2008-11-03
I had the same problem when my USB stick was plugged in. Removing it and the loading bar went on as normal.
Michael

---

### Post by tmray on 2008-11-03
Yumi I don't have a usb stick plugged in but that got me to thinking. It seemed like it was hanging up while loading peripherals so I unplugged them one by one and booted. Turns out it was my wacom tablet I still had plugged in that was causing it. duh :oops:

So now it's running. but I had to load it using the integrated video card. Now I just have to fix the nVIDIA card and then set up the wacom tablet.

Thanks for the help.

---

