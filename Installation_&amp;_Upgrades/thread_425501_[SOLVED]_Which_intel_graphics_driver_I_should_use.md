---
title: "[SOLVED] Which intel graphics driver I should use?"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by finni on 2007-04-27
xserver-xorg-video-i810
or 
xserver-xorg-video-intel

I am now using the i810 package. All work well, even beryl, but I cannot change screen resolutions. I found out from the ubuntuguide.org that the latter driver package would allow me to change screen resolutions, but how does beryl work with that one?

Here's a snap from my lspci;
```

# lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

```

EDIT:

Info of my system:
HP NX7400 Laptop, Intel C2D T2400 Processor
Ubuntu Feisty (Upgraded from Dapper)
Gnome + Beryl

---

### Post by newlinux on 2007-04-27
I would like to know this too. I have:
Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

What do I gain by going to the intel driver? Better hardware acceleration?

---

### Post by finni on 2007-05-03
No answers? Surely there must be somebody who knows these things.

---

### Post by finni on 2007-05-03
Well, as nobody wanted to answer. I tested this myself ,found the courage..

It does work! Beryl works, changing resolutions works! Great, I recommend using the intel driver instead of the i810. At least with similar systems as mine.

---

### Post by newlinux on 2007-05-03
unfortunately it didn't work for me (I have the 915). KDM would load, but keep booting me back to the login screen after logging in.

---

### Post by _tms on 2007-05-03
I have been wondering myself whether to use intel or i810. I've found that xv + compiz does not work with both drivers, and I can only use "Textured Video" from the gstreamer-properties dialog which, on my machine has some vsync-like glitches. It becomes apparent when the video movies quickly. Therefor I'm settling with i810. 
If I could get decent video with the intel driver I'd use that.

---

### Post by finni on 2007-05-04
> **_tms said:**
> I have been wondering myself whether to use intel or i810. I've found that xv + compiz does not work with both drivers, and I can only use "Textured Video" from the gstreamer-properties dialog which, on my machine has some vsync-like glitches. It becomes apparent when the video movies quickly. Therefor I'm settling with i810. 
If I could get decent video with the intel driver I'd use that.

I use vlc for video with X11 Video -mode - works nicely. With XVideo it does give errors and will not function at all.

I managed to get dual-screen in clone-mode working. I'll post about it later on.

---

### Post by _tms on 2007-05-05
> **finni said:**
> I use vlc for video with X11 Video -mode - works nicely. With XVideo it does give errors and will not function at all.

I managed to get dual-screen in clone-mode working. I'll post about it later on.

It does not work nicely. It drains my battery much faster and the resize algorithm makes the image look pixelated.

---

### Post by finni on 2007-05-05
> **_tms said:**
> It does not work nicely. It drains my battery much faster and the resize algorithm makes the image look pixelated.

Ah, might be true that one. I dont watch videos that much anyway :)

---

### Post by finni on 2008-03-06
see the following thread for update on the matter: [http://ubuntuforums.org/showthread.php?t=710233](http://ubuntuforums.org/showthread.php?t=710233)

---

