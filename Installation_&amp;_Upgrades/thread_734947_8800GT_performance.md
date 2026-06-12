---
title: "8800GT performance"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by Dabbill on 2008-03-25
I have been searching for a few days now, and only coming up with problems installing drivers. Well I am able to install drivers, get my correct resultion to work. Compiz works really well, but I cannot get any type of performance out of games. 

I installed the driver straight from nVidia website.
Current system.

4600+ dual core
2gig RAM
160gig SATAII HD
Asus 8800GT
ubuntu x64

I am getting like the same performace in games as I did when I had my 6600GT card in the computer. Do I need to wait for 8.04 to get any performace out of my card, or is there any thing I can try to getting it to work.

Thanks, Dabbill :)

---

### Post by Wobedraggled on 2008-03-25
Check your xorg.conf (sudo gedit /etc/X11/xorg.conf)


Use the link below and check options, I tweaked mine a bit and got some more juice out of it.
Just be sure to backup the file in case you mess up.


[http://en.wikipedia.org/wiki/Xorg.conf]("http://en.wikipedia.org/wiki/Xorg.conf")

---

### Post by uberlube on 2008-03-25
Use ENVY to install your driver and you will be good to go.

---

### Post by Dabbill on 2008-03-25
Tried ENVY with same resaults. Can get compiz and correct resultion to no video performance at all. I mean i get like I get 10fps in wow 15fps max. I know I should be getting a lot higher then that with my current system.

---

### Post by thisismalhotra on 2008-03-25
> **Dabbill said:**
> Tried ENVY with same resaults. Can get compiz and correct resultion to no video performance at all. I mean i get like I get 10fps in wow 15fps max. I know I should be getting a lot higher then that with my current system.

**What** you get 10fps in wow.. thats sucks knowing that wow is not at all graphics intensive if we compare your card with the specs. I have the same card and a quad core proc but I dont think that matters.. I run easily around 30 - 47fps ...

If you are running wow using wine, I think you are running wow in Direct 3d mode so you need to tweak the wow.conf to use OpenGL and some others tips.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

See if this helps you but I get 10fps in WoW with my Ati Radeon Xpress 200M which is an integrated card.
I would seriously look into it as 10fps with WoW on a 8800 GT is kina really low.

---

### Post by Dabbill on 2008-03-25
Thanks much for that post. I will check in to that once I get home from work today.

---

### Post by Dabbill on 2008-03-26
Thanks for the help with WoW. I am now getting like 30-40FPS. Still not what I should be getting I would think, but surely playable now.

Thanks :)

---

### Post by thisismalhotra on 2008-03-26
> **Dabbill said:**
> Thanks for the help with WoW. I am now getting like 30-40FPS. Still not what I should be getting I would think, but surely playable now.

Thanks :)

How did you install driver??
What is the driver version you installed??

Can you list your lspci enteries over here??

---

### Post by Dabbill on 2008-03-26
I can do a lspci when i get home. I installed the driver from nvidia website, version 169.12 i believe. The newest one. Installed it from command line while gdm was shutdown. Told it to auto update xorg.conf.

---

