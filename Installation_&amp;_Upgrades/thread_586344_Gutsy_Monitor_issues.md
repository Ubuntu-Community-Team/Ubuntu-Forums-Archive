---
title: "Gutsy Monitor issues"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by apocalypse2012 on 2007-10-22
I just upgraded to Gutsy and cant get my system to address my monitors native resolution. I have a SGI 1600sw and an Nvidia Quadro FX 2000.

The 'Screen and Graphics' applet does not seem to work at all. The dialog does not refresh when you change monitor types, and it shows no resolution options for many monitors. 

Any one using the SGI 1600sw on Ubuntu these days?

---

### Post by drbongo on 2007-10-22
I am also having monitor/resolution problems with all flavours of Gutsy: Ubuntu, Kubuntu, Edbuntu and Xubuntu. The problem is that after the live CD boots the screen goes blank and nothing else happens. I can get them to work with a safe graphics start, but once booted the resolution is set to 1280x1024 and if I change it the screen just gets messed up. This is true from the live CD and a full install even from the Alternate CD! I will try an update and see if that works. I have also tried setting the resolution at boot time and editing Xorg.conf and usplash.conf but this has not helped!

Has anyone else got this problem and is there a fix?

I am using ATI 9250 and ATI7000 graphics cards and 19"Hansol monitors. The live CD booted fine on computers with a large LCD screen, but not on older VDU's.

drbongo :confused:

---

### Post by grazioso on 2007-12-17
my gfx-1600sw adaptor + sgi v3(nvidia gforce) suddenly stopped working properly    
together with xorg after recent upgrade  xubuntu  to gutsy.

the combo wouldn't accept typical modline fix any more and rejects all   
modes. in some cases it goes to safe mode and in others it just blanks the
screen..

i tried both nv open source and nvidia closed source drivers and
than to my shock it works out of box with no xorg.conf and nv driver at 1600x1024@?
( it is probably the autoselect "feature")- but than it flickers badly and looks washed out.

 any fix for this? 

please don't tell me to get a new gfx card ( if i wanted new card i wouldn't post here)

---

### Post by munden on 2007-12-17
I have the same problem using a Via graphics chip on an MSI K9AGM motherboard with Athlon 64 X2.  When the splash screen comes up it puts my monitor in power save mode.  I am using the same xorg.conf file that worked fine in 7.04.  Looking for ideas here.

---

### Post by grazioso on 2007-12-18
ok it took me good 4 hours and i have a picture, it is not that old clear nice picture pre_ gutsy but it is something  and so far it works with both nv and nvidia drivers. 

it looks like the core of the problem is : EDID and which gfx output is being used. EDID of gfx-1600sw is simply not playing well with card and vice versa. that is why the EDID is disabled and the silly card has to be told where the monitor is connected. so here is part of the xorg.conf that made it work for me in xubuntu gutsy: 

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "vesa"
        Busid           "PCI:1:0:0"
        Driver          "nv" 
#Driver "nvidia"
        Option  "UseEDID" "FALSE" #apparently EDID of GFX-1600sw is bad
        Option "ConnectedMonitor" "DFP" #apparently nvidia card can't tell what's connected &where
EndSection

Section "Monitor"

       Identifier       "SGI 1600SW"
        VendorName      "SGI"
        ModelName       "1600SW"
        Modeline        "1600x1024"     108.0 1600 1616 1656 1704 1024 1027 1030  1056 -Hsync -Vsync
      Modeline "1600x1024" 103.125 1600 1600 1656 1664 1024 1024 1029 1030 HSkew 7 +Hsync +Vsync
   Modeline "1600x1024" 103.125 1600 1600 1656 1664 1024 1024 1029 1030 HSkew 5 +Hsync +Vsync
   Modeline "1600x1024" 103.125 1600 1600 1656 1664 1024 1024 1029 1030 HSkew 1 +Hsync +Vsync
   
HorizSync       31.5-110
VertRefresh     48-160

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "SGI 1600SW"
        DefaultDepth    24

        SubSection "Display"
                Depth           24
                Modes           "1600x1024" 
         EndSubsection

      Subsection "Display"
      Depth 16
      Modes "1600x1024"
      EndSubsection
EndSection


can please someone take it from here and fix that ugly flickering problem with 1600sw+gfx-1600sw+older nvidia cards? 

thanks

---

### Post by grazioso on 2007-12-18
never mind - and the flicker is gone when you i played with switches on gfx-1600sw adaptor

---

