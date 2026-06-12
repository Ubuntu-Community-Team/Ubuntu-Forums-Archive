---
title: "Screen doesn't fit on monitor"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by ginister on 2011-11-20
Hi guys, literally just installed Ubuntu on my new PC!
I've got it all working but the screen doesn't fully fit on. I have no idea what to do! I can't see the toolbars or anything.
Please speak in laymans terms with me, I don't have a clue with anything Linux! Thanks :D

Plus it's a 42" TV from Panasonic that it's on

---

### Post by bluexrider on 2011-11-20
Do you know in fact that your hardware will support a 42" monitor?

---

### Post by MAFoElffen on 2011-11-20
> **ginister said:**
> Hi guys, literally just installed Ubuntu on my new PC!
I've got it all working but the screen doesn't fully fit on. I have no idea what to do! I can't see the toolbars or anything.
Please speak in laymans terms with me, I don't have a clue with anything Linux! Thanks :D

Plus it's a 42" TV from Panasonic that it's on
Okay... So the top and bottom is off the display?

Go to a terminal session, <cntrl><alt><t>... then post the results of
[code}
lspci -vnn | grep VGA
[/code]
Then install hwinfo
```

sudo apt-get install hwinfo

```Then post the results of 
```

sudo hwinfo --monitor
sudo hwinfo --framebuffer
sudo hwinfo --gfxcard
xranr -q

```Then post your /var/log/Xorg.0.log.  

Sounds like you may just need to tweak your DPI settings in the graphics driver configuration file... but I need the info above to be able to recommend what you need, where... to give you instructions.

---

### Post by ginister on 2011-11-21
Will do, just installing it all right now :D Sorry for late reply!

---

### Post by ginister on 2011-11-21
> **bluexrider said:**
> Do you know in fact that your hardware will support a 42" monitor?

Whyever would it not? Seems like a stupid question, I know, but still!

---

### Post by lifeboy on 2011-11-21
Is it not maybe something as simple as adjusting the panasonic's screen settings?  Does it have an auto-set type function maybe?

---

### Post by ginister on 2011-11-21
> **MAFoElffen said:**
> Okay... So the top and bottom is off the display?

Go to a terminal session, <cntrl><alt><t>... then post the results of
[code}
lspci -vnn | grep VGA
[/code]
Then install hwinfo
```

sudo apt-get install hwinfo

```Then post the results of 
```

sudo hwinfo --monitor
sudo hwinfo --framebuffer
sudo hwinfo --gfxcard
xranr -q

```Then post your /var/log/Xorg.0.log.  

Sounds like you may just need to tweak your DPI settings in the graphics driver configuration file... but I need the info above to be able to recommend what you need, where... to give you instructions.

First part: 1:00.0 VGA compatible controller [0300]: nVidia Corporation GF110 [GeForce GTX 560 Ti] [10de:1200] (rev a1) (prog-if 00 [VGA controller])
ubuntu@ubuntu:~$ 
It also says unable to locate package hwinfo

---

### Post by ginister on 2011-11-21
Bump due to being completely stumped! :D

---

### Post by ginister on 2011-11-21
> **lifeboy said:**
> Is it not maybe something as simple as adjusting the panasonic's screen settings?  Does it have an auto-set type function maybe?

At whatever zoom it is at the toolbar is always off screen.

---

### Post by ginister on 2011-11-21
> hal.1: read hal dataprocess 3329: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
31: None 00.0: 10000 Monitor                                    
  [Created at fb.71]
  Unique ID: rdCR.EY_qmtb9YY0
  Hardware Class: monitor
  Model: "Generic Monitor"
  Vendor: "Generic"
  Device: "Monitor"
  Resolution: 640x480@73Hz
  Driver Info #0:
    Max. Resolution: 640x480
    Vert. Sync Range: 50-90 Hz
    Hor. Sync Range: 31-38 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
ginister@Sandy:~$ 
here it is!

---

### Post by bluexrider on 2011-11-22
> **ginister said:**
> Whyever would it not? Seems like a stupid question, I know, but still!
good luck with your stuff

---

### Post by ginister on 2011-11-27
Still need help! I'm running in windows at 1768 x 992 fine

---