### Post by Dabbill on 2008-03-26
Nvidia driver version 169.12
Downloaded from nvidia website for 8800GT for Linux_x64
Installed from command line. Did yes to download modules, It compiled the driver cause it couldnt find a precompiled match. Also downloaded and installed some 32bit libs.

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:10.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:11.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:16.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
04:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```

---

### Post by thisismalhotra on 2008-03-27
> **Dabbill said:**
> Thanks for the help with WoW. I am now getting like 30-40FPS. Still not what I should be getting I would think, but surely playable now.

Thanks :)

Just having fun :- but you know human eye can't see above 40fps....:)

---

### Post by thisismalhotra on 2008-03-27
> **Dabbill said:**
> Nvidia driver version 169.12
Downloaded from nvidia website for 8800GT for Linux_x64
Installed from command line. Did yes to download modules, It compiled the driver cause it couldnt find a precompiled match. Also downloaded and installed some 32bit libs.

Everything seems to be fine and you have the latest driver too.. Just to make sure you have 64 bit ubuntu installed right?? cause drive you download was a 64bit driver... Also try uninstalling the driver and installing it again using ENVY ... That usually work better with ubuntu for many people...including me ... 

Also is there any reason you had to download 32 bit libraries cause mixin 32 bit and 64 bit stuff is a MESS??

This thread might help??

[http://ubuntuforums.org/showthread.php?t=686472](http://ubuntuforums.org/showthread.php?t=686472)

Something I found from wine website: -

Open a terminal window, (konsole/terminal/x terminal etc..), type regedit and press enter. This will start the Wine equivalent of the windows registry editor. If you are familiar with using the registry editor under windows then this is pretty much the same.

   1. Find HKEY_CURRENT_USER\Software\Wine\
   2. Highlight the wine folder in the left hand pane by left clicking on it. The icon should change to an open folder.
   3. Click right on the wine folder and select [NEW] then [KEY].
   4. Replace the text "New Key #1" with OpenGL (CaSe Sensitive).
   5. Right click in the right hand pane and select [NEW] then [String Value].
   6. Replace "New Value #1" with "DisabledExtensions" (CaSe sensitive).
   7. Then double click anywhere on the line, a dialog box will open.
   8. In the value field type "GL_ARB_vertex_buffer_object" (without the quotes).

Note: If you are unable to rename the newly created key "New Key #1" to "OpenGL" then expand the left hand pane of the regedit window using the vertical divider bar. You should now be able to change it. A known bug in Wine is causing this unwanted behavior.

You should see a significant performance gain.

---

### Post by Dabbill on 2008-03-27
Yea i found that to make the registry key. I did that before i started wow to get the 30ish fps. 

I do have a 64bit in stall of ubuntu, but use some 32bit codecs and such to get flash and video playback to work.

---

### Post by thisismalhotra on 2008-03-28
I usually get a good 60-70 fps with wow in linux/vista easily on my 8800gt card.. Actually linux one is usually better than windows one.
Did you change the wtf.conf file as said in one if the links I sent you, that the one which really did it for me. The registry key edit did not make a significant change on mine.

How r u checking the fps??

---

### Post by Dabbill on 2008-03-28
I am useing a performance addon built in to titan pannel.
Yes i updated the config file in WTF folder. Forcing it to opengl is what bumped me from 15fps to 40fps, but it has hit as high as 70fps facing a wall lol.

But also I have noticed that wow will lock up after a few hours of raiding while in linux, and when i do crtl+alt+backspace i cant get my desktop to load, it just sticks at the orange screen just after logon. Have to reboot the computer to get my desktop back working.

---

### Post by PmDematagoda on 2008-03-28
Can you please post your xorg.conf file using:-
```
cat /etc/X11/xorg.conf
```

---

### Post by N1N31NCHN41L5 on 2008-03-28
Check out this link, it will walk you through how to tweak WOW for max performance in Wine.

---

### Post by Dabbill on 2008-03-28
Dont look like your link worked.

I will post up my xorg.conf file once i get home. Work blocked port 22 so cant ssh to my linux box any more.

---

### Post by Dabbill on 2008-03-28
resaults of cat /etc/X11/xorg.conf
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Thu Feb 14 18:14:18 PST 2008

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Thu Feb 14 18:13:41 PST 2008
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "1680x1050@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer P221W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 8 Series"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1680 1050
        Depth       24
        Modes      "1680x1050@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050_60 +0+0; 1680x1050@60 +0+0"
EndSection
```

---

### Post by PmDematagoda on 2008-03-28
It seems that you are using a failsafe xorg.conf instead of a normal one.

Switch to a tty using Ctrl+Alt+F1, kill the X-Server using:-
```
sudo /etc/init.d/gdm stop
```

Then reconfigure the X-Server with:-
```
sudo dpkg-reconfigure xserver-xorg
```
and start the X-Server again:-
```
sudo /etc/init.d/gdm start
```

Then see if your FPS problem is solved.

---

### Post by Dabbill on 2008-03-28
Doing that it doesnt dectect my video card correctly, and trys to use the NV driver. It also dont seem to detect my monitor correct. I have to go in to the nvidia-settings window and reset my resultion to 1680x1050. Also my FPS in WoW seems to be about the same after reconfiguring xorg.conf like you suggested.

