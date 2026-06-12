---
title: "Howto: Boot Gutsy Live CD with ATI Cards"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by sarkar on 2007-10-25
*Disclaimer: I've only tested this method on my ATI Mobility Radeon X1400.*

1. Boot the Live CD with the option "Start Ubuntu in Safe Graphics Mode."  I usually hit F6 and edit the options, removing "quiet splash" from the end.

2. X.org will fail to start after trying 6 times, giving the error message "Server was shutdown 6 times in 90 seconds. Something bad is going on."  You will be returned to a terminal prompt.

3. At this point, your resolution will be too low to see the prompt.  Issue the command "clear" to see it.

4. Kill the failed X server by issuing: ```
$ **sudo killall gdm**
```  If you don't do this, it will continue to try to restart periodically.

5. Edit xorg.conf by issuing: ```
$ **sudo nano /etc/X11/xorg.conf**
```

6. Scroll down to the "Screen" section, which should look something like the code below.  The root of the problem is a missing line in the Display subsection.  Add the line "Depth 24" at the beginning of the Display subsection (bold below).  Note that above it is a line "DefaultDepth 24"; however, there was no Display associated with this depth!

```

Section "Screen"
    Identifier      "Default screen"
    Device          "Generic video card"
    Monitor         "Generic monitor"

    DefaultDepth    24
    SubSection "Display"
        **Depth      24**
        Modes       "1400x1050"
    EndSubSection
EndSection

```

8. Hit Ctrl+O followed by Enter to save the file (you won't be able to see the bottom of the editor).  Hit Ctrl-X to exit.  You won't be able to see the prompt, so issue "clear" again.

9. Restart X with the command: ```
$ **startx**
```

And voila! You will successfully boot from the Live CD.

---

