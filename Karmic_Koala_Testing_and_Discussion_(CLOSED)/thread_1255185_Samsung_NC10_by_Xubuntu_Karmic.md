---
title: "Samsung NC10 by Xubuntu Karmic"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jis on 2009-09-01
Here are some of my experiences on using Xubuntu Karmic development version.

I installed by UNetbootin. No encrypted home directory was offered during installation. 

**Blue buttons:**

Volume down, volume up and mute buttons don't work, but you can bind commands "amixer set Master 5-", "amixer set Master 5+" and "amixer set Master toggle" in keyboard settings, respectively.

Display brightness buttons do not work.

Fn-F5 (toggle screen backlight) does not work.

Fn-F9 (toggle Wifi radio) does not work; the respective LED is lit always.

Fn-F4 (toggle display) toggles between NC10's screen and clone mode, where desktop size is adjusted according to highest possible resolution of the external display, so only part of desktop is visible in NC10's screen. With CRT monitor as external display, picture may be in wrong position, wrong aspect ratio and less than optimal frequency; the first two you may be able to fix by tuning monitor settings. Extended display mode can be set by e.g. grandr.

---

### Post by jis on 2009-09-04
Can anyone tell commands to adjust screen birghtness by (in Karmic)?
```
xbacklight -dec 10
``` tells "No outputs have backlight property".

You can set command ```
xset dpms force off
``` to Fn-F5, but any key/mouse event cancels it.

---

### Post by jis on 2009-09-04
Hibernate does not work.

---

### Post by trtrl on 2009-09-11
Updated today (UNR 9.10 alpha):
- Sound up/down/mute work
- Battery status key works
- Brightness keys don't work
- WLAN key doesn't work
- Suspend works, but returns to 'Login screen settings'
- Hibernate works.
- Webcam works
- Couldn't check: wlan, external display, bluetooth

---

### Post by jis on 2009-09-11
Which utility you used to test webcam?

---

### Post by jis on 2009-09-12
Hibernate started to work after latest updates; [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360609](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360609)

Volume keys work automatically after latest updates (by xfce4-volumed daemon).

---

### Post by trtrl on 2009-09-12
> **jis said:**
> Which utility you used to test webcam?

Used Cheese (default installed in UNR).

---

### Post by trtrl on 2009-10-02
Updated today (UNR 9.10 beta):
- Sound up/down/mute works
- Battery status key works
- Brightness keys now work!
- WLAN key doesn't work
- Suspend now fully works
- Hibernate works.
- Webcam works
- Bluetooth works
- Connecting external display and switching to it crashes the OS.
- Couldn't check: wlan.

---

### Post by jis on 2009-10-04
I am using Xubuntu Karmic beta now.

I can switch WLAN radio status LED off by unticking "Enable Wireless" in NetworkManager Applet 0.7.996 (Network Manager). (Right-click the tray icon first.) But if I e.g. suspend to RAM and resume, the LED is on again even though the setting is remembered by Network Manager.

---

### Post by fhr on 2009-10-04
The most interesting source for patches/scripts for the NC10 is here : [https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa) This guy made an incredible work and everything works just by installing his packages, nothing to tune.

However, I don't what will work or not with XUbuntu. I guess the Fn keys will do their job (brightness, etc), but I don't know if the display (status bars, etc) will work.

---

### Post by jis on 2009-10-04
Hard drive spins up/down pretty often, if the computer is run by battery. This is in Xubuntu Karmic, I don't know about the netbook remix.

---

### Post by jis on 2009-10-05
I applied [http://www.voria.org/forum/viewtopic.php?f=3&t=33](http://www.voria.org/forum/viewtopic.php?f=3&t=33) and disk does not spin down that often anymore. However, it sounds like it parks heads once in ten seconds or so. The events are counted in Load_Cycle_Count that can be detected by ```
smartctl -d ata -a /dev/sda |grep Load_Cycle_Count
``` as root.

---

### Post by jis on 2009-10-05
Does your bluetooth work after latest updates? I have used blueman to manage bluetooth, but I can't turn bluetooth on anymore.

---

### Post by jis on 2009-10-05
Oh now I can toggle bluetooth again. I did suspend to RAM and resume. Strange.

---

### Post by ogoun on 2009-10-22
Hi,

may I aks what firmware you guys have installed?

I have 11CA but since the update I don' receive scancodes for brightness up and down.

---

### Post by trtrl on 2009-10-23
> **ogoun said:**
> Hi,

may I aks what firmware you guys have installed?

I have 11CA but since the update I don' receive scancodes for brightness up and down.

I have 11CA with a fresh install, and brightness keys work fine (see also [https://bugs.launchpad.net/bugs/397617](https://bugs.launchpad.net/bugs/397617)).

---

### Post by jis on 2009-10-23
I can't make xfce4-power-manager suspend computer on closing the laptop lid anymore, but gnome-power-manager works better. Maybe I have ruined my system by applying partial upgrades by Update Manager?

---

### Post by ogoun on 2009-10-23
> **trtrl said:**
> I have 11CA with a fresh install, and brightness keys work fine (see also [https://bugs.launchpad.net/bugs/397617](https://bugs.launchpad.net/bugs/397617)).

Thanks,

I tried it out and I'm impressed. Everythin works out of the box, except for Hibernation (it just locks the screen).

---

### Post by jis on 2009-10-23
> **ogoun said:**
> Thanks,

I tried it out and I'm impressed. Everythin works out of the box, except for Hibernation (it just locks the screen).

Which power manager are you using? I am able to hibernate when using xfce4-power-manager.

---

### Post by ogoun on 2009-10-23
gnome-power-manager.

I know this therad is for Xubuntu but it's the only one for 9.10 on a NC10 ^^

---

### Post by jis on 2009-10-23
You could file a bug report against it at [https://launchpad.net/ubuntu/+filebug](https://launchpad.net/ubuntu/+filebug)

---

### Post by ogoun on 2009-10-23
I browsed through launchpad nad found out I had the same problem like this guy: [http://ubuntuforums.org/showthread.php?t=1283702](http://ubuntuforums.org/showthread.php?t=1283702)

Karmic wrote an entry for an encrypted swap in the /etc/fstab (dunno why) and the swap wasn't recogniced.

---

