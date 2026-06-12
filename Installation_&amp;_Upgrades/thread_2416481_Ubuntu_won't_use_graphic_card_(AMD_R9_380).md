---
title: "Ubuntu won't use graphic card (AMD R9 380)"
date: 2019-04-10
forum: Installation &amp; Upgrades
---

### Post by tempest-anastasia on 2019-04-10
Hi Everyone and thank you for taking the time to help me with this question.

I have been trying to install some form of Linux on my desktop computer for over a week now.  I have some major concerns with Windows 10 and I really would like to use something else, but I'm starting to worry that this computer might just never be able to take it. I have tried to boot Ubuntu, Linux Mint and Fedora but the same thing happens with all of them.

I am trying to install on a Chillblast Fusion NightHawk Gaming PC, it has a Intel Core i5 4460 3.2GHz and a AMD Radeon R9 380 4GB and it seems that Linux does not want to output through that card. The PC is connected to a FLATRON E2211 monitor through the graphics card.

In order to see a desktop at all I have to unplug my monitor from the graphics card and plug it into the on board slot.

I can then run Ubuntu off the USB stick but it is incredibly sluggish and I am wondering if my hardware is going to be causing me a lot of issues going forward even if I can get it to run (I expect as it is an old gaming PC the hardware is mostly designed for windows).

My current goal is to try and get the Live USB stick to use my graphics card because I don't want to wipe my working system off to replace it with something that isn't working. I suppose I could just run it with my on board graphics however it feels like an incredible waste but it is potentially a sacrifice I might consider making.

I don&#8217;t understand why grub is happy to output through the card but not Ubuntu (or the other distros I&#8217;ve tried) I feel like maybe the distro is choosing to only output through the onboard and I need to edit some text file somewhere and change it to using the card but I have no idea where to even start looking for that unfortunately /etc/?

I have been having some issues trying to install the AMD drivers on the live USB stick, here is my process:


