---
title: "graphique stuck at 640X480"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by Kaizoku001 on 2011-09-08
When I browsed Ubuntu 11.04 from the CD, or when I used usb boot loader, the display looked good,

but after installing ubuntu stand alone, i can only get a 640X480 display.
in aditional drivers, it show that NVIDIA is active, but not in use.
I have no idea what this means

I admit I am a newb, can somebody please help

---

### Post by realzippy on 2011-09-08
Welcome to UF!
Did you install the driver in additional drivers?

Open a terminal,run:

```
sudo nvidia-xconfig
```

reboot.

---

### Post by Kaizoku001 on 2011-09-08
> **realzippy said:**
> Welcome to UF!
Did you install the driver in additional drivers?

Open a terminal,run:

```
sudo nvidia-xconfig
```reboot.

Thanks for the reply.
trie it and this is what I got:

> Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
I really want to switch to ubuntu, but not with this display rez.
Why is the resolution ok when I just try Ubunto and not when i install it.
Help please.
######################
Also
In Add Drivers it shows 
"NVDIA Accelerated Graphics Driver" wit green light next to it 
And then Says 
> 3D-accelerated proprietary graphics driver for NVIDIA cards. Required if you want to run Unity.

This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as provide 2D acceleration of newer cards.

You need to install this driver if you wish to use the Unity desktop, enable desktop effects, or run software that requires 3D acceleration, such as some games.
and under that 
I have 
"Green ligth: this driver is activated but not currently in use"
how do i get it in use????

---

### Post by Kaizoku001 on 2011-09-08
just wanted to add one more detail
I'm using a LG iPS226 led monitor
and ubuntu seems to not be able to recognize my monitor

Please help

going to bed now. hope i can solve this tomorrow.
would hate to have to go back to Win

---

### Post by realzippy on 2011-09-08
No panic.
Now nvidia-xconfig has created a new xorg.conf,
we now have to add the valid Hsync/Vrefresh values for your monitor
and everything will be alright.
Please show that file:

```
gedit /etc/X11/xorg.conf
```

---

### Post by Kaizoku001 on 2011-09-08
> **realzippy said:**
> No panic.

```
gedit /etc/X11/xorg.conf
```

Good morning 
Thank you for the reply.

Ok gedit is open and ready, 
all i see i a blanc page there's nothing in it
What do I need to type in it?
My video card is geforce gt 430

1 more thing, I just DLed the latest driver for galaxy geforce. it's now in my download folder.
NVIDIA page  writes: > Installation  instructions: Once you have downloaded the driver, change  to the directory  containing the driver package and install the driver  by running, as root, sh ./NVIDIA-Linux-x86_64-280.13.run

  One of the last  installation steps will offer to update your X  configuration file. Either  accept that offer, edit your X configuration  file manually so that the NVIDIA X  driver will be used, or run  nvidia-xconfigwell now my problems are:
did that and this is what I got:> ERROR: You appear to be running an X server;
       please exit X before installing.  For
       further details, please see the section
       INSTALLING THE NVIDIA DRIVER in the
       README available on the Linux driver
       download page at [www.nvidia.com](www.nvidia.com).


ERROR: Installation has failed.  Please see
       the file
       '/var/log/nvidia-installer.log' for
       details.  You may find suggestions on
       fixing installation problems in the
       README available on the Linux driver
       download page at [www.nvidia.com](www.nvidia.com).


Welcome to the NVIDIA Software Installer for
Unix/Linux

The file '/tmp/.X0-lock' exists and appears to
contain the process ID '1094' of a runnning X
server.

**how do I exit x server (and should I)**
[B] don't know if i should accept, config or run xconfig.
also need to figure out what to input in my gedit windows for xorg.conf
[/B]
other than that all is well
"not"

---

### Post by realzippy on 2011-09-09
Please wait with installing manually downloaded nvidia-driver.
This should be last choice; when manually installing you have to repeat this
whenever there is a kernel update.
Also your nvidia driver seems to be installed already, otherwise the command *sudo nvidia-xconfig* would have refused to work.

When you ran it,it repeated:
```
New X configuration file written to '/etc/X11/xorg.conf' 
```

So I wonder why  *gedit /etc/X11/xorg.conf* shows nothing.
Typo?
Please repeat:
```
sudo nvidia-xconfig
```
then
```
gedit /etc/X11/xorg.conf
```

---

### Post by Kaizoku001 on 2011-09-09
Ok this is more like it.
here is what i have in gedit
what exactly shold i change? i don' want to make any mistakes here.

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-08.nvidia.com)  Mon Apr 18 15:14:00 PDT 2011


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


not to sound too redundant, but
again thanks

---

