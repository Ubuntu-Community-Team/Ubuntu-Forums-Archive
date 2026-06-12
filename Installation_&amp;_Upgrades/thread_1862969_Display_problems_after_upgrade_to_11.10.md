---
title: "Display problems after upgrade to 11.10"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by mazin77 on 2011-10-17
Hello,
I upgraded from the first 11.04 to 11.10 beta with no problem.After some update I got the following problem:
-When my PC starts, while in the splash screen, the screen become blank ( amber LED like in a standby) , the HDD activity stops and  I get no response from Alt+Ctrl+F1, Esc  ...etc. But if I press Ctrl+Alt+Del the Kubuntu splash screen appears then the system restart.

-If I press Esc button while the system start during the splash screen before it hang, the system start to a command line . I pressed Alt+F7 Alt+F8 and i don't see errors.

-I read in some forum that deleting xorg.conf can solve the problem; so I mv it.
Now the GUI start, but whenever I login I get the folowing message:
```
"none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 262
CRTC 262: trying mode 1024x768@0Hz with output at 1152x864@60Hz (pass 0)
CRTC 262: trying mode 1024x768@0Hz with output at 1152x864@60Hz (pass 1)
"
```Also I cant change my resolution, no desktop background image, and  if I didn't press OK in the previous message early the menus and icons will look ugly!

CPU AMD64
GPU ATI radeon x800 pro
monitor Philips 107S "Unkown in System setting> Displays after I removed xorg.conf"
OS GUI  ubuntu 64-bit 11.10 gnome

---

### Post by swerner on 2011-10-17
> **mazin77 said:**
> 
-I read in some forum that deleting xorg.conf can solve the problem; so I mv it.
Now the GUI start, but whenever I login I get the folowing message:
```
"none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 262
CRTC 262: trying mode 1024x768@0Hz with output at 1152x864@60Hz (pass 0)
CRTC 262: trying mode 1024x768@0Hz with output at 1152x864@60Hz (pass 1)
"
```


I had the same problem with that message appearing.  It was solved with:
```

rm ~/.config/monitors.xml

```

---

### Post by bohemier on 2011-10-19
> **swerner said:**
> I had the same problem with that message appearing.  It was solved with:
```

rm ~/.config/monitors.xml

```

Thank you so much... I had a similar problem and although I replaced my old xorg.conf file in place, I had that kind of error message.

Cheers

---

### Post by 130s on 2011-12-02
This worked for me like a charm. Thanks!

---

### Post by kd8cgo on 2011-12-17
This worked great for me as well on an Nvidia GTX 460M laptop!  Thanks +1!

---

### Post by mejpark on 2012-04-19
My Ubuntu 11.10 machine has an nVidia GT218 [GeForce 210] graphics card installed. I have 2 Dell 1708FP panels connected to the adapter - the first by DVI, the second by VGA.

The following error message popped up each time I logged in:

```
none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 354
CRTC 354: trying mode 2560x1024@50Hz with output at 1280x1024@51Hz (pass 0)
CRTC 354: trying mode 2560x1024@50Hz with output at 1280x1024@51Hz (pass 1)

```

I choose the safe option to backup the XML file rather than delete it, just in case I needed to restore it:

[FONT="Courier New"]mv ~/.config/monitors.xml ~/.config/monitors.xml.backup[/FONT]

Thank you for sharing the solution, bohemier, This solved the problem - the error message no longer appears when I sign in.

Although, the monitor that is connected to VGA input is not as sharp as the monitor connected using DVI. On Windows XP, the image on both screens is pin sharp - I can't spot any difference between the two. Does anyone else experience this on Ubuntu?

---

