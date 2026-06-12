---
title: "Ubuntu won't start after changing to 8600GT"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by UnBr34KaBl3 on 2007-12-28
I changed to 8600GT and windows is still working but when i start ubuntu the normal loading screen apears and then it disappears and the screen becomes black. It asks for my login and pw in just plane text on a black background. But I never have the time to write it cuz the keys on the keyboard stops working from time to time and the screen flashes about two times. Then it just starts to write a lot of numbers on the screen and it says something like "to much work for... icq869 or something ,I dont really know, after every suck number. After a while a while it stops with a message at the bottom of the scren, it says END and then it just reboots.

If I start with safe mode I see somethin like a terminal but on the whole screen. Can I type some code or something there that makes Ubuntu to download the drivers to make it work.

I used an Ati X300 graphics card before and I am connectet to the Internet thruogh at wireless USB-adapter if i makes any diffrence.

---

### Post by taurus on 2007-12-28
Try to reconfigure your X server for the new nVidia card with

```
dpkg-reconfigure -phigh xserver-xorg
```
Then, you can reboot from the recovery mode with

```
shutdown -r now
```

---

### Post by UnBr34KaBl3 on 2007-12-28
Thank you works fine now!:)

---

