---
title: "clean 10.10 install - no window manager"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by smokin74 on 2010-10-20
as per the title - after a hard disk failure got new disk and attempting dual boot of xp and 10.10 - had to burn 10.10 twice to get it to complete the install process, but thats another story - basically on logging in there is now gnome panels - i get my 'low battery' warning etc and the login music but thats it - it does work in 'safe mode' though - what can i do to correct this?

ironically had exactly same problem on the upstairs desktop when upgrading to 10.4 but buggered if i can remember how i fixed it - even checked my previous posts on it.

im sure its probably something simple - help me out guys!!!

atb in advance 

Chris

---

### Post by smokin74 on 2010-10-21
still got this problem - its all there in 'safe mode' - help help help - it cant be too serious can it???


thanks in advance


chris

---

### Post by P4man on 2010-10-21
boot a regular session (that doesnt quite work). Press control+alt+F1
Log in if requested (password wont show up). Run 

```
dmesg
```

see anything at the end that catches your eye?

---

### Post by smokin74 on 2010-10-21
> **P4man said:**
> boot a regular session (that doesnt quite work). Press control+alt+F1
Log in if requested (password wont show up). Run 

```
dmesg
```see anything at the end that catches your eye?


to be honest, no ! i take it you were expecting something specific??

Cheers

Chris

---