---

### Post by PmDematagoda on 2008-03-28
Do this:-

1) Open a modules file for editing with:-
```
sudo gedit /etc/default-linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```

3) Save the file, reboot the PC and then try reconfiguring the X-Server again.

---

### Post by Dabbill on 2008-03-28
when i open that file its blank. So should i just add that line in it?

---

### Post by PmDematagoda on 2008-03-29
Oops, I made a mistake, the command is:-
```
sudo gedit /etc/default/linux-restricted-modules-common
```

Really sorry for the mistake.:oops:

---

### Post by Dabbill on 2008-03-29
Edited that file like you said and reconfigured xorg. Now when i restart the computer i cant get any thing past my login screen to load. It just stays at this orangish pink screen. Finally after a full reboot of the computer i got my desktop back up. As far as i can tell WoW is still running the same.

---

### Post by PmDematagoda on 2008-03-29
Could you please post your new xorg.conf file again.

---

### Post by Dabbill on 2008-03-29
xorg.conf right now
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:3:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-84
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NVIDIA Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1680x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection
```


This was with it trying to auto detecting every thing.
Any thing i need to change in this, or any thing look wrong?

---

### Post by Dabbill on 2008-04-01
bump?

Sorry for the bump, was told to post the code but havent gotten a reply.

---

### Post by thisismalhotra on 2008-04-01
> **Dabbill said:**
> bump?

Sorry for the bump, was told to post the code but havent gotten a reply.

I don't know if this helps but your real problem maybe the latest nvidia driver.. what happened is I had a perfect working Linux installation with WoW working and all the special effects etc...etc.. with the driver version 169.09 installed through ENVY.

Since I read from your post that new drivers have come out I went ahead and upgraded to that one. Same as you the driver had to compile itself to be installed on my system. And now my PC wont even boot up into a graphical login it says X11 error. I uninstalled the driver and tried to install the older one but nothing works. I can not even manually start X as it gives error. I think when the driver compiles it makes   some changes just particular to your system which can not be undone... 

I would give a shot to the older driver and see if that works, also in WINE use Win XP settings and not VISTA for WoW.
Please dont feel I am trying to blame you, just wanted to share what happened to me..

---

### Post by Dabbill on 2008-04-01
I have wine set to use XP for every game i believe, but i will also give that driver a try. Thanks for the info. Will let ya know what happens.

---

### Post by Dabbill on 2008-04-01
Where can i get the older version of envy for 169.09 driver. All i can find is the envy with 169.12 driver.

---

### Post by stchman on 2008-04-01
> **Dabbill said:**
> I have been searching for a few days now, and only coming up with problems installing drivers. Well I am able to install drivers, get my correct resultion to work. Compiz works really well, but I cannot get any type of performance out of games. 

I installed the driver straight from nVidia website.
Current system.

4600+ dual core
2gig RAM
160gig SATAII HD
Asus 8800GT
ubuntu x64

I am getting like the same performace in games as I did when I had my 6600GT card in the computer. Do I need to wait for 8.04 to get any performace out of my card, or is there any thing I can try to getting it to work.

Thanks, Dabbill :)

I run Feisty and an 8800GT.  I installed Envy 0.9.10 and did the manual install of the 169.12 drivers.

My new LCD widescreen monitor has a native 1920x1200 so I added "1920x1200" as first in the line of resolutions in my xorg.conf file.

Very easy.  Google Earth works perfectly and the openGL games I play.

---

### Post by thisismalhotra on 2008-04-02
> **stchman said:**
> I run Feisty and an 8800GT.  I installed Envy 0.9.10 and did the manual install of the 169.12 drivers.

My new LCD widescreen monitor has a native 1920x1200 so I added "1920x1200" as first in the line of resolutions in my xorg.conf file.

Very easy.  Google Earth works perfectly and the openGL games I play.

Can you please post your xorg.conf file so that I can use it to fix my PC. Thanks

---

### Post by Dabbill on 2008-04-02
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Fri Jan 11 14:26:48 PST 2008

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier      "Default Layout"
  screen "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
        Load            "glx"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
EndSection

Section "InputDevice"
        Identifier      "stylus"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "eraser"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "cursor"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Horizsync       28.0    -       84.0
        Vertrefresh     43.0    -       60.0
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "nVidia Corporation NVIDIA Default Card"
        Driver          "nvidia"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NVIDIA Default Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1680x1050"
        EndSubSection
        Option          "AddARGBGLXVisuals"     "True"
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection
```

