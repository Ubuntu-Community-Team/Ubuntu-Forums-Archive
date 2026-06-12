---
title: "Strange Terminal Cursor Behavior Dapper"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by philosophia on 2006-12-27
After installing dapper I notice that text in the terminal seems 'flickery', it is becoming a little annoying.  The behavior I see is

When typing text in a terminal in Gnome, I hit a character on the keyboard, the cursor moves to the beginning of the line, then to the end of the line and displays the character.  So it looks like the cursor is always flickering.

This is with the default terminal font Gnome terminal is configured to use out of the box - monaco 12.  It seems to be a problem local to the machine since, if I SSH to a remote host in the same terminal - all of a sudden the flickering cursor problem disappears.

Here is the section related to my screen resolution from my xorg.conf
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 945G Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x768" "1024x768" "800x600" "640x480"
```

Anyone experience this problem before?

---

