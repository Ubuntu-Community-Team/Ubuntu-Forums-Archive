---
title: "Toshiba Portege M750 problems"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by grantg on 2010-05-04
So, I have to use this windows computer for my school, and i hate windows!!  Ubuntu is perfect for me, except that i have to dual boot sometimes to windows 7 for the one application that wont run in a virtual environment (LockDown Browser, and occasionally onenote).  Except, i cant find tablet control features in Ubuntu, to change input devices (the touchscreen is awful, but I cant turn off the option to use finger as an input device.  Also, when i boot to windows 7, the mouse track pad/left and right click doesn't work (they work in Ubuntu)???  The keyboard does, and so does my stylus (which I have to use as a substitute)  Any help would be great!!  Thanks, Grant

---

### Post by Favux on 2010-05-04
Hi Grant,

What version of Ubuntu are you in?  Karmic or Lucid or ?

---

### Post by grantg on 2010-05-05
I am using Ubuntu 10.04 LTS Lucid Lynx.

I posted this after trying to reinstall mouse drivers for my Windows 7 side, which failed after restarting, but magically after a couple more restarts my mouse movement and click functions came back???

Anyway, I LOVE UBUNTU. While Windows 7 informs me that their own Microsoft application has stopped working and "is looking for a solution," Ubuntu just works. Also, my machine has always booted slowly (even after reimaging). Ubuntu flies into action in no time!

My main concern is finding Toshiba tablet drivers, as some of my hardware doesn't work. My google abilities are weak, and I've gotten no where in the subject. I'm new to Ubuntu, so I thought maybe I'm looking in the wrong places? I'd just love to get features like rotating the screen when I go into tablet mode. A point in any direction would be an amazing help.

Thanks!!
-Grant

---

### Post by Favux on 2010-05-05
Hi Grant,

So your stylus works?  How many buttons on the stylus?  Does it have an eraser?

You can turn touch off.  First we need to know what Lucid is calling your Wacom devices.  So in a terminal enter:
```
xinput --list
```
and post the output.

---

### Post by grantg on 2010-05-05
```
grant@grant-laptop:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=14    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                         id=15    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; CNA7157                                     id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
```

My stylus has a right click button and eraser. I don't believe the button on the stylus is configured for right click as all I know it does is close Firefox tabs.

Thanks!
-Grant

---

### Post by Favux on 2010-05-05
OK, the device names have changed.  Here is what I mean:

stylus = Serial Wacom Tablet or 15

eraser = Serial Wacom Tablet eraser or 13

touch = Serial Wacom Tablet touch or 14

So to turn touch off instead of:
```
xsetwacom set touch Touch off
```
which is the old name you would use:
```
xsetwacom set "Serial Wacom Tablet" Touch off

```
Notice you have to use quotes around the device names. Or you could use:
```
xsetwacom set 14 Touch off
```
N-trigs have problems with touch and writing too.  So there are a couple of scripts to toggle touch on and off in "6) Turning touch on and off" in the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

To make the stylus button a right click see "c) Lucid-configuring through 10-wacom.conf" in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Add to the serial Wacom snippet/section:
```
	Option "Button2" "3"
```
like so:
```
Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
	Option "Button2" "3"
EndSection

```
Reboot and you should be good.

---

### Post by grantg on 2010-05-05
That did it! 

Thanks!

Any idea where I might start to be able to rotate my screen?

---

### Post by Favux on 2010-05-05
Hi Grant,

Great!  :)

Sure, the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  A modified method one script should work for you.  Also wacomrotate in method 3.

---

