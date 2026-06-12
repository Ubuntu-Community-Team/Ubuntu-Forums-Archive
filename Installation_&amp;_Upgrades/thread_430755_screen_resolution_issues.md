---
title: "screen resolution issues"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by kameleon25 on 2007-05-02
I have a Matrox G400/G450 installed in my Ubuntu machine running 7.04. When I installed it I could only get a max resolution of 1024x768 in the screen settings in Gnome. I tried editing the xorg.conf file manually by only leaving the 1280x1024 (the resolution I want) setting as an option. Now it only displays 1280x800. The monitor I have is a Mitsubishi Diamond Scan 70. It should be able to do 1280x1024@65hz according to the documentation. It has been a while since I have messed with linux but I am killing my winblowz addiction slowly. Could anyone guide me in the right direction?

Thanks,

Kameleon

P.S. When I tried 6.04 Ubuntu and Kubuntu before on a different machine it was kinda weird. The Ubuntu (Gnome) would run at a max of 1024x768 where the Kubuntu (KDE) would run 1280x1024 no problem. Both were the live cd though. I did not install anything on that pc as it is my wifes. Any insight on that also?

---

### Post by dannyboy79 on 2007-05-02
type in

sudo dpkg-reconfigure xserver-xorg

and chose the defaults for anything you don't know and hten when the resolutions come up make sure you chose the applicable one. good lcuk

---

### Post by kameleon25 on 2007-05-02
First off, I must say DANG that was fast. :) I am used to having to post a question on other forums and wait a week for a reply. ;) Anyways, I did do the sudo dpkg-reconfigure -phigh xserver-xorg last night and it never would do the 1280x1024. So leaving off the -phigh part will help? I am at work at the moment and will try as soon as I get home. Thanks!

---

### Post by dannyboy79 on 2007-05-02
> **kameleon25 said:**
> First off, I must say DANG that was fast. :) I am used to having to post a question on other forums and wait a week for a reply. ;) Anyways, I did do the sudo dpkg-reconfigure -phigh xserver-xorg last night and it never would do the 1280x1024. So leaving off the -phigh part will help? I am at work at the moment and will try as soon as I get home. Thanks!

as long as your sure that your graphics card and monitor support that resolution than it should work. it's possible that the incorrect hor and vert frequencies are being chosen which then will not allow you to chose the resolution that you want. do you know what the range of the horizontal and vertical frequencies that you montor runs at? it's either in the internet or in the manual.

---

### Post by kameleon25 on 2007-05-02
This is the info I have found:

Display

Diagonal Size: 17"

Viewable Size: 16"

Dot Pitch / Pixel Pitch: 0.28 mm

Max Resolution: 1280 x 1024 / 65 Hz

Max Sync Rate (V x H): 100 Hz x 70 kHz

Video Bandwidth: 100 MHz

Factory Preset Resolution Modes:

    * 1280 x 1024 / 65 Hz
    * 1024 x 768 / 85 Hz

When I look in the xorg.conf file I don't see anything specified for the sync rate.

---

### Post by Syke on 2007-05-02
This walkthrough is a little old, but I think it might help your tweaking.

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by kameleon25 on 2007-05-02
Ok, I did all of the above and still can only get 1280x800. I also found the sync rates and input them manually and still no go. Any other thoughts?

---

### Post by undecidable on 2007-05-03
One other thing worth doing is to check the xorg log and see if there are any funny messages during X startup.
(menu/Admin/system log/xorg0.log)

---

### Post by kameleon25 on 2007-05-06
Still no go. The xorg0.log says it isn't using that resolution because the hsync is out of range or something similar. I even put in the modeline that I generated via one of those webpages for such a issue.  

I am almost just about to ditch this install and move it to my main machine. This is a p3 1ghz w/ 384mb ram and a matrox g400/450. My main machine that winblows is on is a p4 2.53ghz running at 2.8ghz w 1gb ram and a geforce 5200. The only thing keeping me from formating my main winblowz machine is the... .uh.... video backup part. ;) Like using "ripit4me". Beyond that I have found suitable replacements for all my stuff in linux. 

Any other ideas?

---

### Post by dannyboy79 on 2007-05-07
i think there is a program that can "get" the frequency ranges from the screen. i forget what it's called. if the error log is stating that you have a bad range than that's the issue. try to gogle for the little app.

---

### Post by hal8000 on 2007-05-07
What resolution do you get when working in windows? Most monitors can display on screen graphics of horizonatal and vertical refresh rates, so post these together with your resolution.

