---
title: "How i got 1280x800 widescreen resolution to work on Dell 700m"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by Krad on 2006-06-07
I fiddled with the 855 resolution and just could not get it to work like i had in breezy.  I went onto universe and did a search for 855.  855-> 915resoltution.  This package supports the 855chipset so installed it and read the readme that was suggested in the package summary.  It was your basic directions, to the point.  ran the few commands and edits i needed to make.  Reboot and 1280 x 800 showed up in my screen resolutions.  I selected it and I am in widescreen heaven again.!!! i will post the good parts of the doc below that helped me fixed the issue.

worked like a charm...

915resolution for Debian
------------------------

915resolution changes the resolution of an available vbios mode.

1. First, you need to check available modes by:

# 915resolution -l

2. You will get a mode list such as:

Intel 800/900 Series VBIOS Hack : version 0.4.7

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x768, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x768, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x768, 32 bits/pixel

3. Write the mode number and resolution which you want to use to
   /etc/default/915resolution. For example:

MODE=3c
XRESO=1400
YRESO=1050

# optional setting
BIT=32

4. Reboot or run "/etc/init.d/915resolution start" by hand.

5. To use specified resolution, you need to modify your X configuration
   file (If you use Xorg, it's /etc/X11/xorg.conf)

SubSection "Display"
    Depth           24
    Modes           "1400x1050" "1024x768" "800x600" "640x480"
EndSubSection


  -- Steffen Joeris <steffen.joeris@skolelinux.de>, Thu, 10 Nov 2005 12:02:41 +0100

:twisted:

---

### Post by Klaidas on 2006-06-07
Glad you succeeded :)
You could pubblish this to the howto section too :)

---

### Post by indrajeetak on 2006-08-10
Thank you for the succinct and techno-jargon free solution for the display problem. It worked wonderfully for me at the first attempt on my DELL 700m. If I were not able to solve the display problem, UBUNTU would have lost another user. You were a big help.:D

---

