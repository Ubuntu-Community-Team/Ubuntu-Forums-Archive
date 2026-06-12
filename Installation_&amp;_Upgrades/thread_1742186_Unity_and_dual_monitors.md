---
title: "Unity and dual monitors"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by fvillars on 2011-04-28
Does Unity/Ubuntu 11.04 allow for the use of dual monitors? I see a number of posts nibbling at the edges of this issue, but I see no clear cut answer.
My own brief experience with this new upgrade (< 24 hours) suggests to me the answer is no. Anyone with a different answer let me know.

---

### Post by Blasphemist on 2011-04-28
It does work, dual monitors and natty. I am using it. See screenshot.

---

### Post by ewanchic on 2011-04-29
:KS Thanks for the screenshot. My co-worker is using a Mac, and is having an issue with one-menu and multiple screens. Your screenshot answered the question: does the menu show up on both screens, and it looks like it does...as it should. Thanks!


> **Blasphemist said:**
> It does work, dual monitors and natty. I am using it. See screenshot.

---

### Post by mr.n.nand on 2011-04-30
Hi,

I was able to setup the dual monitor mode. The problem for me is that, Unity is not switching to single monitor mode when the other monitor is disconnected.
Any ideas?

Thanks

---

### Post by fvillars on 2011-04-30
Thanks for the replies. Clearly dual monitors will work under some configurations, but there is one which will no longer work that used to  work under 10.10. 

If you have 

a)two single-headed NVIDIA cards 

b) each with a single monitor attached and 

c) configured as a single desktop using Xinerama,

This would work under Ubuntu 10.10 and previous versions, but will no longer work under 11.04/Unity.

The reason for this is:

1)Xinerama and Unity are incompatible with one another. If you try to
  use them together X will either crash or freeze.

2)The previous NVIDIA workaround, "Twinview", will only work with a    single double-headed card, not with two separate cards.

The only solution for those with my particular setup: 2 monitors, 2 NVIDIA cards is:

1)ditch the 2nd card and monitor and go with a single monitor or

2)ditch both cards, buy a new double-headed card and use Twinview to configure or

3)use card/cards by different manufacturer or 

4)stick with Ubuntu "Classic", which is what I will do since it works perfectly well and since I am not yet sold on all the bells and whistles of 11.04

---

### Post by lyndros on 2011-05-01
Anyhow if they want to have a real and usable desktop operating system in my opinion Unity is a step back. 

I am having exactly the same problems with two ATI graphic cards with a single monitor attached to each one.

---

### Post by Ken UK on 2011-05-01
> **lyndros said:**
> 
I am having exactly the same problems with two ATI graphic cards with a single monitor attached to each one.

I would never do that, I am in the same position but I put both monitors in one card. I have never got dual monitors with separate cards to work in Linux, one always show a terminal type display.

Dual monitors works for me without any problems.

---

### Post by RavensKrag on 2011-05-01
The kernel that ships with Ubuntu 11.04 seems to have some regressions with this sort of thing.  I'm using 2.6.38-02063804-generic and seems like that is working much better with my hardware.

Here's the terminal commands to DL and install the older kernel.
```
cd && wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804_2.6.38-02063804.201104221009_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-image-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb

sudo dpkg -i linux-image-2.6.38-02063804*
```

You will then need to reboot, of course.

---

### Post by orion2001 on 2011-05-01
Any of you folks with ATI hardware managing to pull off a dual monitor set-up without screen corruption issues?

Just installed 11.04 to take my first attempt at moving towards linux and everything works quite nicely, except my dual-display setup which unfortunately has me going back to Windows 7. 

Anytime I try a dual monitor setup (HDTV and LCD Monitor) I invariably get some screen corruption issues. Happens with both Unity and Classic (although less frequently with the latter). I tried both the original Radeon drivers as well as the proprietary drivers pushed by Ubuntu after the install, but with no luck. 

Seems like other folks are also having screen corruption issues. Is this something that would eventually be fixed via an update or will I have to get my hands dirty and/or wait for the next version of ubuntu?

---

### Post by Blasphemist on 2011-05-01
> **orion2001 said:**
> Any of you folks with ATI hardware managing to pull off a dual monitor set-up without screen corruption issues?

Just installed 11.04 to take my first attempt at moving towards linux and everything works quite nicely, except my dual-display setup which unfortunately has me going back to Windows 7. 

Anytime I try a dual monitor setup (HDTV and LCD Monitor) I invariably get some screen corruption issues. Happens with both Unity and Classic (although less frequently with the latter). I tried both the original Radeon drivers as well as the proprietary drivers pushed by Ubuntu after the install, but with no luck. 

