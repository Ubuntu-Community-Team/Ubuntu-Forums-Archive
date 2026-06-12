---
title: "Install: Prompt: Yes, XWindows: Nope!"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by maxppp on 2007-02-22
Hi Guys, after doing an internet install, following the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=28948"), all appeared to go well...

However, when i boot i get prompted for my username/password in a cmd prompt, i enter it, type 'startx'. This loads a mouse pointer with a fuzzy black/white hatched wallpaper. Thats as far as it gets, any ideas?

The log, amongst other, gives alot of font registration errors? Its a p3 800 compaq with an intel chipset and onboard everything, if that helps

Much obliged

---

### Post by renzokuken on 2007-02-22
sounds like your xorg.conf is using the wrong driver.

login at the prompt and then type

```
sudo nano /etc/X11/xorg.conf
```

scroll down the file till you see the section

```

Section   "Device"
     Identifier     "your grafix card name"
     Driver         "ati"                  [color=red](i use ati as an example, could be anything)[/color]
End Section

```
(.....also note that the above is simplified, you may have a cuple of other lines in the section but just leave them as they are.....)

well change "ati" or whatever it is to "vesa" 

press Ctrl+X, Y and enter to save and exit.

then try startx again

---

### Post by maxppp on 2007-02-22
I changed to

```
Section "Screen"
Identifier "Default Screen"
Device "Vesa"
Monitor "GDM-5410"
Default Depth 24 etc etc.....


```

Typing startx i get thefatal error: no screens found ?

---

### Post by mikewhatever on 2007-02-22
Please note that it is X11, not x11.

---

### Post by maxppp on 2007-02-22
Yes Mike realised that one fairly soon, forgot about linux being case sensitive :S

---

### Post by maxppp on 2007-02-22
im getting about 15 lines of : Warning: font renderer for ".pcf already registered at priority 0.

finishing with Could not init font path element unix/:7100, removing from list!

---

### Post by mikewhatever on 2007-02-22
It is a good idea to back up the xorg file:
> cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
and I do not know what's wrong with the fonts.

---

### Post by renzokuken on 2007-02-23
> **maxppp said:**
> I changed to

```
Section "Screen"
Identifier "Default Screen"
Device "Vesa"
Monitor "GDM-5410"
Default Depth 24 etc etc.....


```

Typing startx i get thefatal error: no screens found ?


you changed the wrong section, hence no screens found. this is the section that controls the screens, not the "Device" section i stated earlier.

you need to change the value for "driver" in the "device" section, NOT the "device" value in the "screen" section

---

