---
title: "Ubuntu Edge 6.1 X can't start due to wscom"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2007-01-04
I don't have any wacom tablets plugin my computer, After Ubuntu Edge 6.1 works fine for 1 day, the system crashed when I tried to reboot.... Probably, Ubuntu Edge 6.1 looks my Logitech Webcam 5000 pro ( I use UVC as the driver ) as a tablet or something... 

no clue of it at all.

I tried to install wacom-tools by apt-get install wacom-tools, yes, it's installed, but no folder(or file) was created as "/dev/input/wacom", there is a folder "/dev/input", but can only seen when boot into text mode Ubuntu, I can't reach it in SuSE (it should be able to I believe)....

Everything has been tried but ends up failure. Unlike other reports online, my problem is I don't actually have a tablet at all !!!

Anybody can help?? Really urgent!!!

Cheers
JIA Pei

---

### Post by jiapei100 on 2007-01-04
Problem solved. But the way to solve it seems a little bit stupid.
Revise /etc/X11/xorg.conf as the following: change all the original "/dev/input/wacom" to "dev/input/event0"


Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/event0"          # Change to
                                                      # /dev/input/event
                                                      # for USB
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/event0"          # Change to
                                                      # /dev/input/event
                                                      # for USB
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/event0"          # Change to
                                                      # /dev/input/event
                                                      # for USB
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

---

### Post by jiapei100 on 2007-01-04
still one problem!!!

Each time I reboot, I still have to go into text mode first, then type startx...

Besides, it seems that "startx" and "X" have some difference, right?

cheers

---

### Post by tictacman on 2007-01-25
I came across wacom tablet weirdness after trying to get my 5000pro to work (which it sort of does).  Have you commented out the last few lines of xorg.conf as well?  

#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
EndSection

Probably wont work i'm just a newbie, but thought it might be worth mentioning:D

---

