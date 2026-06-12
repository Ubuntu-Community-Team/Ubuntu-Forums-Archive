---
title: "Xorg loads wrong driver"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by grshorwich on 2009-11-19
Using Karmic Koala.

Graphics adapter = ATI Radeon 9200SE (RV280 chipset).

Like several people if a search on the net is anything to go by, I have been experiencing total lock-ups as soon as anything requiring OpenGL is started, but not always, which makes it rather infuriating to troubleshoot...

In the absence of a /etc/X11/xorg.conf file, Xorg tries to detect the graphics chip and load the appropriate driver automatically, and this is where the problem lies. Xorg is loading the "ati" driver for this card when it should be loading the "radeon" driver.

Create a barebones /etc/X11/xorg.conf file containing this, which is based on Xorg's default built-in configuration with just the name of the graphics driver changed:

```
Section "Device"
        Identifier "Builtin Default ati Device 0"
        Driver "radeon"
EndSection

Section "Screen"
        Identifier "Builtin Default ati Screen 0"
        Device "Builtin Default ati Device 0"
EndSection

Section "Device"
        Identifier "Builtin Default vesa Device 0"
        Driver "vesa"
EndSection

Section "Screen"
        Identifier "Builtin Default vesa Screen 0"
        Device "Builtin Default vesa Device 0"
EndSection

Section "Device"
        Identifier "Builtin Default fbdev Device 0"
        Driver "fbdev"
EndSection

Section "Screen"
        Identifier "Builtin Default fbdev Screen 0"
        Device "Builtin Default fbdev Device 0"
EndSection

Section "ServerLayout"
        Identifier "Builtin Default Layout"
        Screen "Builtin Default ati Screen 0"
        Screen "Builtin Default vesa Screen 0"
        Screen "Builtin Default fbdev Screen 0"
EndSection
```Save the config file and reboot.

No more lock-ups :)

---

### Post by aftertaf on 2009-11-19
:popcorn:

you don't happen to ahve a way of testing this well, do you?
I have  a T60 with Radeon X1300, which is no longer supported by ATIccc with latest Xserver version...
so now i'm on karmic i have only 2d graphics . .  no more compiz or compositing (afaik).

bit of a downer, actually :(

trying your above fix, but with "radeonhd" as "radeon" changed nothing for me, and the package xorg----radeonhd has the X1300 listed...

---

### Post by aftertaf on 2009-11-19
radeonhd 'works', but the 3dness is all sloooooow
will try to check out why.

---

### Post by grshorwich on 2009-11-19
Could it be because 3D is being taken care of by software rather than by hardware?

Your /var/log/Xorg.0.log might give some indication.

---

### Post by realzippy on 2009-11-19
Your file is messed up completely.Delete it.
Watch out for doubled "device sections" etc.

Something I do not understand is why all people 
complain about the lack of ATI catalyst driver.
Write to ATI.And,why not runnig **8.04  ???????????????**
....where 3D works fine.Can Karmic do anything what I have not found yet?Cook coffee?pay bills?
If I was forced to use an ATI card and had to decide:
Full (ATIlike) hardware acceleration (Intrepid) or EXT4 and Grub2 (karmic)
the answer would be clear.
Any answers?

Edit:
Think it might be a good idea to make kind of fat sticky sign at beginners section concerning
"Old" ATIcards/Catalyst/Do **not** install! 9.04 or 9.10/ **or** RADEON and do not complain.
Not that it is bad reading those ATIoldcard/Karmic/Compiz threads but they are useless.
The only way to make ATI better drivers and "long"-term support is to buy NVIDIA cards, a used
GT 6600 might beat the newest ATI 4XXX card in 3D ...

---

### Post by jmartini on 2009-11-19
Thanks for this. Following the update to 9.10, X was sluggish and Xorg was consuming about 10% of the cpu while idle. Specifying the correct driver in xorg.conf appears to have addressed the issue.

---

### Post by realzippy on 2009-11-19
"Lord knows I've suffered"

---

