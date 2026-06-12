---
title: "After Warty-&gt;Hoary upgrade, nvidia driver doesn't work"
date: 2005-04-25
forum: Installation &amp; Upgrades
---

### Post by pointym5 on 2005-04-25
I upgraded my wife's Ubuntu machine from Warty to Hoary this morning via apt-get. Everything seemed to go OK, but upon reboot the X server wouldn't start. The failure had the familiar look of an unhappy nvidia driver, so I made sure I had updated that, and it continued to fail.

After much trying and retrying the reinstallation of everything I could think of, I ended up downloading the driver kit from NVidia.com and building my own. That version worked perfectly.

When it was failing, I got no errors whatsoever in my X log.  It looked fine.  I could also successfully load the nvidia module via modprobe, with no reported errors.

The machine in question is a slightly old Athlon box with an AGP GeForce2 MX 400 card. It had always worked just fine under Warty with the nvidia driver.

---

### Post by poofyhairguy on 2005-04-25
[QUOTE=pointym5]I upgraded my wife's Ubuntu machine from Warty to Hoary this morning via apt-get. Everything seemed to go OK, but upon reboot the X server wouldn't start. The failure had the familiar look of an unhappy nvidia driver, so I made sure I had updated that, and it continued to fail.

After much trying and retrying the reinstallation of everything I could think of, I ended up downloading the driver kit from NVidia.com and building my own. That version worked perfectly.

When it was failing, I got no errors whatsoever in my X log.  It looked fine.  I could also successfully load the nvidia module via modprobe, with no reported errors.

The machine in question is a slightly old Athlon box with an AGP GeForce2 MX 400 card. It had always worked just fine under Warty with the nvidia driver.[/QUOTE]

Can I see your Xorg conf?

---

### Post by pointym5 on 2005-04-25
Sure - note that, as I said, the machine is now working properly with "nvidia", while beforehand it did not.


```

Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Driver          "nvidia"
        BusID           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-96
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by DutchLau on 2005-04-26
Hi,

I had EXACTLY the same problem when I first upgraded via apt-get distroupgrade. I backed up the important files I had on the computer putting the primary hdd as a slave in my over Ubuntu box, and I installed Hoary from a burned Iso. No problems whatsoever, if anything, X was faster in Hoary! I recommend a fresh install, but who am I?  :-)  Good luck,

Cheers,

---

### Post by fordfan753 on 2005-04-26
[QUOTE=pointym5]I upgraded my wife's Ubuntu machine from Warty to Hoary this morning via apt-get. Everything seemed to go OK, but upon reboot the X server wouldn't start. The failure had the familiar look of an unhappy nvidia driver, so I made sure I had updated that, and it continued to fail.

After much trying and retrying the reinstallation of everything I could think of, I ended up downloading the driver kit from NVidia.com and building my own. That version worked perfectly.

When it was failing, I got no errors whatsoever in my X log.  It looked fine.  I could also successfully load the nvidia module via modprobe, with no reported errors.

The machine in question is a slightly old Athlon box with an AGP GeForce2 MX 400 card. It had always worked just fine under Warty with the nvidia driver.[/QUOTE]

Try replacing 
driver     "nvidia"
with:
driver     "nv"
This should let you start X, then install the newest nvidia drivers via apt-get or any other way you can think of. After this is all installed properly try to change "nv" back to "nvidia" to test the drivers, if X starts test to see if you get a good frame rate in glxgears, if X doesn't start just back up all your important stuff and reinstall Hoary.

---

### Post by pointym5 on 2005-04-26
[QUOTE=fordfan753]Try replacing 
driver     "nvidia"
with:
driver     "nv"
This should let you start X,[/QUOTE]

Well, uh, if you read the post you'll see that I did all that. The driver from the Ubuntu upgrade **did not work at all**.  That's the point.  Yes, of course I could bring up X with the "nv" driver, but so what?  I'm trying to voice a problem I found (and which, apparently, has been seen by other people) with the upgrade process. I personally am familiar enough with the way things work that building the NVidia drivers myself wasn't an issue, but that should not be the way things work for most Ubuntu users.

---

