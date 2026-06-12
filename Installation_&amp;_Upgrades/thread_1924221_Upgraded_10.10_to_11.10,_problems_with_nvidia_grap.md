---
title: "Upgraded 10.10 to 11.10, problems with nvidia graphics &amp; more"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by lindsayward on 2012-02-12
Hi. I decided to do a couple of dist-upgrades and take my machine from 10.10 to 11.10, and now it's a bit stuffed. I have looked at lots of help discussions and tried most things I found there. I'd appreciate any help with my situation.
I use my computer almost entirely for MythTV and just want to get that back working again.

Currently, it hangs at boot and I can Ctrl+Alt+F1 to get to a tty window, where I see the last thing was:

Stopping System V runlevel compatibility

When I log in, I can startx, but the desktop and interface is very plain and 'old' looking. I can run MythTV but it won't play videos. I don't seem to have any audio either (there was no HW device in the sound options panel).

I have tried purging nvidia-* and then installing nvidia-common, and I have tried (current situation) installing nvidia-173 (based on some other posts). I don't know what version I should be using. I have an onboard 9400 card (DFI Lanparty mobo).

I have tried adding the x-swat ppa and editing some blacklist files and grub (but not downloading from nvidia's site directly). 

So now I'm not sure whether to keep trying to get the graphics and other things going again or try some kind of 'downgrade' or reinstall.
(I have all of my MythTV recordings in my home directory, so backing that up would need a big disk and I fear losing my database for this.)

Thanks in advance (from my wife!) for your help.

---

### Post by MAFoElffen on 2012-02-12
> **lindsayward said:**
> Hi. I decided to do a couple of dist-upgrades and take my machine from 10.10 to 11.10, and now it's a bit stuffed. I have looked at lots of help discussions and tried most things I found there. I'd appreciate any help with my situation.
I use my computer almost entirely for MythTV and just want to get that back working again.

Currently, it hangs at boot and I can Ctrl+Alt+F1 to get to a tty window, where I see the last thing was:

Stopping System V runlevel compatibility

When I log in, I can startx, but the desktop and interface is very plain and 'old' looking. I can run MythTV but it won't play videos. I don't seem to have any audio either (there was no HW device in the sound options panel).

I have tried purging nvidia-* and then installing nvidia-common, and I have tried (current situation) installing nvidia-173 (based on some other posts). I don't know what version I should be using. I have an onboard 9400 card (DFI Lanparty mobo).

I have tried adding the x-swat ppa and editing some blacklist files and grub (but not downloading from nvidia's site directly). 

So now I'm not sure whether to keep trying to get the graphics and other things going again or try some kind of 'downgrade' or reinstall.
(I have all of my MythTV recordings in my home directory, so backing that up would need a big disk and I fear losing my database for this.)

Thanks in advance (from my wife!) for your help.
LOL... Yes, have to keep wives happy. 

NVidia 9400 = nvidia-current as a driver. Install directions? Could use Jockey in System Settings > Additional Drivers or from a terminal
```

gksudo jockey-gtk

```
Or use any of the command line tutorials I wrote, linked from this Post:
[Sticky- Graphics Resolution: Table Of Contents]("http://ubuntuforums.org/showpost.php?p=10740087&postcount=2")

Stopping at the message "Stopping System V runlevel compatibility"... 95% of the time this means that either the video driver is not installed or that there is a problem with the video driver and that it is not loading.

I'm hoping that info can get you started, but if you have any questions, please ask. I'm here to help.

---

### Post by lindsayward on 2012-02-12
Thank you for your reply. Nice to have an expert on my case!
I think I do have the nvidia-current (290.10) driver installed. I can startx (I'm writing this in Firefox on that machine), and synaptic tells me it's installed and that's the version. The additional drivers/jockey show the recommended one is activated.
(BTW, how can I find out what driver is installed from the command line?)

**OLD:** So now my problems (AFAIK) are that it won't boot directly (I have to invoke X manually), my desktop windows look 'old' (and I'm missing lots of icons - e.g. in settings), and I've got no sound.

Here's a screenshot of one of my windows (also showing no sound hardware I guess):
[IMG]http://dl.dropbox.com/u/3195573/soundWindow.png[/IMG]

Am I missing some kind of desktop manager or something?

I'm trying to find my grub settings, but can't see what file to look in. I'll add it later if I can.

---

### Post by lindsayward on 2012-02-12
OK, so I did a few things and it's nearly there :)
I added vt.handoff=7 back into the grub option (/etc/default/grub) and now it boots all the way through to a login screen. It shouldn't ask me for a login, but I'm sure I can figure that out again.
I ran sudo dpkg-reconfigure lightdm (not sure if that did anything)
and
what seemed to make the biggest difference strangely, was that I chose a theme for the desktop appearance. I hadn't bothered earlier because I thought I had bigger problems. Now the desktop and icons all look good AND I've got sound again! 
[IMG]http://dl.dropbox.com/u/3195573/soundWindow2.png[/IMG]
Now I just need to get lirc, my remote, going again, sort out the auto-login and auto-start MythTV... I think.

---

### Post by MAFoElffen on 2012-02-12
> **lindsayward said:**
> Thank you for your reply. Nice to have an expert on my case!
I think I do have the nvidia-current (290.10) driver installed. I can startx (I'm writing this in Firefox on that machine), and synaptic tells me it's installed and that's the version. The additional drivers/jockey show the recommended one is activated.
(BTW, how can I find out what driver is installed from the command line?)

So now my problems (AFAIK) are that it won't boot directly (I have to invoke X manually), my desktop windows look 'old' (and I'm missing lots of icons - e.g. in settings), and I've got no sound.

In case these help...
Here's my **/etc/X11/xorg.conf**
(just noticed there's a version number)

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 290.10  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Wed Nov 16 20:32:22 PST 2011


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nvidia"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "screen"
    Device         "nvidia"
    Monitor        "Monitor0"
    Option         "NoLogo" "true"
    Option         "DynamicTwinView" "false"
    Option         "NoFlip" "false"
    Option         "FlatPanelProperties" "Scaling = Native"
    Option         "ModeValidation" "NoVesaModes, NoXServerModes"
    Option         "UseDisplayDevice" "DFP-1"
        #Option  "ModeDebug"           "true"
    Option         "HWCursor" "false"
    SubSection     "Display"
        Modes      "1920x1080_60" "1920x1080_60_0" "1920x1080_50" "1920x1080_30" "1920x1080_25" "1920x1080_24" "1920x1080_60i" "1920x1080_50i"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "false"
EndSection

```Here's a screenshot of one of my windows (also showing no sound hardware I guess):

Am I missing some kind of desktop manager or something?

I'm trying to find my grub settings, but can't see what file to look in. I'll add it later if I can.

Thank you!
Although I've helped many using MythTV with their Graphics Issues, I'm not familiar with the Myth TV Desktop. I do know the the past icons and utilities applet have changed with 11.10.  The functionality is still there, but some of them have evolved and changed as many were combined into applets with tabs of what used to be separate applets.

On starting X at startup... I could tell you a lot of things to check and how to hard code it... but the easiest way is to fix what is most likely broke. Yes, the display manager is suspect:
```

sudo dpkg-reconfigure lightdm

```Next for sound... Install the utility "hwinfo"
```

sudo apt-get install hwinfo

```Then post the results of
```

sudo hwinfo --sound

```

---

### Post by lindsayward on 2012-02-12
:) Looks like you replied in between my post and me editing it. 
I don't know what the exact solution was - a combination of things, I guess. As above, sound and desktop/graphics are now going well, thanks.
I found that with 11.10 the messages sent by the remote are slightly different (KEY_Play instead of just Play) and had to edit my lircrc file - not a big deal.

---

