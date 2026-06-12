---
title: "Xlib: connection to &quot;:0.0&quot; refused by server"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by ati on 2007-05-09
Hallo,

I upgraded form ubuntu 6.10 to kubuntu 7.4.
I have a strange problem after upgrading to 7.4.
If I try to open for example kedit via sudo command  it opens up but has no su privileges.
if I try to go root and open an aplication form console i get this error massage:
```

root@desktop:/home/ati# gedit
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

```

I also installed the server version on my other computer replacing fedora 4. Installed the kde package, and under x i have the same error as above mentioned.

Can please someone help me out? I spent quite some time to set up this system and would relay hate to reinstall it.

Thank you.

---

### Post by Wim Sturkenboom on 2007-05-09
With regards to root:
as far as I know, you can't work that way as the screen is 'owned' by the normal user and not by root and therefor your connection is refused.
Login as root in the graphical login screen and try gedit again; quite sure it will work.

No idea about kedit.

---

### Post by mlind on 2007-05-09
Is your user in admin group and admin group has been given root privileges in /etc/sudoers?

As Wim Sturkenboom said, root doesn't have privileges to your $DISPLAY, so either extract the display cookie using xautch extract and merge it as root using xauth merge, or use xhost +local:root.

---

### Post by ati on 2007-05-09
Thank you for the replays and the explanations.
xhost +local:root did the trick, now my life is much easier. :)

There is still something that doesn't seem right here, when i launch an application form console i get some error massages :

```

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Is that normal? or can i do something to get rid of them?

Thank you.

---

### Post by Nythain on 2007-05-09
to fix that problem edit your xorg.conf and comment out the table pc only devices like this:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "stylus"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

```
should do the trick

---

### Post by ati on 2007-05-09
It works like a charm.

Thank you.

---

