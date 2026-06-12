---
title: "Newbie without a clue"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by Seazzy on 2005-02-24
I recently installed Warty on my PC (Celeron procesor, 128mb RAM), and while I have been able to work thru most of my problems my biggest trouble right now is that Ubuntu is freezing. 

I have checked the logs, but there do not seem to be any error messages from when the system freezes.

 Sometimes a white line will run vertically down the screen when it freezes, other times it will just freeze. I have noticed that the freezing usually coincides with trying to move objects on the screen ie: a scroll bar on a text window in Mozilla,  moving files from my home directory to another folder w/in the home directory in the GUI.

I have not been able to get into the GRUB menu (is menu the right word) when I boot up, because my ESC key doesn't work (!), but I am not even sure that that is where I should be looking.

Anyone have any ideas about what's going on here?

---

### Post by alastair on 2005-02-24
This is a hard one to diagnose - even locally perhaps.

Maybe a video driver problem - what video card?

What driver? e.g.

grep Driver /etc/X11/xorg.conf

---

### Post by bennyp on 2005-02-24
[QUOTE=Seazzy]I recently installed Warty on my PC (Celeron procesor, 128mb RAM), and while I have been able to work thru most of my problems my biggest trouble right now is that Ubuntu is freezing. 

I have checked the logs, but there do not seem to be any error messages from when the system freezes.

 Sometimes a white line will run vertically down the screen when it freezes, other times it will just freeze. I have noticed that the freezing usually coincides with trying to move objects on the screen ie: a scroll bar on a text window in Mozilla,  moving files from my home directory to another folder w/in the home directory in the GUI.

I have not been able to get into the GRUB menu (is menu the right word) when I boot up, because my ESC key doesn't work (!), but I am not even sure that that is where I should be looking.

Anyone have any ideas about what's going on here?[/QUOTE]
 Hey, I'm Zeazzy's brother.
It's an alladin tnt2 on board video card

---

### Post by Buffalo Soldier on 2005-02-25
Two siblings using Ubuntu. If that is not a show of Ubuntu-Love, I don't know what is :P

TNT2 is and old card, but I don't think its too old. What's your XF86Config-4 file looks like?

---

### Post by Seazzy on 2005-02-28
Here is my fourth attempt at posting my XF86Config-4 file. The computer kept freezing everytime I pasted into the reply to thread field!

```


Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/Speedo"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "speedo"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
        Load    "xtt"

EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xfree86"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "dvorak"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
   Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV5 [Aladdin TNT2]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Visual Sensa"
        HorizSync       30-70
        VertRefresh     50-160
Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV5 [Aladdin TNT2]"
        Monitor         "Visual Sensa"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"

                Depth           8
                Modes            "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes            "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection




```

---

### Post by bennyp on 2005-03-10
Hey people.

So we have some more info for you.

This computer exhibits the same lacking up behavior with other OS's as well. We've tried with Windows 98, Windows 2000, KNOPPIX live CDs, and ubuntu, and we're going to try with gentoo soon if the locking porsists, but i suspect that using gentoo wont help. The only OS that does not produce locking is Windows98. I've advised my sister to run a memtest, even though we've run memtests before to no avail.

---

### Post by hashimoto on 2005-03-10
For me this starts to sound more like a hardware issue (though I can't explain why it would work correctly on W98). Is the card securely in its slot, pushed all the way to the bottom?

---

### Post by Seazzy on 2005-03-31
The card is stuck inplace, it's part of the cheap motherboard we got with the original box.

I am now thinking it might be good idea to try another distro. Does anyone know of any that are good for ancient hardware? I suspect that most new OS's, commercial and non-, are getting a little too caught up in making things all shiny and cool-looking, which is great if you have up-to date hardware. If your hardware, like mine, works but is not new enough to work with the new software, it seems like you are SOL.

Where is the free software for people who also want free (as in old) hardware?

---

### Post by Whiffle on 2005-03-31
That sounds like a hardware issue to me, espcially if windows is doing it.  In my experience hard lockups are most commonly related to bad power supplies or something not being seated correctly.

---

