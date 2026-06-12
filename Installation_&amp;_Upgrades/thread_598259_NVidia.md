---
title: "NVidia"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by Roaring Silence on 2007-10-31
Please can someone help me with this frustrating Nvidia problem.
I have spent 3½ days on this and am still no nearer a solution.
I made a fresh install of Ubuntu Linux 7.10
I installed all the updates.
I used the terminal command: 
	sudo apt-get install build-essential
to obtain all the necessary compilers before the Nvidia driver was installed.
My video card is:
	Nvidia GeForce2 Integrated GPU
for which I need the nvidia-glx driver, so I downloaded the package:
	NVIDIA-Linux-x86-96.43.01-pkg1.run
from their website and installed it with the sudo sh command.
It seemed to install perfectly and yet on reboot, nothing but a blank screen!
I uninstalled the nvidia driver and then loaded the Linux restricted packages to try the Restricted Drivers Manager route ....on reboot, nothing but a blank screen!
I tried all the other methods suggested in this forum, but on reboot, nothing but a blank screen!
I then tried the ENVY script. This downloaded a pile of stuff, and did give me a screen in a sensible resolution, 1152x864 instead of the frustrating 800x600, but the display was very unstable and I think was not refreshing properly
Can anyone please tell me how I edit my xorg.conf file, or is there a bug somewhere, making a solution impossible at the moment? Thanks in advance.

Here is my xorg.conf file:
Identifier     "Default Layout" 
    Screen         "Default Screen" 0 0 
    InputDevice    "Generic Keyboard" 
    InputDevice    "Configured Mouse" 
EndSection 

Section "Files" 
EndSection 

Section "Module" 
    Load           "glx" 
EndSection 

Section "InputDevice" 
    Identifier     "Generic Keyboard" 
    Driver         "kbd" 
    Option         "CoreKeyboard" 
    Option         "XkbRules" "xorg" 
    Option         "XkbModel" "pc105" 
    Option         "XkbLayout" "gb" 
EndSection 

Section "InputDevice" 
    Identifier     "Configured Mouse" 
    Driver         "mouse" 
    Option         "CorePointer" 
    Option         "Device" "/dev/input/mice" 
    Option         "Protocol" "ImPS/2" 
    Option         "ZAxisMapping" "4 5" 
    Option         "Emulate3Buttons" "true" 
EndSection 

Section "InputDevice" 
    Identifier     "stylus" 
    Driver         "wacom" 
    Option         "Device" "/dev/input/wacom" 
    Option         "Type" "stylus" 
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY 
EndSection 

Section "InputDevice" 
    Identifier     "eraser" 
    Driver         "wacom" 
    Option         "Device" "/dev/input/wacom" 
    Option         "Type" "eraser" 
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY 
EndSection 

Section "InputDevice" 
    Identifier     "cursor" 
    Driver         "wacom" 
    Option         "Device" "/dev/input/wacom" 
    Option         "Type" "cursor" 
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY 
EndSection 

Section "Monitor" 
    Identifier     "LCD MONITOR" 
    Option         "DPMS" 
EndSection 

Section "Device" 
    Identifier     "nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics]" 
    Driver         "nvidia" 
    Option         "NoLogo" "true" 
EndSection 
 
Section "Screen" 
    Identifier     "Default Screen" 
    Device         "nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics]" 
    Monitor        "LCD MONITOR" 
    DefaultDepth    24 
    Option         "AddARGBGLXVisuals" "True" 
    SubSection     "Display" 
        Depth       24 
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" 
    EndSubSection 
EndSection 

Section "Extensions" 
    Option         "Composite" "Enable" 
EndSection

---

### Post by Roaring Silence on 2007-10-31
I have now done 3 successive installations of Gutsy and each time tried a different one of the three main ways of installing the NVidia driver viz:
   1) Via the restricted packages manager
   2) By installing the driver from the NVidia website
   3) By using the ENVY script
I have also tried all the ways suggested on these forums. Nothing seems to work.
Any ideas, before I regrettably and reluctantly have to give up on Ubuntu altogether?

---

### Post by dabl on 2007-10-31
> **Roaring Silence said:**
> 

I have now done 3 successive installations of Gutsy and each time tried a different one of the three main ways of installing the NVidia driver viz ...

Any ideas, before I regrettably and reluctantly have to give up on Ubuntu altogether?



OK -- STOP reinstalling -- you can't keep doing the same thing over and over and expecting a different result ... that would be... errrr, fatiguing!  :)

That's an old integrated Nvidia chip.  Let's give it one more chance, but in this sequence:

1. With NO proprietary Nvidia driver running, or trying to run, download and install Envy.  If you need to configure a VESA driver so that you're not running a proprietary driver, run ```
sudo dpkg-reconfigure xserver-xorg
``` and choose "NO" on the first question about autodetecting, and choose "VESA" on the second screen, and then accept the defaults until you get to monitor.  You can set the resolution to something comfortable like 1024 x 768 and set the refresh rate to something your LCD or CRT can live with.  When the script dumps you back to the CLI you can start the X server with ```
startx
``` and you should have a GUI in which to proceed.

 You need the file:

"envy_0.9.8-0ubuntu10_all.deb"

from this web site:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

When downloaded, right-click it and "Open With > Gdebi Installer" or something to that effect, to install it.  Open the console and enter ```
sudo envy -t
``` to run the installer in text mode.
If you have the remains of the last failed attempt to install the proprietary driver still on your system, the first thing to do is "Remove the Nvidia Driver".  After that runs, then run Envy again and choose "Install the Nvidia Driver".  When it restarts X you'll know right away whether it worked or not, because you'll either see the Nvidia splash screen, or you won't.

If you do, then open the console and enter ```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
``` to write a new xorg.conf file with glx and compositing enabled.  It will restart the X server.

If you make it that far, then open the console again and enter ```
sudo nvidia-settings
``` to set your default resolution and refresh rates, and don't forget to click the "Save to X Configuration File" button.  If you are concerned about an appearance of instability on the screen, this is the place to adjust things -- slow down the refresh rate a little, or else try a lower resolution.

Good luck! :)

---

### Post by Roaring Silence on 2007-10-31
Thanks for taking the time to reply. I went through all your instructions very carefully 3 times, but, sadly, nothing worked any time. Just froze at a blank screen every time. I really don't know what is wrong.
I am thinking that I might go back to Ubuntu 7.04 and load one of the earlier glx legacy drivers. If I can get Ubuntu 7.04 to work at a sensible resolution, then maybe I can upgrade into Gutsy.
Thanks for trying, anyway.

---

### Post by skits on 2007-10-31
I cannot help. 

&#65279;My Experience with upgrading to Ubuntu 7.1 – not good!

I have been using Ubuntu Dapper for about a year and have used other distributions of Linux for about ten years. So I'm not a total neophyte. And the reviews on Gutsy were very good.

I downloaded the Ubuntu 7.10 i386 desktop iso – took three tries to get one that passed the MD5 check. 

I burned cd's, five, before I decided it might be the brand of cd that was causing the Check Disk Integrity failures. A different brand worked first burn. 

The live cd functioned well – I had 1280x1024 resolution, windows opened and closed, Internet was browsed, games played, Office used – in short it looked good. Time to try the Install function.

I have a Gateway AMD 3800 with 1GB ram and a 200GB hd, nVidia GeForce 6100 onboard video, onboard NIC etc. . I had the drive partitioned into several virtual drives – this saved my valuable files as /home is on one “drive”.

Install went well; have to be careful setting up the partitions/drives to make sure it doesn't reformat the wrong drive and destroy valuable data. Time to re-boot.
Hmm, resolution is 800x600. Strange. Check xorg.conf – all resolutions are there but not displayed on  System>Preference>Screen resolution, only 640x480 and 800x600. Do some browsing on the Internet, lots of hits on Google for Ubuntu 7.1 display issues. That should have been a warning!

Download and install the nVidia proprietary driver and reboot. Windows open, but have no title bars, windows are ghosts and don't update, windows cannot be moved around, there are no icons on the top tool bar. Went through this whole process several times. I found that I could get the empty windows (e.g. Synaptic Package Manager) to update by either going to a terminal session via Ctrl-Alt-F4 and then back via Ctrl-Alt-F7, or by minimizing the window (when it had “decorations”) and then restoring it. Either is a tedious way to scroll through choices.

More browsing on the internet. Found several hints. Tried adding Options to Xorg.conf in the Screen section to “AddARGBLXvisuals” “True” and “DisableGLXRootClipping””True”. No better.

Tried setting indirect=yes in /usr/bin/compiz. Nope

Tried apt-get install advanced-desktop-effects-settings and turning on various combinations of the effects. Nope. Still variations on the non-updating, ghosting etc of the applications windows.

Tried removing/disabling the nVidia driver. Nope.

Could not find how to remove compiz. Lots of posts about the wonders of its eye-candy.

Any time I had Compiz AND the nVidia driver enabled, I had the weird problems. Without the nVidia driver I had low resolutions. but most things worked.

I tried the Alternate install – no better.

After two days of frustration, I downloaded Dapper, 6.06.1. I re-installed it and, apart from having to re-install all the optional programs like gcj, gcc, g77, f95, Eclipse etc etc etc, all is well now.

So, my advice if you have an nVidia card (or, if you have an ATI card, according to some of the 'issues' I googled) DO NOT UPGRADE to 7.10, unless you are prepared for a lot of work. 

Of course, your mileage may vary. 
And, BACK UP your important files first!

---

### Post by Roaring Silence on 2007-11-01
Interesting comments. If I had a full time job, or if in any way time was money for me, there is no way I could touch Ubuntu. I have spent 4 days on this problem. Luckily I am retired.
The "vesa" generic driver did not work at all. I have now got a decent resolution using the "nv" generic driver - 1280 x 1024, but I still cannot get the proprietary nvidia driver to work. That means I cannot turn on desktop effects, but that is no big deal for me. The screen set-up is now stable, and I can work on this computer at last. The config file xorg.conf needed lines in the "Monitor" section giving the HorizSync and VertRefresh parameters. So the section now reads:

Section "Monitor"
        Identifier      "LCD MONITOR"
        Option          "DPMS"
        HorizSync       30-68
        VertRefresh     50-85
EndSection

For some reason when I was letting nvidia-config automatically configure this file, it was leaving these important lines out.
I don't know much about the politics of this, but it seems from what I have read on the internet that there is something of a stand-off between Mark Shuttleworth and Canonical on the one hand and the proprietary drivers people like NVidia on the other. I just hope they can soon get their act together for their mutual benefit. From my experience, more limited than yours, Linux in general, and Ubuntu in particular is a much better operating system than Windows XP, and much more fun to use, when things are working as they should.

---