Seems like other folks are also having screen corruption issues. Is this something that would eventually be fixed via an update or will I have to get my hands dirty and/or wait for the next version of ubuntu?

Here's something I ran into.

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

Seems my simple Intel graphics are workable.

---

### Post by orion2001 on 2011-05-01
> **Blasphemist said:**
> Here's something I ran into.

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

Seems my simple Intel graphics are workable.
Thanks a lot Jim. I have a Radeon HD 5770, so it should definitely be good enough for Unity and to run a dual monitor setup (1280x720 and 1920x1200). I did try the fglrx drivers, but they didn't really help too much. Ubuntu seemed very finicky about screen resolution settings in general and would occasionally default back weirdly causing strange artifacts.

Also, any time I exit out of XBMC (running in fullscreen mode) on the second monitor, it would force me back into Cloned desktop mode and lower the resolution on my higher res screen.

---

### Post by gewin on 2011-05-01
I have been struggling with external monitors on a laptop for a week now. The external HD TV on a HDMI port on an Acer laptop . I have had only minimal success (only with the intel graphics not the nvidia). Mirror displays doesn't work but when you haven't selected this I have control of the displays. xrandr commands allow me to select different primary outputs for Unity but I have to say this isn't stable.

This is disappointing as some many notebook people want dual monitor support.

---

### Post by gyaneshwar on 2011-05-01
I have ATI X1650 and till 11.04 I had no problems with following configuration:

Left monitor DVI-0=1440x900 90degrees
Right monitor DVI-1=1920x1280 normal rotation.

Now, on Natty it works only in safe mode.

If I put rotation to normal everything is fine but how to make it work on 90. I tried Unity, Gnome Classic and KDE - everywhere is the same problem so it means that the hardware support is gone!

Any idea?

Thanks

---

### Post by Blasphemist on 2011-05-01
> **gyaneshwar said:**
> I have ATI X1650 and till 11.04 I had no problems with following configuration:

Left monitor DVI-0=1440x900 90degrees
Right monitor DVI-1=1920x1280 normal rotation.

Now, on Natty it works only in safe mode.

If I put rotation to normal everything is fine but how to make it work on 90. I tried Unity, Gnome Classic and KDE - everywhere is the same problem so it means that the hardware support is gone!

Any idea?

Thanks

Run this and it may tell you if there is something to address.
```
/usr/lib/nux/unity_support_test -p
```

It comes from this.

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

---

### Post by gyaneshwar on 2011-05-01
> **Blasphemist said:**
> Run this and it may tell you if there is something to address.
```
/usr/lib/nux/unity_support_test -p
```

It comes from this.

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

I did that and got no errors:

/usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV530
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

Any other?

---

### Post by Blasphemist on 2011-05-01
I don't know if this is just what you are experiencing, in fact I think this is worse than what you have. You may want to take a look.