[LIST]
[*]I downloaded the 18.04.2 desktop AMD Ubuntu iso
[*]I used lili.exe to make the USB stick, just using the default value: ( [IMG]https://imgur.com/RaPu2Eg[/IMG][IMG]https://imgur.com/RaPu2Eg[/IMG]https://imgur.com/RaPu2Eg )
[*]Rebooted -> USB stick boot
[*]Saw the GNU Grub v2.02 -> Try without installing.
[*]Monitor switches itself off (no input)
[*]I unplug the monitor from the graphics card and into the on board slot, see the beaver wallpaper. It's really really sluggish though, takes ages to boot
[*]I downloaded the AMD R9 380 Drivers.
[*]Extract them, try to follow the doc folder installation instructions but it's about ubuntu 14. No longer relevant.
[*]I type ./amdgpu-pro-install get errors:
[/LIST]

```
ubuntu@ubuntu:~/Downloads/amdgpu-pro-18.50-756341-ubuntu-18.04$ ./amdgpu-pro-installdeb [ trusted=yes ] file:/var/opt/amdgpu-pro-local/ ./
Ign:1 cdrom://Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210) bionic InRelease
Get:2 file:/var/opt/amdgpu-pro-local ./ InRelease
Ign:2 file:/var/opt/amdgpu-pro-local ./ InRelease
Hit:3 cdrom://Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210) bionic Release
Get:4 file:/var/opt/amdgpu-pro-local ./ Release [816 B]
Get:4 file:/var/opt/amdgpu-pro-local ./ Release [816 B]                                                                           
Get:5 file:/var/opt/amdgpu-pro-local ./ Release.gpg                                                                                                        
Ign:5 file:/var/opt/amdgpu-pro-local ./ Release.gpg                                                                               
Hit:6 http://archive.ubuntu.com/ubuntu bionic InRelease                                                                           
Hit:7 http://archive.ubuntu.com/ubuntu bionic-updates InRelease                                                                   
Hit:9 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Reading package lists... Done                      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
amdgpu-pro-pin is already the newest version (18.50-756341).
Selected version '18.50-756341' (localhost [all]) for 'amdgpu-pro-pin'
0 upgraded, 0 newly installed, 0 to remove and 224 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 amdgpu : Depends: amdgpu-lib (= 18.50-756341) but it is not going to be installed
 amdgpu-lib32 : Depends: amdgpu-lib (= 18.50-756341) but it is not going to be installed
                Depends: libdrm2-amdgpu:i386 (= 1:2.4.95-756341)
                Depends: libdrm-amdgpu-amdgpu1:i386 (= 1:2.4.95-756341)
                Depends: libllvm7.0-amdgpu:i386 (= 1:7.0-756341)
                Depends: libwayland-amdgpu-client0:i386 (= 1.15.0-756341)
                Depends: libwayland-amdgpu-server0:i386 (= 1.15.0-756341)
                Depends: libwayland-amdgpu-egl1:i386 (= 1.15.0-756341)
                Depends: libxatracker2-amdgpu:i386 (= 1:18.2.0-756341)
                Depends: libgbm1-amdgpu:i386 (= 1:18.2.0-756341)
                Depends: libegl1-amdgpu-mesa:i386 (= 1:18.2.0-756341)
                Depends: libegl1-amdgpu-mesa-drivers:i386 (= 1:18.2.0-756341)
                Depends: libgles1-amdgpu-mesa:i386 (= 1:18.2.0-756341)
                Depends: libgles2-amdgpu-mesa:i386 (= 1:18.2.0-756341)
                Depends: libglapi-amdgpu-mesa:i386 (= 1:18.2.0-756341)
                Depends: libgl1-amdgpu-mesa-glx:i386 (= 1:18.2.0-756341)
                Depends: libgl1-amdgpu-mesa-dri:i386 (= 1:18.2.0-756341)
                Depends: libosmesa6-amdgpu:i386 (= 1:18.2.0-756341)
                Depends: mesa-amdgpu-va-drivers:i386 (= 1:18.2.0-756341)
                Depends: mesa-amdgpu-vdpau-drivers:i386 (= 1:18.2.0-756341)
 amdgpu-pro-lib32 : Depends: libgl1-amdgpu-pro-glx:i386 (= 18.50-756341)
                    Depends: libegl1-amdgpu-pro:i386 (= 18.50-756341)
                    Depends: libgles2-amdgpu-pro:i386 (= 18.50-756341)
                    Depends: libglapi1-amdgpu-pro:i386 (= 18.50-756341)
                    Depends: libgl1-amdgpu-pro-dri:i386 (= 18.50-756341)
                    Depends: libgbm1-amdgpu-pro:i386 (= 18.50-756341)
 vulkan-amdgpu-pro:i386 : Depends: libc6:i386 (>= 2.17) but it is not installable
                          Depends: libgcc1:i386 (>= 1:3.3.1) but it is not installable
                          Depends: libstdc++6:i386 (>= 4.8) but it is not installable
                          Depends: wsa-amdgpu:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```

I'm wondering if I'm getting these errors because I'm running in a live environment? And even if I can get these errors fixed and the driver installed is it likely to fix the fact that the graphics card isn't outputting? And should the fact that the USB stick is running so sluggishly be a red flag?

I expect that these errors are due to some rookie mistake and they are probably easily fixable. My concern however is more that Grub can use my graphics card but Ubuntu (and other distros) can't. I could be wrong but it was my understanding that graphics cards can output at least something without a driver, just with out any of the advanced features so I'm wondering if there is something in Ubuntu that's making it choose not to use my card and to output only from the on board. Is there a file somewhere that you have to edit with a text editor which allows you to choose which device to use? I wouldn't know where to look for such a thing but it does seem quite often that's the way you fix things in Linux. 

Thanks once again for your help and I'm sorry this post is so long. I expect I'm doing something really stupid and obviously wrong.

I hope you have a great week.

Take care

Tempest

---

### Post by Autodave on 2019-04-10
First off, it will be sluggish running off of a USB stick.

What puzzles me is that you say that you installed the AMD-GPU drivers?  For that card, you should not need to install any driver since Ubuntu comes with the drivers that you need.

I see all the dependencies that are missing, so it is no wonder that the AMD card isn't working properly.  Have you tried booting from the install medium w/o installing anything?  It should just work.  You may want to try another download to make sure that your's wasn't corrupted.

Linux isn't Windows: generally, every driver you will need is included already.

---

### Post by tempest-anastasia on 2019-04-10
I understand that Linux tends to have many drivers so I was expecting some functionality from it but as I say the monitor just switches itself off because it isn't receiving any input at all. I guess I could try downloading a fresh iso but this has happened with all 3 of the flavours of mint, fedora workstation and vanilla Ubuntu. I don't think it's a corrupted iso this seems to be a consistent issue across many if not all distros. 

A lot of the files that are dependencies are part of the tar ball, I think the auto install script may have been written for an earlier version of Ubuntu, but as you say it does come with some drivers so I should be expecting some output.

Is there an application I can download that scans my hardware and lets me know if there is a specific part of it that is incompatible? 

If this is unfix-able then do you have any advice for me going forward? Should I just forget about my graphics card and use my onboard? I might even just downgrade back to windows 7. It's out of support but it didn't spy quite as much or have as much ad ware.

Edit: I found this article which seems to suggest that Ubuntu defaults to the intel on board graphics, sadly it's asking for a nvidia gui to be downloaded [https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu](https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu) It's not a laptop but could something similar be going on?

Edit 2: So I thought I'd try plugging my monitor into my Linux mint laptop and it works fine. One thing I should mention though is that the graphics card is expecting DVI inputs but my monitor is VGA and I'm having to use an adapter. Is that something that can mess up Linux?

Edit 3: My graphics card has HDMI outputs. I carried the pc to my TV and I managed to get it to output there. It was running SIGNIFICANTLY smoother as well through the TV in fact so much so I don't think I could bear to run through my onboard. I guess this means theres something either up with the adapter or the way that Linux outputs DVI. I just don't know why it works for windows but not Linux :/

There are 2 DVI ports on the graphics card however one of them has what looks like a minus next to the bank of pins and one has what looks like a plus next to the bank of pins. The adapter is set up in such a way that it won't go into the minus. I would love to try it in the other slot but the adapter just won't go. I really don't know what I can do about that though. I think until I can afford a new monitor I'm going to have to go back to windows sadly. I do want to learn Linux though and I'll probably end up running Ubuntu in a full screen VM.

Edit 4: I found some guides about people who were struggling with having too low resolution and how to use xrandr. I’ve followed along but to no prevail sadly. According to xrandr the dvi ports are both disconnected. I have absolutely no idea what’s up with that seeing how my bios grub and windows can all use it no problem :(

---

### Post by tempest-anastasia on 2019-04-14
Something I've noticed is that my monitor will say check signal cable if its unplugged. However, just plugging it into the adapter makes that message go away so I'm thinking now it might be something to do with the monitor. I've gone on to amazon and bought a £5 VGA/DVI cable. Going to see if that fixes it, if not then I dunno I guess I will have to buy a new monitor. It's such a weird issue...

I'll update this when it comes along, and if it fixes it I'll set this as solved.

---

### Post by QIII on 2019-04-14
Don't bother buying anything!  That is not the problem.

Your BIOS/EFI should give you the option to choose between the dedicated or integrated (on the i5) GPUs.  Make sure that it is set to use the dedicated graphics.  That will push the machine to the AMD GPU.  If you are only getting a signal from the on board graphics connections, then the Intel graphics are being used and the AMD card is not active.

The R9 380 works perfectly without having to mess with the driver.  I have one on one of my machines.  For GPUs supported by AMDGPU, the amdgpu module is active at install and will be loaded on startup.  For GPUs not supported, the radeon module will be used.  The only reason you might need to worry about anything is if you specifically need the add-on AMDGPU-PRO overlay for AMDGPU.

Is this a fairly new installation of Ubuntu?  Are your multi-booting?

---

### Post by tempest-anastasia on 2019-04-14
I tried disabling integrated GPU and telling my bios to only use the graphics card, it didn't help though, still wouldn't output when it got passed grub. This is such a weird problem it really is.

This is a live USB stick of Ubuntu. I did try installing it using the on board to see what I was doing but that still didn't help :(.

---

### Post by tempest-anastasia on 2019-04-24
I&#8217;m still having this issue sadly. The new cable didn&#8217;t help, I think over the weekend I&#8217;ll try to take photos of all my bios screens and share them. I&#8217;ve been trying to trial and error it this evening but no joy yet. I&#8217;m still really really really confused as to why it seems to output the hdmi part of the card but not the dvi :( could this be a setting or worse a bug that&#8217;s present within the Linux kernel or drivers? I was wondering if there is another gratis os I could grab and try out that didn&#8217;t use the Linux kernel (does bsd for instance, use the Linux kernel?) it just bothers me how windows seems to cope 

I dunno...I&#8217;m starting to worry this machine might not be able to take it which is really sad as I absolutely love running Linux on my laptop but maybe there is something weird interfering with it in the bios. There&#8217;s an awful lot of acronyms that don&#8217;t make much sense to me even after googling them.

---

### Post by CatKiller on 2019-04-24
> **tempest-anastasia said:**
> Edit 2: So I thought I'd try plugging my monitor into my Linux mint laptop and it works fine. One thing I should mention though is that the graphics card is expecting DVI inputs but my monitor is VGA and I'm having to use an adapter. Is that something that can mess up Linux? 

Yes. Monitor and resolution detection uses [EDID](https://en.wikipedia.org/wiki/Extended_Display_Identification_Data). Many adaptors will not pass that information along. In addition, many older monitors had missing or false EDID values. 

> There are 2 DVI ports on the graphics card however one of them has what looks like a minus next to the bank of pins and one has what looks like a plus next to the bank of pins. The adapter is set up in such a way that it won't go into the minus. I would love to try it in the other slot but the adapter just won't go.

There is a reason it doesn't fit: it wouldn't help you. VGA, being an analogue signal, uses the analogue pins around that key. You're *only* using those pins. The digital signal pins aren't being used at all by your adaptor. You should be able to see that the connector that only has digital connection pins and no analogue ones is of no use to you with your VGA monitor. I'm guessing that it's pretty old.

It's going to say that the DVI ports aren't connected to anything, because there's nothing saying that it is connected. The monitor may be able to give that signal, or it might not, but it's not being passed through your adaptor anyway. HDMI gives a better quality signal, so that's the default if both are available. Regardless, you should be able to send the output through the DVI port, either with the display settings of your graphical environment, or through xrandr, or through xorg.conf.

---

### Post by tempest-anastasia on 2019-04-25
Thanks for the reply

I haven't been able to find a setting in the GUI as of yet, I went through all the settings and it's either not there or I really did miss it.

I suspect it's not passing information on, xrandr seems to think its a 4:3 monitor even though its 1080p. Because it's a flat 1080p I wouldn't have thought it was that old, although I did buy it a few years ago and it was for a low price as it was probably discontinued its not like it's a big CRT either, but I guess technology moves on very quickly. I don't really know much about xrandr but I'll read through the man page and see if there is something there I could use.

Hopefully I can find something in the xorg.conf file. Do you have any idea what I might be able to look for? My plan is to hopefully search for "HDMI" and see if anything comes up. I'll have to do all this at the weekend though because I don't have access to it at the moment.

I'm wondering if the reason it works for windows is because windows just outputs through every port by default. Whereas Linux maybe has a more use as little as is needed approach? 

I can see the grub launcher, does that hold a bunch of init scripts as well? Is there something there that might need to be looked at?

Many thanks

---

### Post by CatKiller on 2019-04-25
> **tempest-anastasia said:**
> Hopefully I can find something in the xorg.conf file. Do you have any idea what I might be able to look for? My plan is to hopefully search for "HDMI" and see if anything comes up.

You probably won't have an xorg.conf file. Auto-detection is used instead and, at the moment, you don't have anything it can use to auto-detect with unless you're using HDMI with your TV.

However, xorg.conf *will* be used if it's there. You'll need to specify the output that you're using and the resolution that you need to use, and any other information that might help the auto-detection along. Basically, all the stuff that would be available if EDID was working.

---

### Post by mastablasta on 2019-04-26
> **tempest-anastasia said:**
> 
I'm wondering if the reason it works for windows is because windows just outputs through every port by default. Whereas Linux maybe has a more use as little as is needed approach? 


by default it doesn't. i have nvidia that has HDMI, VGA and DVI port. and by default output is on DVI. so BIOS, GRUB... all until the system GUi loads is on TV. after that it switches to my VGA monitor, which i set as primary and default display. same happens in windows which is on the other hard drive. i see nothing on monitor (and TV is off) until it starts loading the windows GUI. i was puzzled lately to see some games when switched to full screen to move themselves to a disabled display while switching off primary monitor.

---

### Post by tempest-anastasia on 2019-04-26
I think there's a way of getting x.org to generate a conf file. I'm just wondering what the best way of going about this is. Should I plug it into my television first so it tries to auto fill and tweak those settings? Or should I just leave it as it is and have it generate one while the monitor is switched off? I'm still a huge rookie to all this and a lot of this is going over my head but I'm learning a lot in the process. I don't really know how I would do it with the monitor switched off. I know a little bit about SSH and I have a working Mint laptop, but I don't think the live USB allows you to ssh into it without changing things first does it? And changing things without the monitor might be tricky to impossible. Unless there's some files on the USB stick I can tweak first? I know with the raspberry pi you can just create a blank file called ssh to set it up headlessly, is there something similar that can be done with the ubuntu install?

---

### Post by CatKiller on 2019-04-26
I wouldn't trust anything to auto-generate an xorg.conf. Particularly when the main issue you're having is that auto-detection doesn't work in the first place.

A skeleton xorg.conf might look something like

```

Section "Device"
    Identifier "Default Device"
EndSection

Section "Monitor"
    Identifier "Default Monitor"
    HorizSync www-xxx
    VertRefresh yyy-zzz
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device "Default Device"
    Monitor "Default Monitor"
EndSection

```

The HorizSync and VertRefresh values you could get from the monitor's manual or specifications, or copy them from the specs of a different monitor of the same size & resolution. Those are the most important bits of the EDID information for saying which resolutions your monitor can do. It's not *essential* to have those values in there, but it will make your life easier.

You can specify different options for different outputs; you could have one set of options for your DVI output and your HDMI output, say. **man xorg.conf** tells you about all the configuration options you can put in there, and the structure, and so on.

In your position, I would probably try to set up a dual-screen with the TV - so that I could see what I was doing - and then, once I'd brought the monitor to life, stop using the TV. Configuring an installed system will be easier than configuring a live session, since you won't have to keep redoing it each time you reboot the computer. Live sessions don't save anything.

To be able to SSH to a computer, you just need to install the openssh-server package. Obviously for a live session you'd need to install that package every time.

---

### Post by tempest-anastasia on 2019-04-26
So by plugging my monitor into the onboard I managed to generate an xorg.conf file.

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
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
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
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

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "Accel"                  # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "AccelMethod"            # <str>
        #Option     "DRI3"                   # [<bool>]
        #Option     "DRI"                    # <i>
        #Option     "ShadowPrimary"          # [<bool>]
        #Option     "TearFree"               # [<bool>]
        #Option     "DeleteUnusedDP12Displays"     # [<bool>]
    Identifier  "Card0"
    Driver      "amdgpu"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "Accel"                  # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "AccelMethod"            # <str>
        #Option     "DRI3"                   # [<bool>]
        #Option     "DRI"                    # <i>
        #Option     "ShadowPrimary"          # [<bool>]
        #Option     "TearFree"               # [<bool>]
        #Option     "DeleteUnusedDP12Displays"     # [<bool>]
    Identifier  "Card1"
    Driver      "amdgpu"
    BusID       "PCI:1:0:1"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "Accel"                  # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "Backlight"              # <str>
        #Option     "CustomEDID"             # <str>
        #Option     "DRI"                    # <str>
        #Option     "Present"                # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "HWRotation"             # [<bool>]
        #Option     "VSync"                  # [<bool>]
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "ReprobeOutputs"         # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "VirtualHeads"           # <i>
        #Option     "TearFree"               # [<bool>]
        #Option     "PerCrtcPixmaps"         # [<bool>]
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "BufferCache"            # [<bool>]
    Identifier  "Card2"
    Driver      "intel"
    BusID       "PCI:0:2:0"
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

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
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

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
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

I tried to follow the man page for xorg.conf but I'm afraid this stuff is far beyond me :( Parts of it seem to be beyond the person who wrote the man page as well! (I.E the VIDEOADAPTOR section). I'm guessing I need to change the device or the screen section but I have no idea what to. I am starting to feel like we're getting somewhere now though.

---

### Post by tempest-anastasia on 2019-04-26
Sorry CatKiller I wasn't ignoring you I think we must have posted at exactly the same time. I'll try to find out the monitor specifications and see what needs changing. I think I need a little bit of a break for a while though, I'm starting to get a bit of a headache with all this new information that's coming in!

Edit: I restarted x using your skeleton xorg.conf with the values from the manual and sadly it didn’t help. I’m sorry but this really is feeling like it’s way beyond what I can do now. I think I’m just going to have to buy a new monitor. I think I’m going to leave this up for the weekend but after that I think I’m just going to have to go back to windows 10 in the meantime. There’s a few hdmi monitors on amazon I might be able to afford one at the end of the month, it will probably be a heck of a lot nicer anyway so it’ll probably be worth it in the long run :3

---

### Post by CatKiller on 2019-04-26
Yeah, you're starting from a really hard place. Your monitor's VGA, which is before monitor manufacturers started taking EDID seriously, and you don't even have all the VGA pins available because you're going through the adaptor. Auto-detection makes this *all* a lot easier.

If you do persevere with that monitor while you're waiting for a new one, you don't need to specify everything in your xorg.conf. If you're going for a single file (widespread autodection means that you can get away with just snippets in xorg.conf.d for some things these days) the main thing is that the bits you do have are self-consistent. Bear in mind the kinds of graphics cards that were available in 1984 (when X11 was invented) and came and went since (like AGP and 3D accelerator cards); that's why a lot of the old-and-crusty options exist.

The Device section specifies the options for the graphics card. So that might be things like the bus-id, to identify it if you have more than one device (which you do), the driver that you want to use to control that device, and other options.

The Monitor section specifies the options for the monitor. So things like resolution/timings, how many colours, which port it's attached to, and so on.

The Screen section is the abstract thing that ties everything together. *This* monitor, attached to *this* device, has *these* properties.

You can have multiple entries for all of those, but each Screen needs one Monitor and one Device. You can call any of them whatever you like - the Identifier entries - as long as you use the same Identifier to refer to the same thing. So if you called one monitor, "My HDMI television," say, that would be fine as long as whichever Screen you'd defined to use it also referred to "My HDMI television."

lspci will tell you the bus-ids, and xrandr should tell you what the outputs are called as far as the computer is concerned.

The only reason I know about any of this stuff is because the monitor I was using when I first started using Ubuntu lied in its EDID. I wasn't in as awkward a position as you, though: I got an image, it was just at the wrong resolution. Your situation is a tougher nut to crack.

---