### Post by realzippy on 2011-09-09
You have to edit 
```
HorizSync [COLOR="Red"]28.0 - 33.0[/COLOR]
VertRefresh [COLOR="Red"]43.0 - 72.0[/COLOR]
```

which are vanilla/failsafe to the values for your monitor:

```
HorizSync 30.0 - 83.0
VertRefresh 56.0 - 75.0
```

use

```
gksudo gedit /etc/X11/xorg.conf
```

to open file with admin privileges.
Close file saving changes,reboot (or restart Xserver).

---

### Post by Kaizoku001 on 2011-09-09
Ok I did as you suggested.
rebooted, and still no changes.
I went to system settings to see if anything changed
nothing did. my max resolution is still 640X480
additional Drivers: still say that the "NVIDIA accelerated Graphics driver"
is activated but not currently in use.

What Next?
BTW
when I shut Gedit i get this message in terminal
> (gedit:1663): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1663): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.8GDN1V': No such file or directory

(gedit:1663): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


---

### Post by realzippy on 2011-09-09
Ignore the "driver activated but not in use" message for the moment.
This probably is a well known bug.
Please open xorg.conf again,I am not sure if the Hsync/Vrefresh edits
you tried to make persisted due to the error messages you posted.

---

### Post by Kaizoku001 on 2011-09-09
Unfortunately I'm not home rigth now.  
Had te step out for a few hours,
But after I wrote my post I reppened  xorg.conf just to make sure the changes were saved.
They were.

---

### Post by realzippy on 2011-09-09
Strange.
Run
```
sudo nvidia-bug-report.sh
```

and attach (please do not post,it is too large) the resulting file.

---

### Post by Kaizoku001 on 2011-09-09
Ok I'm back.

here is the file
[ATTACH]201804[/ATTACH]

Hope this works

---

### Post by Kaizoku001 on 2011-09-09
BTW how do I see what's in the 
Bug report?
##############
Sorry figured it out.

---

### Post by dino99 on 2011-09-09
let X be drived by the kernel, and dont confuse it with proprio config

sudo rm /etc/X11/xorg.conf

are you connected via displayport ?
The monitor on displayport will tear, the only way around this is to use a displayport adapter.

xorg with displayport is known to work out of the box with 'nouveau' (un-blacklist it)

---

### Post by Kaizoku001 on 2011-09-09
> **dino99 said:**
> let X be drived by the kernel, and dont confuse it with proprio config

sudo rm /etc/X11/xorg.conf

are you connected via displayport ?
The monitor on displayport will tear, the only way around this is to use a displayport adapter.

xorg with displayport is known to work out of the box with 'nouveau' (un-blacklist it)

sorry but i officially have no idea what your talking about

---

### Post by Kaizoku001 on 2011-09-09
The Good news is the problem is solved.
Unfortunately, I don't Know why, or more precisely what was wrong. witch is something i hate.
your last post gave me an idea: I shutdown the PC and disconnected the dvi cable and connected the VGA (d-sub 15 pin) cable.
restart the PC and all is well.

[B]now why was it bad in the first place?
Why did it all look good when i tried ubuntu from the CD and not when i installed it?
is there a way for me to use the DVI connection in the future?
And what about the HDMI?[/B]

Ubuntu seems to be full of questions.
any idea where I can find the answers?

And again thanks for the help!

---

### Post by realzippy on 2011-09-09
**@dino99**

Do you want to say that OP should use the nouveau driver instead of the nvidia-driver?
Or do you want to say that the nvidia-driver works without EDID
(you read his log for sure) in full resolution?
Please explain.
.........................................................................

@Kaizoku001

from your log:
```
[    15.024] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-0 is invalid: the
[    15.024] (WW) NVIDIA(GPU-0):     checksum for EDID version 1 extension is invalid.
```
...means,the nvidia-driver cannot "see" your monitor's data and uses
kind of failsafe mode.Normally adding Hsync/Vrefresh works,I have no idea why it fails here.
Since your setup works with connected VGA cable,you could try to acquire the EDID data with the  VGA cable connected,then "feed" this data manually
when using the DVI cable.

With VGA cable connected,can you check if a button
"acquire edid" is offered in nvidia-settings ?

---

### Post by Kaizoku001 on 2011-09-09
> **realzippy said:**
> 
With VGA cable connected,can you check if a button
"acquire edid" is offered in nvidia-settings ?

indeed ther is. and I have saved a copy.

---

### Post by realzippy on 2011-09-10
So you could edit your xorg.conf "Device" section with:

```
Option "ConnectedMonitor" "DFP-0"
Option "CustomEDID" "DFP-0: /etc/X11/edid.bin"
```

Move your saved edid.bin to /etc/X11/ of course or change the path to your needs.
Then test the dvi cable...

---

