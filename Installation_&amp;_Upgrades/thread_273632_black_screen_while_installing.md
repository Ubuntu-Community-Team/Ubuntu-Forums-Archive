---
title: "black screen while installing"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by hstokholm on 2006-10-08
Hey..

I have recently bought a new desktop, and I figured I would try to install ubuntu on it... So I found my ubuntu live cd, booted from it, but after the progress bar my screen doesn't recieve a signal... After a while I can hear the gnome startup sound, so I know that the boot process continues, but my screen just stays black.. 

I have tried to boot with the safe graphic settings, but that doesn't make any difference.. So I hope you have any ideas... I guess it has something to do with my ati card, but I have no idea what I could do about it. ](*,) 
My config is as follows:

asus a8 sli, amd x2 4200+, 1 gb ram, ati x1800xt 512mb

---

### Post by Kateikyoushi on 2006-10-08
Try to use the alternate install cd, you can install ubuntu in text mode with it.

---

### Post by herroyuy on 2006-10-08
i have the same problem too... i can hear start up sound... but i can see nothing.. all black on my screen... i'm on acer laptop with ati x700... is it an issue with ati?

---

### Post by pony-tail on 2006-10-09
I have the same issue -
Asus A8NSLI Premium AMD64 4600X2 - Radeon X850XT Pe
Live CD (Dapper64 boots to black screen )
Tried Alternative CD cannot get X to start even using "VGA"
Windows works OK Gentoo 64 works ok but has other issues 
Tried Dapper 64 Kubuntu and Ubuntu (dapper) and Ubuntu64 live
(edgy) no joy.

---

### Post by UKHack on 2006-10-09
Hi,

This is similar to a problem that I had with my Acer Ferrari laptop.

Basically the display card is getting mixed up and is trying to output the display to a secondary monitor (which you haven't got hooked up)

You may want to try editing your xorg.conf file (use Ctrl Alt F1 to get to a console and type sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old to make a backup.

Then type sudo vi /etc/X11/xorg.conf). Press the Insert key on your keyboard so you can edit the file and scroll down to the "Device" section

Add the following lines to the "Device" section:

Code:

Option "CRT2Position" "clone" Option "MonitorLayout" "LVDS, CRT"

Hit the Escape key and press :wq and enter to save the file.

Now switch back to the X window by pressing Ctrl Alt F7 and then press Ctrl-Alt-Backspace to restart X. Hopefully you should be greeted by the login screen. If you are running the Live CD then just press enter here.

If you need to restore your original xorg.conf file then when you are at the terminal type sudo cp /etc/X11/xorg.conf.

Hope this helps,

Andrew

---

### Post by tseliot on 2006-10-09
If you tried the livecd and you were not able to install Ubuntu even when using the Safe Mode:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

If nothing works and the Xserver just crashes, please post the output of the following command:
```
lspci
```

---

### Post by pony-tail on 2006-10-09
Back again -
Worked in "breezy" using "vesa" module

---

### Post by hstokholm on 2006-10-18
Hi im back again...

I managed to install ubuntu but none of the suggested drivers worked... But I am testing if the fglrx driver could start the x-server... I am going to try whem ubuntu is finished updating... 30 minutes left :p

---

### Post by hstokholm on 2006-10-18
It started a x-server, but it says meta when I use fglrxinfo... But atleast gnome is starting :D

---

