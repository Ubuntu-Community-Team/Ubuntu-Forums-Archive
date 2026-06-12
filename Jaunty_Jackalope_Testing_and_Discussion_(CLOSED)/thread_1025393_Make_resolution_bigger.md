---
title: "Make resolution bigger"
date: 2008-12-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by inxygnuu on 2008-12-30
Does anyone know how to make the resolution bigger on Nvidia cards? I know Jaunty doesn't have all of the drivers, but what about xorg.conf?

---

### Post by vishalrao on 2008-12-30
You could change/add Driver line in xorg.conf to "nv" to see if it helps. Search around for default/sample xorg.conf

---

### Post by inxygnuu on 2008-12-30
little help here... I don't no where to put the nv. I have never been in the xorg.conf before.

---

### Post by vishalrao on 2008-12-30
never been in the xorg.conf before huh?

word of advice from one noob to another: if you (like me) want to ignore the warnings about running alphas then make sure you have external backups of your important data because it is very highly likely you or the software will trash your system completely :lol:

for xorg.conf in a terminal run "gksudo gedit /etc/X11/xorg.conf" to edit the file. in there look for a "Section Device" and add/edit a line before the "EndSection":

```
Driver "nv"
```

Else if its empty file, just add the following and try:

```

Section "Device"
Identifier "My Device"
Driver "nv"
EndSection

```

Since DontZap seems to be the default now (meaning you cant restart X with ctrl+alt+backspace) then either reboot, or I believe running "sudo /etc/init.d/gdm restart" might work...

If the video gets trashed I hope you know about selecting the recovery item below the normal boot item then going to a root shell from there, in case you need to make more fixes

---

### Post by Starks on 2008-12-30
I'm shocked that nobody has recommended the built-in nvidia control panel for the binary driver.

You can control resolution there or in the gnome-display-properties

---

### Post by vishalrao on 2008-12-30
isnt nvidia driver broken/unavailable with latest xserver/kernel in jaunty? im actually running 180.18 beta though

---

### Post by ShirishAg75 on 2008-12-30
A small tip. 

Its always a good idea to make backup of the file itself . 

so 

```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

Although having recover X in the recovery mode has made this point moot but still is good.

---

### Post by inxygnuu on 2008-12-30
> **Starks said:**
> I'm shocked that nobody has recommended the built-in nvidia control panel for the binary driver.

You can control resolution there or in the gnome-display-properties

neither work. Jaunty does not know I have an Nvidia card, and the gnome display panel only goes up to 800x600, which is ugly, and has very little room for me to do anything. I don't need 3d or anything, just my native resolution (1280x800). The xorg configuration gave me some error, so i just reset it to defaults.

help would be appreciated,
3v4n=P~

---

### Post by a fenderson on 2008-12-30
Could you post your current xorg.conf?

---

### Post by inxygnuu on 2008-12-30
Both on the .confs are posted in a file.

---

### Post by vishalrao on 2008-12-30
please try to add the line

```
Device "nv"
```

so that you have this in your JauntyX11.txt:

```

Section "Device"
  Identifier  "Configured Video Device"
  Device  "nv"
EndSection

```

make sure you have the package installed called "xserver-xorg-video-nv" installed, check in synaptic package manager

---

### Post by inxygnuu on 2008-12-31
Oh, thanks! the problem was that it couldn't find it. I didn't have it like that because in order for me to boot into jaunty, i had to change it back to the original.

---

### Post by inxygnuu on 2008-12-31
Yep, still having problems. is there a way to force a bigger resolution? All I actually need is the Nvidia driver, anyway...

---

### Post by a fenderson on 2008-12-31
I had to put this in my xorg.conf to get the resolution I wanted:

```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection      "Display"
                Depth 24
                Modes "1280x1024"
        EndSubSection
EndSection

```

And I don't know if this will work for you (I have an ati card), but I also had to add

```
        Option          "IgnoreEDID" "true"
```

to my "Device" section to get the correct resolution to show up.

---