---

### Post by Dabbill on 2008-04-04
Tried using the newest ENVY. Also installed the driver downloaded straight from nVidia. It just sees it as a generic nvidia card. Compiz works and google earth seem to work well, but still not getting the perforamce i should be from might and magic, or WoW.

Am i just kind of out of luck till 8.04 is fully released or nvidia releases a new driver?

---

### Post by thisismalhotra on 2008-04-04
whats ur FPS in wow now?? 
R u measuring it from the blizzard UI or some other tool ... If I remember you are using some other tool, what does blizzard UI says about the fps??

---

### Post by Dabbill on 2008-04-04
Been useing an addon called Titan panel to judge my FPS and compairing it to my other windows PC thats close in stats for proccessing power. Both useing the same list of addons.

---

### Post by thisismalhotra on 2008-04-05
with titan panel you still have Blizzard UI, so just mouse over that green bar, right next to the bags and see what that says for FPS, also what is your monitors native resolution and what is your resolution insiade the game??

Please post you wow.wtf file here too?? and version of WINE and are you using windows xp settings in wine or windows vista??

Try nvidia website for 64bit 169.09 driver, I am still running those?? (finally got my system back up) .. one more things did you install ENVY legacy or ENVYNG??

Also, I assume you are using 64 bit version of all these?? What is your FPS now, still at 30 ??

---

### Post by Dabbill on 2008-04-05
I dont use the blizard stock bars. I use bartender. Both my windows PC and Linux PC have 22" wide screen running at 1680x1050. In the same area my windows PC gets 60fps, where my linux box is getting 25fps.

I have the newest wine that came out through the built in updates. Also downloaded the legacy version of ENVY. Yea they are all 64bit versions also.

Windows PC
6000+ dual core.
4gig Ram
8800GTX

Linux PC
4600+ dual core.
2gig Ram
8800GT

I will post up the wow config file once i get home.

---

### Post by Dabbill on 2008-04-05
```
SET locale "enUS"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1680x1050"
SET gxRefresh "50"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET movie "0"
SET expansionMovie "0"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET farclip "777"
SET particleDensity "1.000000"
SET groundEffectDensity "64"
SET realmName "Ner'zhul"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET gameTip "88"
SET gxWindow "1"
SET gxMaximize "1"
SET textureFilteringMode "5"
SET checkAddonVersion "0"
SET Gamma "1.000000"
SET Sound_MasterVolume "0.050000011920929"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET shadowLevel "0"
SET groundEffectDist "140"
SET weatherDensity "3"
SET CombatHealing "0"
SET uiScale "0.81000000238419"
SET useUiScale "1"
SET mouseSpeed "1"
SET profanityFilter "0"
SET cameraYawMoveSpeed "150"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1.7999999523163"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET UnitNameOwn "1"
SET UnitNameNPC "1"
SET autoSelfCast "1"
SET guildMemberNotify "1"
SET SlideBarConfig "anchor=right;position=221.03702330622"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET Sound_EnableReverb "1"
SET Sound_EnableHardware "1"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_ZoneMusicNoDelay "1"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET DesktopGamma "1"
SET gxTripleBuffer "1"
SET Sound_EnableErrorSpeech "0"
SET ffxGlow "0"
SET reamlist "127.0.0.1"
SET accountName "dabbil"
SET cameraView "3"
SET Sound_EnableAmbience "0"
SET ffxDeath "0"
SET cameraPitchMoveSpeed "75"
SET cameraPitchSmoothSpeed "45"
SET questFadingDisable "1"
SET autoQuestWatch "0"
SET fctLowManaHealth "1"
SET fctHonorGains "1"
SET fctAuras "1"
SET showPartyDebuffs "0"
SET PetMeleeDamage "0"
SET cameraWaterCollision "0"
SET cameraPivot "0"
SET CombatDamage "0"
SET CombatLogPeriodicSpells "0"
SET ChatBubblesParty "1"
SET assistAttack "1"
SET showChatIcons "1"
SET gxApi "opengl"
SET gxCursor "0"
```

