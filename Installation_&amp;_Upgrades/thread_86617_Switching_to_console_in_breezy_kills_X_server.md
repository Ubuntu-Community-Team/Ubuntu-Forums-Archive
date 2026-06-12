---
title: "Switching to console in breezy kills X server"
date: 2005-11-05
forum: Installation &amp; Upgrades
---

### Post by qhuys on 2005-11-05
Hi there

I've just had a very traumatic upgrade to Breezy from Hoary (which worked beautifully, see right at the bottom of post for description of what I did / went wrong). I've ended up having to do a clean breezy installation, which went well. However, when I now switch to console and then back to gnome (or ion), the X server dies. In fact it dies so badly that I can't even restart it and can't go back to a console or kill gdm or anything. I have to shutdown the computer and restart. I've tried doing 
            dpkg-reconfigure xserver-xorg
which didn't help but then I don't really understand all the options

I'm on a Dell Latitude C400, PIII, 512Mb RAM, i810 chipset. My xorg.conf file is below. 

I'd be VERY grateful if somebody could help me with this... 

Thanks, q

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82830 CGC [Chipset Graphics Controlle
r]"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSectionSection "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82830 CGC [Chipset Graphics Controller]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection



EndSection


-------------------------------------------------
Here is what I did when upgrading, in case it helps somebody: 
First, when I popped the CD into the drive, ubuntu didn't notice anything (no popup)
In synaptic, I added the Breezy CD and unselected all other repositories. 
I then hit the reload and apply buttons. 
There were lots of locale problems (my locale was en_GB:en I think)
At some point dpkg complained and returned an error, which seemed to be caused by postfix (?), though I'm not sure I understood that bit. 
Thereafter, I tried to do apt-get -f dist-upgrade, but ended up with the same problem, though it seems I got through a few more packages.

---

### Post by qhuys on 2005-11-06
I should add that the X server dies most flamboyantly. All kinds of weird colours happen on the screen, until it finally ends up with some fat ugly vertical red lines...

---

### Post by greenwom on 2005-11-06
I have a similar problem, if I ctrl-alt-backspace it doesn't restart x. 
I can go back and forth from the terminal but it doesn't always work. 

Where do we go from here.  If I'm trying to anything like configure a mouse and I want restart X to check the settings I have to reboot each time :(

hope someone can give guidance.

---

### Post by jbhuffman on 2005-11-21
Any word on a fix/solution for this?  I have this issue and cannot find an answer.

---

### Post by rjwood on 2005-11-21
[quote=jbhuffman]Any word on a fix/solution for this?  I have this issue and cannot find an answer.[/quote]

what happens when you type startx?

---

### Post by jbhuffman on 2005-11-21
Wow, fast response, thanks!

Actually, if I attempt to switch back to X, the system becomes unusable.  I cannot kill X nor switch back to console; I have to reboot the machine.  It appears to be caught in a loop, either refreshing X or actually attempting to stop/start X again.  I'm not sure other than if I switch to a console, I lose any ability to switch back to X.  I imagine I could kill X from the console and restart but that is quite annoying.

I've just been using terminal within my X session until I can find a solution.

J.

---

### Post by Joeak on 2005-11-30
I have pretty much the same problem, with Breezy on a Dell C400 with i810 video driver.  X works well, but when you ctlr-alt-f1 to a terminal session, when you ctrl-alt-f7 back to X whatever text screen I am on melts oddly to white and then black.  I usually power it off and back on.  I found that I could, however, do ctrl-alt-del and it would go through a reboot that is invisible until the BIOS fires up.

I don't care that much about virtual terminals but I think this may be related to why X won't start at all after I suspend/hibernate...  One bug at a time...

---

### Post by slightly72 on 2006-03-20
Have you guys figured out what the problem is? It seems I have exactly the same problem (X server going blank after switching to console, after hibernate) on the same intel 82830 chipset, so your solution might work for me too. Thanks.

---

### Post by phibxr on 2006-05-29
Same problem here. iMac G4 750MHz with Geforce 2 MX running on open source NV-drivers.

---

### Post by Joeak on 2006-06-02
See my post at [http://ubuntuforums.org/showthread.php?p=531943#poststop](http://ubuntuforums.org/showthread.php?p=531943#poststop)

I think the main solution was:

sudo nano /boot/grub/menu.1st
on kernel line, add "vga=771" (without the quotes) to kill the flashing boot screen
ctrl-x to save

and then rebooting

---

### Post by qhuys on 2006-10-30
Hey guys

So, a year down the line or whatever, I finally came across the solution --  use vga=771 as a kernel option (to stop the screen from flashing during startup). Then edit the file /etc/X11/xorg.conf. In the section "Section Screen" change the default depth to 16 (in my case from 24). That did the trick. It also solved the hibernation problems :D Take care, Q

---

