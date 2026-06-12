---
title: "Logitech Dinovo BT KB and and mouse"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by manutremo on 2006-06-02
Hi!

I have a Logitech Dinovo Bluetooth keyboard and mouse. I used to use them on Breezy and went ok.

On installing 6.06 I find that as soon as I reach the login screen, they stop working.

I have also tried to install Breezy and then upgrade to Dapper... somewhere in the middle of the upgrade, they also stop working.

Is there something to do with this? Some issue with the bluetooth support on Dapper?

Thanks!

---

### Post by jjeremia on 2006-06-02
I have the same set and it is working all fine. The only thing that I have to do is that I need to unplugg the base from the USB and put it in again when gdm loads.


jjeremia

---

### Post by manutremo on 2006-06-02
[QUOTE=jjeremia]I have the same set and it is working all fine. The only thing that I have to do is that I need to unplugg the base from the USB and put it in again when gdm loads.
[/QUOTE]

Thanks

But do you have to do that every time you boot to gdm or just the first time?

---

### Post by wintermuteNYC on 2006-06-05
I too have the DiNovo Bluetooth keyboard, and find that it does not work with Dapper Drake.

Anyone solve the issue for good?  Is it a problem with USB or with Bluetooth?

---

### Post by manutremo on 2006-06-05
Just uninstall the bluez packages and the Dinovo works fantastic!

---

### Post by roufneck on 2006-06-06
[QUOTE=manutremo]Just uninstall the bluez packages and the Dinovo works fantastic![/QUOTE]

You mean all the bluez packages including libbleutooth1? Doesn't this remove bleutooth support. I have to be sure because I can try this only once. I don't have a spare keyboard and mouse at the moment.

I have the same gdm loading problem with logitech bleutooth mx keyboard and mouse.

---

### Post by roufneck on 2006-06-06
Never mind, I thought I just try it.

Removing every bluez package except libbluetooth1 did it for me. Ubuntu is starting up without the need to unplug the usb bleutooth hub for a second. =D>

Thanks a lot...

---

### Post by wintermuteNYC on 2006-06-06
is the problem with buggy Bluetooth packages themselves?  Or is it a configuration issue with the keyboard/mouse not being set up properly?

In other words, can I disable bluetooth, boot into Ubuntu, re-enable bluetooth, configure the keyboard/mouse in the bluetooth module, then reboot and use as normal?

Does it need a pin key or something, and that is causing it to fail?

Or is it just plain broken and won't work until the Bluez module is fixed?

---

### Post by roufneck on 2006-06-07
It could be the pairing or the fact that linux sees my hub as a usb device and not as a bleutooth hub. Or my lack of linux experience ;)

A way to configure the keyboard and mouse with pairing I found here: [http://linux.yes.nu/diNovo/?Page=cGFnZTAx](http://linux.yes.nu/diNovo/?Page=cGFnZTAx)

I have seen a few reaction that they got it working.

---

### Post by wintermuteNYC on 2006-06-08
When I tried to remove bluez-utils, it wanted to remove gnome-desktop as well.

I tried to turn off bluetooth in /etc/modprobe/aliases by changing the word "bluetooth" to "off", but that did not help.

---

### Post by manutremo on 2006-06-08
[QUOTE=wintermuteNYC]When I tried to remove bluez-utils, it wanted to remove gnome-desktop as well.[/QUOTE]

Don't worry, gnome-desktop is only a "virtual" package, it's not going to uninstall the desktop or anything.

Only problem is that some other packages will install it again, and then it will install bluez again, so you'l have to remove it (again) :D

---

### Post by roufneck on 2006-06-09
It wanted me to uninstall ubuntu-desktop. In the description it sais that it is not neccessary. And untill now I don't have any problems with it.

---

### Post by xodeus on 2006-06-09
I've a similar problem, but just with a normal cordless Logitech mouse and keyboard.
[http://www.ubuntuforums.org/showthread.php?t=189274](http://www.ubuntuforums.org/showthread.php?t=189274)

---

### Post by FritzThePirate on 2006-06-29
If you want to disable bluez without having to uninstall the metapackage ubuntu-desktop you can use this command in the terminal
```
sudo update-rc.d -f bluez-utils remove
```
It will stop the bluez-utils package from loading at boot, and will thereby stop the random problems it seems to cause with the dinovo.

---

### Post by pwlodarczak on 2006-09-29
I have a similar problem with the diNovo keyboard. When I reboot Ubuntu only the mouse would connect. I have to unplug the bt dongle, then the mouse and keyboard are reconnecting. I edited the
/etc/default/bluez-utils to autoconnect as proposed in a closed thread but it still wouldn't autoconnect the keyboard. Any ideas?
Peter

---