That is my Config.wtf file from WTF folder.

Wine version 0.9.58

---

### Post by thisismalhotra on 2008-04-07
Read this page maybe would help,

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

I run wow on 32 bit ubuntu, and I have 22'widescreen on 1680x1050. The only difference between you and me is I have copied the wow folder from my windows installation.

Your config file looks fine but here is mine just in case you want to use and try...

---

### Post by Dabbill on 2008-04-07
I have tried useing a install copied over from my windows computer. Also does fresh install on linux box. Still same performance. :(

---

### Post by thisismalhotra on 2008-04-08
> **Dabbill said:**
> I have tried useing a install copied over from my windows computer. Also does fresh install on linux box. Still same performance. :(

Here are some more performance tweaks from the link below(also contains info how to strat wow on a dedicated X session);

[http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

** Performance Tweaks**
**Kernel Boot Parameter**

Users of nvidia 8800 GTS and GTX cards have reported significant performance increases (around 10-30 fps improvements) by adding the vga=normal boot option on kernels 2.6.22 and 2.6.23.

**OpenGL Registry Edit**

A common performance tweak for wine and opengl games is a registry edit. While your results may vary, many users report up to a 100% increase in framerate with no loss of stability. To make this change, do the following:

   1. Open regedit (regedit)
   2. Navigate to HKEY_CURRENT_USER\Software\Wine\
   3. Right click on the wine folder and select [NEW] then [KEY].
   4. Replace the text New Key #1 with OpenGL (case sensitive).
   5. Right click in the right panel and select [NEW] then [String Value].
   6. Replace the text New Value #1 with DisabledExtensions (case sensitive).
   7. Now right click on DisabledExtensions and select Modify
   8. A dialog box should appear. In the value field type GL_ARB_vertex_buffer_object 
[B]
Startup Script[/B]

The idea for this tweak is to create a script which will allow you to launch WoW on a dedicated X server, and will give you a little FPS boost (up to 10-15fps).

    * Start by creating the script: nano -w ~/launch-wow.sh
    * Paste the following in the script: 

Code: ~/launch-wow.sh

 #!/bin/sh

 export WOW_PATH=~/".wine/drive_c/Program Files/World of Warcraft" # Installation path

 X :3 -ac -terminate &   # Launch on a new X session on display 3
 cd "${WOW_PATH}"        # Goto WoW dir 
 sleep 2
 DISPLAY=:3 `which wine` WoW.exe -opengl # Launches WoW

    * Press Ctrl+O then Ctrl+W to save and quit nano.
    * Make your script executable: chmod +x ~/launch-wow.sh 

**Enabling hardware rendering**

You should verify that you are actually rendering the game with OpenGL, not just software. If you are getting 1 FPS or the game is virtually unplayable, you're probably using software rendering. To switch to hardware/OpenGL rendering, run the following command as root:

**For nVidia Cards: eselect opengl set nvidia**

[B]For ATi Cards: eselect opengl set ati
[/B]
Exit X, Log out and back in, then start X again. Startup WoW, and you should be fine. See [http://forums.gentoo.org/viewtopic-t-448436-start-375.html](http://forums.gentoo.org/viewtopic-t-448436-start-375.html).
[edit] Config.wtf Tweaks
Warning: You need to run WoW at least once and log into a character so a Config.wtf file can be created.

The Config.wtf file is located in the WTF folder in your WoW installation. By default, this location is /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/.
[B]
OpenGL[/B]

Instead of launching WoW with the -opengl switch, you can make the change permanent by adding the following line:

```
SET gxApi "opengl"
```

---

### Post by Dabbill on 2008-04-16
I installed XP on to my linux computer on another HD. Opened wow and it was kinda laggy about the same performance as in Linux, but remember that i had it set to opengl in the config file. Took the opengl tag out of the file and wow ran really smooth with no lag. Wonder if this card just doesnt like opengl or some thing.

---