Also post your /etc/X11/xorg.conf file.  Personally, I'd drop a resolution to work at a higher refresh rate, 1280x1024 @ 65Hz is not a standard resolution but working at 75 or 85Hz is a standard resolution. You may see screen flicker at 65Hz.

---

### Post by kameleon25 on 2007-05-07
I will do that. It is just weird that on 6.10 I could boot off the live cd with kubuntu and it would do 1280x1024. But regular ubuntu wouldn't no matter how I did it. Kinda makes me think it is something with gnome. We shall see.

---

### Post by kameleon25 on 2007-05-07
As requested here is my xorg.conf file:

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
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
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "Matrox Graphics, Inc. MGA G400/G450"
        Driver          "mga"
        BusID           "PCI:1:0:0"
        Option          "OldDmaInit"            "True"
EndSection

Section "Monitor"
        Identifier      "SD7714C"
        HorizSync       47-63
        VertRefresh     50-110
        Option          "DPMS"
        # V-freq: 100.00 Hz  // h-freq: 108.94 KHz
        Modeline "1280x1024" 247.50  1280 1408 1712 2272  1024 1024 1028 1089
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Matrox Graphics, Inc. MGA G400/G450"
        Monitor         "SD7714C"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection



In windows I am running 1280x1024 at 60hz. Now that is on my main pc which is on the same monitor via a KVM switch.

---

### Post by dannyboy79 on 2007-05-07
huh? this is all I have in my monitor section.


Section "Monitor"
    Identifier     "SENERGY 714"
    Option         "DPMS"
EndSection


it's a Princeton Synergy 17" Flat Panel monitor w/ DVI and Analog input. Does you monitor have both inputs as well?? If it does this is how I am able to run both my windows computer and my ubuntu box on the same Monitor. My kvm switch doesn't have DVI and so I could take full advantage of my ATI AIW 9800 Pro that I have in my windows box, I hooked the DVI port on that to the monitor's DVI input and then I just used the D-Sub analog connector for my Ubuntu box. I hit Scroll Lock 2 times to get it to switch the keyboard and mouse to the other computer and merely hit the "Input" button on the front of the monitor to get to the other computer's display. 

I am guessing that it has something to do with the KVM switch. Is it top of the line or just a $50 dollar one? 

Just cause I am curious maybe you could try what I am suggesting and after you switch it so that both computers are directly connected to your monitor, then re-run 

sudo dpkg-reconfigure xserver-xorg 

and see if it's works. if it does, then try  to switch back to the KVM. Hope this works for ya.

---

### Post by kameleon25 on 2007-05-07
It is a linksys 2-port one. Not cheap but not top of the line either. I don't think it has anything to do with the KVM switch as the previous version of kubunu was able to display via live cd the 1280x1024. But then again that was a different pc. Same kvm switch and monitor. Just different pc. I am almost at my wits end.

---

### Post by dannyboy79 on 2007-05-08
it's not like it would take you more than 5 mins to try. I can't suggest anything more. good luck and definitely let us know if you solve it.

---

### Post by kameleon25 on 2007-05-08
Oh, don't get me wrong... I do appreciate the help and suggestions. I do plan to try it. It will just be tomorrow at the earliest before I can. I certainly hope that isn't the case with the KVM switch being the issue. But it is possible. I have done some research and found that 95% of my programs I "had to have windows for" run with WINE. So the sooner I can get the resolution issue fixed the sooner I can ditch macroshaft. So I will be trying the kvm-less hookup soon. I will keep ya'll posted.

P.S. I have searched google for that little program but cannot find it. Any other ideas like what part of the name is? 

Thanks so very much!

---

### Post by dannyboy79 on 2007-05-08
it's read-edid. that's actually what the dpkg-reconfigure xserver-xorg is already using but sometimes the xserver doesn't read from the edid.bin located within /etc/X11/. Check this link out, a similar problem for another user and trying to get proper refresh rate for his widescreen.

[https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/94994](https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/94994)


Apparently, all he had to do was make sure his xorg.conf was not there, i mean either rename it or move it don't delete it. Then do control alt backspace and this should restart the xserver and if it can't find the xorg.conf it might work just like in the link I linked to.

 also, just to be clear, I am not saying skip the kvm completely, I am only saying skip it for the video is all. that way you don't haev to have 2 keyboards and 2 mice. good luck

---