[https://bugs.launchpad.net/ubuntu/natty/+source/xserver-xorg-video-ati/+bug/628727](https://bugs.launchpad.net/ubuntu/natty/+source/xserver-xorg-video-ati/+bug/628727)

Other than that, I don't have anything else right now.

---

### Post by gyaneshwar on 2011-05-02
> **Blasphemist said:**
> I don't know if this is just what you are experiencing, in fact I think this is worse than what you have. You may want to take a look.

[https://bugs.launchpad.net/ubuntu/natty/+source/xserver-xorg-video-ati/+bug/628727](https://bugs.launchpad.net/ubuntu/natty/+source/xserver-xorg-video-ati/+bug/628727)

Other than that, I don't have anything else right now.

Thanks anyhow :)!

sgy

---

### Post by amartinezi on 2011-05-02
> **Blasphemist said:**
> Here's something I ran into.

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

Seems my simple Intel graphics are workable.


This is just the ubuntu spec to run unity..there is only some advises and a script to run to check if your system is unity capable. Doesn't help to active dual monitor, at least to me.

---

### Post by Blasphemist on 2011-05-02
gyaneshwar, looking back at this in the light of day I want to be sure I understand. Your only issue is rotation for one monitor right? The displays application should allow you to change that, as should xrandr. This is from the xrandr man page.

--rotate rotation
              Rotation  can be one of 'normal', 'left', 'right' or 'inverted'.
              This causes the output contents to be rotated in  the  specified
              direction. 'right' specifies a clockwise rotation of the picture
              and 'left' specifies a counter-clockwise rotation.

So since you did this in previous versions, is it now not working with the same thing done? 

amartinezi, are you having an issue activating a second monitor? I just can't tell for sure what your issue is.

Lastly, here is a link on implementing a second monitor dynamically to ensure it works with both one and two depending on what is connected. Implementing this is one of my tasks today.

[https://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor](https://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor)

---

### Post by cyberbsd on 2011-05-04
I can set one monitor portrait and one landscape with NVIDIA single card two head under classic mode(Separate X).

but...
windows in the portrait can't get mouse focus correctly.
Ex. I can't move window in extend monitor, only master monitor working correctly.

sign...

---

### Post by Rodemire on 2011-05-04
> **Blasphemist said:**
> It does work, dual monitors and natty. I am using it. See screenshot.

Can i ask, how did u get it to work with the Nvidia card? I cant seem to get my launcher on both screens.

---

### Post by Blasphemist on 2011-05-04
> **Rodemire said:**
> Can i ask, how did u get it to work with the Nvidia card? I cant seem to get my launcher on both screens.

I don't have nvidia, I have intel. The launcher is only on one screen. I don't think it can be on both unless you use both monitors as the same image. If you have your desktop span the two monitors, you can't have the launcher on both.

---

### Post by israel.figueroa on 2011-05-04
11.04 100% fresh install on w/Intel Card. 10.10 double monitor worked great. Now every time I hook The monitor and enable it on the Monitor Settings, the diplay extend but the windows doesn't show, only te mouse.

So I open a terminal and run as user:

```

compiz --replace
```

Aparently compiz doesn't get a notification of the resolution update, so keeps drawing windows just within the known margins. 

Afther the comand, a full desktop redraw and the windows can pass from a display to another correctly. It keep being buggy, but now it seems to me that it's a compiz related bug.

Now, I hope that this help someonelse.

Regards
Israel

---

### Post by RavensKrag on 2011-05-07
> **israel.figueroa said:**
> 
So I open a terminal and run as user:

```

compiz --replace
```

Aparently compiz doesn't get a notification of the resolution update, so keeps drawing windows just within the known margins. 


You, good sir/madam are a hero.

One thing I would like to note however, is that this command should be run using Alt + F2 and not in a terminal.  Well, unless you have no intent to close that terminal for the remainder of your session.

Now if only I could figure out how get a script to execute when a monitor gets plugged in, I could automate this whole process for a quick workaround...

---

### Post by brel on 2011-05-08
Similar issues. I've intel graphics and before I did a 'compiz --replace' the screens were really flaky (nothing on the attached screen; on my laptop, there was a big black bar in the top half).

'compiz --replace' does clean things up, but now I've got disappearing application windows. They get lost in the space between my monitors it seems.

I hope someone's working on this. I first tried dual monitors on a 10.10 install a few days ago and it worked flawlessly. I'm regretting somewhat my upgrade to 11.04 (although I like unity so far).

---

### Post by thegreygandalf on 2011-05-15
Nec 2080UX+ (1600x1200 50 cm screen rotated 90° CCW to be 1200x1600) to the left of Nec PA301W (2560 x1600 70cm screen)

This worked fine under Ubuntu 10.10 with Xinerama

Under Ubuntu 11.04 it does NOT work (neither in Unity nor in Ubuntu classic mode) : the left screen remains black (except for mouse pointer, when in that area) and the right screen has the contents of the left screen plus its own shifted 1200 pixels to the right. When in the right screen the mouse pointer clicks operate 1200 to the right of where the pointer is displayed (try clicking anything that way !). The right hand side of the right screen is outside the visible area.

In the present state this is unusable. 

Is there any hope of the Ubuntu people fixing this mess ?

---

### Post by Blasphemist on 2011-05-15
> **thegreygandalf said:**
> Nec 2080UX+ (1600x1200 50 cm screen rotated 90° CCW to be 1200x1600) to the left of Nec PA301W (2560 x1600 70cm screen)

This worked fine under Ubuntu 10.10 with Xinerama

Under Ubuntu 11.04 it does NOT work (neither in Unity nor in Ubuntu classic mode) : the left screen remains black (except for mouse pointer, when in that area) and the right screen has the contents of the left screen plus its own shifted 1200 pixels to the right. When in the right screen the mouse pointer clicks operate 1200 to the right of where the pointer is displayed (try clicking anything that way !). The right hand side of the right screen is outside the visible area.

In the present state this is unusable. 

Is there any hope of the Ubuntu people fixing this mess ?
Your post seems to say that you're not asking for help in this forum but rather asking if the ubuntu developers will fix this. I can't speak to whether the developers will fix this, nor can anyone else from the information you've provided, unless you provide more detail. The basics of your whole platform, the details of your video subsystem, the detail of what you have tried and the results or lack there of from your efforts are needed if you'd like any of us to help. 

Would you like for us to help?

---

### Post by aago1254 on 2011-05-15
this didnt work all it did is installed another version of linux and now it doesnt work and now i have to go to a older version of linux to even get back into my desktop lame thanks for messing up the boot loader when i have more time ill have to remove it

> **RavensKrag said:**
> The kernel that ships with Ubuntu 11.04 seems to have some regressions with this sort of thing.  I'm using 2.6.38-02063804-generic and seems like that is working much better with my hardware.

Here's the terminal commands to DL and install the older kernel.
```
cd && wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804_2.6.38-02063804.201104221009_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-image-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb

sudo dpkg -i linux-image-2.6.38-02063804*
```You will then need to reboot, of course.

---

### Post by thegreygandalf on 2011-05-22
@Blasphemist
Thanks for your reply and offer of help and yes, if you can, I would like some help.

Here is my system: a Gigabyte 870A-UD3 (AM3) mainboard with a Phenom  ii x6 1100t and 8 GB ram (2 x Kingston 4GB ram )with a GainwardGeForce GTX 570 1280MB GDDR5 **NVIDIA** graphics card. The monitors are both connected via dvi cables. If you other info, please let me know (including, if possible how/where to obtain/find it)

**In Ubuntu 11.04 (classic):**
*System->Preferences->Monitors* only finds the NEC PA301w (2560x1600) screen.
  *System->Preferences->Monitors *also states "Rotation not supported" in the drop down menu from its icon when placed in the bar at the top of the screen - This prompted me to ask whether the Ubuntu developers have to do something ?

*System->Administration->Multiple Screens* also only finds the NEC PA301w (2560x1600) screen in a window called grandr

*System->Administration->Nvidia X Server Settings* finds both the NEC PA301w (2560x1600) and the NEC LCD2080UX+ (1600x1200) but has apparently no options to rotate the latter to 1200x1600.
[I]
System->Administration->Additional Drivers[/I] opens a window which states that "No proprietary drivers are in use on this system" but places a green circle in from of "NVIDIA accelerated graphics driver (version current) recommended" and "This driver is activated but not currently in use". There is only a "remove" button and apparently no way of "using" it from that window
[B]
The xorg.conf which only uses the NEC PA301w (2560x1600) and leaves the other screen black under ubuntu 11.04 (classic) is :[/B]
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

Section "InputClass"
        Identifier "Mouse Remap"
        MatchProduct "Saitek Cyborg R.A.T.7 Mouse"
        MatchDevicePath "/dev/input/event*"
        Option "ButtonMapping" "1 2 3 4 5 6 7 2 9 10 11 12 0 0 0"
EndSection

**The xorg.conf which worked in Ubuntu 10.10 but does not work with ubuntu 11.04 is :**
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@yellow)  Mon Oct  4 15:59:51 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1600 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEC PA301W"
    HorizSync       31.0 - 99.0
    VertRefresh     30.0 - 87.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "NEC LCD2080UX+"
    HorizSync       30.0 - 96.0
    VertRefresh     48.0 - 87.0
    Option         "DPMS"
    Option         "Rotate" "CCW"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "D13U"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "D13U"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-4: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-3: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "InputClass"
        Identifier "Mouse Remap"
        MatchProduct "Saitek Cyborg R.A.T.7 Mouse"
        MatchDevicePath "/dev/input/event*"
        Option "ButtonMapping" "1 2 3 4 5 6 7 2 9 10 11 12 0 0 0"
EndSection

---

### Post by ravindra_jain12 on 2011-05-29
> **israel.figueroa said:**
> 11.04 100% fresh install on w/Intel Card. 10.10 double monitor worked great. Now every time I hook The monitor and enable it on the Monitor Settings, the diplay extend but the windows doesn't show, only te mouse.

So I open a terminal and run as user:

```

compiz --replace
```

Aparently compiz doesn't get a notification of the resolution update, so keeps drawing windows just within the known margins. 



Thanks a lot for sharing this. I've upgraded my laptop from 10.10 to 11.04 and found dual monitor support not working properly. Tried running "*compiz --replace*", but it didn't work. Then I tried the following on Alt-F2 dash prompt: ```
*unity --replace*
```

This redraws everything just perfectly. My dual monitor setup is working absolutely fine, and I like the way they handled global menubar problem by adding it on both the screens.

---