### Post by P4man on 2010-10-21
well, I was hoping for a hint. Ive seen something similar once with the netbook remix and dmesg was full or errors about some faxmodem driver. Eventually it loaded the gnome panels but it took like 10 minutes. Blacklisting the modem driver  solved it for me. No such luck here :(

Can you tell us more about the PC hardware? amount of RAM, videocard you have ?

Also, this really is a clean install, and you didnt keep a /home partition? If you did, or even if you didnt,  try creating a new user:

```
sudo adduser testuser
sudo passwd testuser
```

try loggin in with "testuser".

---

### Post by smokin74 on 2010-10-22
> **P4man said:**
> well, I was hoping for a hint. Ive seen something similar once with the netbook remix and dmesg was full or errors about some faxmodem driver. Eventually it loaded the gnome panels but it took like 10 minutes. Blacklisting the modem driver  solved it for me. No such luck here :(

Can you tell us more about the PC hardware? amount of RAM, videocard you have ?

Also, this really is a clean install, and you didnt keep a /home partition? If you did, or even if you didnt,  try creating a new user:

```
sudo adduser testuser
sudo passwd testuser
```try loggin in with "testuser".

Hi again and thanks but still no joy 
added another user and same symptoms - log the user in in safe mode and its all good

it was a clean install as it was a new hard drive  - clean install of xp and ubuntu, all new patitions (seprate root and home partitions)

hardware is an compaq nx9005 laptop 512 ram 60 gig hd ati graphics with 64mb shared ram

as for errors in dmesg  - there is one that comes up about creating ali ac97 mixer - but it has done this on every versio of ubuntu - and i do have sound ok using pulseaudio - if you can tell me how to put the output of dmesg into a text file id be glad to send it to you/ post it here if that helps - i may be mising something obvious


once again, thanks


Chris

---

### Post by P4man on 2010-10-22
Okay, I googled the machine type and you seem to have a radeon 320 mobility U1, can you confirm that by running 

```
lspci
```

I suspect thats the cause, that card may not be properly supported. Do you have a xorg.conf file? If so, can you post it? If not, can you generate one, by running 

```
sudo Xorg -configure
```

(you have to stop X first, so run ```
sudo service gdm stop
``` first. To reload it run ```
sudo service gdm start
```

---

### Post by Rody on 2010-10-22
try ctrl alt F7

I am not having much luck with 10.10 so far but i did figure out that most of the time it boots (when it boots at all) to tty1 instead of tty7.

---

### Post by smokin74 on 2010-10-22
> **P4man said:**
> Okay, I googled the machine type and you seem to have a radeon 320 mobility U1, can you confirm that by running 

```
lspci
```I suspect thats the cause, that card may not be properly supported.


Thats Correct

 > **P4man said:**
> Do you have a xorg.conf file? If so, can you post it?


 If not, can you generate one, by running 

```
sudo Xorg -configure
```(you have to stop X first, so run ```
sudo service gdm stop
``` first. To reload it run ```
sudo service gdm start
```


Here it is

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "dri2"
    Load  "record"
    Load  "dri"
    Load  "extmod"
    Load  "dbe"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "CustomEDID"             # [<str>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
        #Option     "NewPLL"                 # [<bool>]
        #Option     "ZaphodHeads"            # <str>
    Identifier  "Card0"
    Driver      "radeon"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

@Rody - thanks for the reply - i have tried all the tty options - my machine boots up to the login screen fine - its only after signing in i just get the background image, the startup music, a popup about my critically low battery (i run on mains all the time as 2.2% isnt long lol!!) and a movable mouse pointer. If i select 'safe mode' option on login it all loads up fine.


Well chaps - over to you again

Cheers

Chris

---

### Post by P4man on 2010-10-22
In the device section try adding this line

```
Option "RenderAccel" "off"
```

---

### Post by smokin74 on 2010-10-22
done that - where should my xorg.conf file be stored  - i did a search and couldnt frind it so ran the 'Xorg -configure' as you said to give you the info i provided - it did, however store this as xorg.conf.new in my /home folder - just not sure as to where it should be as /home cant be right can it?


cheers

chris

---

### Post by P4man on 2010-10-22
It goes to /etc/X11
Check if there isnt one there already, if there is, post that one.

If there is none, then copy the one you created there and rename it (remove the .new)

from a terminal:

```
sudo mv xorg.conf.new /etc/X11/xorg.conf
```

Note the upcase X.

---

### Post by smokin74 on 2010-10-23
> **P4man said:**
> It goes to /etc/X11
Check if there isnt one there already, if there is, post that one.

If there is none, then copy the one you created there and rename it (remove the .new)

from a terminal:

```
sudo mv xorg.conf.new /etc/X11/xorg.conf
```Note the upcase X.


done that - still no joy 

What is different about the safe mode parameters that is different to standard 'desktop' mode that allows it to work ok?? - from what i see i have ***less*** permissions in safe mode as you cant invoke any 'root' type operations such as adding a user using the 'users' menu  (you can do it via sudo in a terminal window still), or attempting to use the software update / synaptic (but you can apt-get in a terminal window)

it must be something and nothing...........???

atb

chris

---

### Post by P4man on 2010-10-23
just to be sure, can you provide the contents of

```
/etc/X11/xorg.conf
```

Also you can try changing
```

 Driver      "radeon"
```

into 
```

 Driver      "vesa"

```

see if that cures it

---

### Post by smokin74 on 2010-10-23
xorg.conf:

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "dri2"
    Load  "record"
    Load  "dri"
    Load  "extmod"
    Load  "dbe"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "CustomEDID"             # [<str>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
        #Option     "NewPLL"                 # [<bool>]
        #Option     "ZaphodHeads"            # <str>
    Identifier  "Card0"
    Driver      "radeon"
    BusID       "PCI:1:5:0"
    Option "RenderAccel" "off"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

will try your alteration now and report back


cheers for sticking with this

Chris

---

### Post by smokin74 on 2010-10-23
ok i altered it and its now throwing me to tty1 on startup - obviously i need to edit xorg.conf to correct it (there was no .bak file created so i cant just rename) - having to type this in windows - what is the text editor i need to use? 

cheers

Chris

---

### Post by P4man on 2010-10-23
eck. vesa is like so basic, it should always work, but I guess you should have removed some of the modules as they wont work with vesa.

Anyway, to fix it, you could simply remove or rename xorg.conf, but to edit it:

sudo nano /etc/X11/xorg.conf

Then to save press control+X and then Y.
But Id leave vesa in there, just try commenting out all the modules, and remove that
    Option "RenderAccel" "off"
line again.
To try, start a gui session with

```
sudo service gdm start
```
(if it complains its already running, replace start with restart)

---

### Post by smokin74 on 2010-10-24
Still no joy - wont do safe mode even unless "radeon" is the driver

even regenerated xorg.conf file and started the process from scratch no joy

am i consigned to safe mode forever???

---

### Post by LittleHome on 2010-10-28
Hello to everyone...

unfortunately this is the only thread I have found that treats the same problem I have - and it ends here without a solution.

:(

My problem is just the same, only I have done an update from 10.04 rather than a clean new install. I am experiencing this on an embedded platform with an Intel Pentium Mobile and using an Intel GME965 graphics chip.
Strangely I can turn the window manager back on using the Visual Effects page in the settings of a normal session (no safe mode). Switching to "Extra" (thus using compiz) or back to "None" (for metacity) turn on the respective window manager and everything is fine until I turn off the machine...

I have the impression that window manager (no matter which) either is simply not started at all or something gets in the way of starting it as the system boots.

Can anyone tell me, where I can find the settings, programs etc. that automatically start at boottime?
Are they different from the things that get started during logon of a user?
How can I influence them?

I hope to have been complete in my explanation. - Unfortunately I am not as experienced yet... Just  XXX  Windows a little while ago.

Thanks for any help and input!
Thilo

---

### Post by BigMick on 2010-10-28
> **LittleHome said:**
> Hello to everyone...

unfortunately this is the only thread I have found that treats the same problem I have - and it ends here without a solution.

:(

My problem is just the same, only I have done an update from 10.04 rather than a clean new install. I am experiencing this on an embedded platform with an Intel Pentium Mobile and using an Intel GME965 graphics chip.
Strangely I can turn the window manager back on using the Visual Effects page in the settings of a normal session (no safe mode). Switching to "Extra" (thus using compiz) or back to "None" (for metacity) turn on the respective window manager and everything is fine until I turn off the machine...

I have the impression that window manager (no matter which) either is simply not started at all or something gets in the way of starting it as the system boots.

Can anyone tell me, where I can find the settings, programs etc. that automatically start at boottime?
Are they different from the things that get started during logon of a user?
How can I influence them?

I hope to have been complete in my explanation. - Unfortunately I am not as experienced yet... Just  XXX  Windows a little while ago.

Thanks for any help and input!
Thilo

Hi,

I managed to get around this issue by adding this to the bottom of my xorg.conf file:


Section "Extensions"
Option "Composite" "Disable"
EndSection


Hope this helps.

---

### Post by smokin74 on 2010-10-28
> **BigMick said:**
> Hi,

I managed to get around this issue by adding this to the bottom of my xorg.conf file:


Section "Extensions"
Option "Composite" "Disable"
EndSection


[COLOR=Red]**Hope this helps.**[/COLOR]

Indeed it did - that appears to have done the trick - pretty much as it should be - the only niggle i can see is the 'network' icon in the notification tray has a grey background - not exactly the end of the world though!!

thanks for your help (and everyone else too!!)


atb

chris

---

### Post by LittleHome on 2010-11-09
> **BigMick said:**
> Hi,

I managed to get around this issue by adding this to the bottom of my xorg.conf file:

Section "Extensions"
Option "Composite" "Disable"
EndSection


Hello BigMick,

I have helped myself (quick and dirty, I guess) by adding COMPIZ to the auto-start programs (sorry, I'm using a German version and don't know how exactly this is called in the English version...). This works fine for me.
Might try your solution later, if I find some spare time. Will let you know then.

Thanks to everyone.
Thilo

---

### Post by warfie on 2010-11-11
I suffered this problem after a clean install of Meerkat on an old Dell 5150 with a Geforce FX Go5200.
The problem only occurred after installing the restricted driver for the graphics card.
I fixed it by uninstalling and reinstalling Compiz through the package manager.

Hope this helps someone else...

---

