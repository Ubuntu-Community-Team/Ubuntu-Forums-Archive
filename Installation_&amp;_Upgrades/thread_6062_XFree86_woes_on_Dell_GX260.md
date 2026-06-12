---
title: "XFree86 woes on Dell GX260"
date: 2004-11-24
forum: Installation &amp; Upgrades
---

### Post by Defiler on 2004-11-24
I'm having major difficulty getting a fresh install of Ubuntu to work on these Dell GX260 systems. They feature Intel i845-based onboard video, which is set to "8MB video memory" mode in the system BIOS.
When I followed the guided setup (Warty, version 4.10), I answered "Yes" when prompted to fetch package updates from the net.  That process completed successfully, but I was never asked to configure X.
After gdm failed to start at boot, I ran:
***sudo dpkg-reconfigure xserver-xfree86***
..but that failed to help.  Eventually, I tried changing to the 686 + restricted kernel package, just in case the i810 driver wasn't provisioned properly in the vanilla package. No joy.

Here's the gist of the error:
Skipping "/usr/X11R6/lib/modules/fonts/libspeedo.a:spencode.o":  No symbols found
(EE) I810(0): No Video BIOS modes for chosen depth.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

I've included copies of dmesg, base-config.log, etc, etc at the following URL. If you need any other information, just let me know.

[http://supremetyrant.com/ubuntu/](http://supremetyrant.com/ubuntu/)

Thanks for any help you can provide. I've scoured this forum for similar issues, but  haven't found any relevant suggested fixes.

---

### Post by Magneto on 2004-11-24
[QUOTE=Defiler]I'm having major difficulty getting a fresh install of Ubuntu to work on these Dell GX260 systems. They feature Intel i845-based onboard video, which is set to "8MB video memory" mode in the system BIOS.
When I followed the guided setup (Warty, version 4.10), I answered "Yes" when prompted to fetch package updates from the net.  That process completed successfully, but I was never asked to configure X.
After gdm failed to start at boot, I ran:
***sudo dpkg-reconfigure xserver-xfree86***
..but that failed to help.  Eventually, I tried changing to the 686 + restricted kernel package, just in case the i810 driver wasn't provisioned properly in the vanilla package. No joy.

Here's the gist of the error:
Skipping "/usr/X11R6/lib/modules/fonts/libspeedo.a:spencode.o":  No symbols found
(EE) I810(0): No Video BIOS modes for chosen depth.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

I've included copies of dmesg, base-config.log, etc, etc at the following URL. If you need any other information, just let me know.

[http://supremetyrant.com/ubuntu/](http://supremetyrant.com/ubuntu/)

Thanks for any help you can provide. I've scoured this forum for similar issues, but  haven't found any relevant suggested fixes.[/QUOTE]
 Use the generic vesa driver instead of the intel i810  /etc/X11/XF86Config-4

---

### Post by Defiler on 2004-11-24
Thanks. I chose "vesa" in dpkg-reconfigure xserver-xfree86, told it to save, and then looked at the config file. Oddly, it still showed i810.
I manually edited XF86Config-4, and changed the Device line to "vesa".
startx still gives me the same error, except that it now says:
(EE) VESA(0): No Video BIOS modes for chosen depth.

---

### Post by Magneto on 2004-11-24
[QUOTE=Defiler]Thanks. I chose "vesa" in dpkg-reconfigure xserver-xfree86, told it to save, and then looked at the config file. Oddly, it still showed i810.
I manually edited XF86Config-4, and changed the Device line to "vesa".
startx still gives me the same error, except that it now says:
(EE) VESA(0): No Video BIOS modes for chosen depth.[/QUOTE]

what resolution are trying? 

post your xf86config-4  you can attach it to the post

---

### Post by Defiler on 2004-11-24
Trying 1152x864x24:
[http://supremetyrant.com/ubuntu/XF86Config-4](http://supremetyrant.com/ubuntu/XF86Config-4)

---

### Post by Defiler on 2004-11-24
I just tried 800x600, and that failed as well.

---

### Post by Magneto on 2004-11-24
[QUOTE=Defiler]Trying 1152x864x24:
[http://supremetyrant.com/ubuntu/XF86Config-4](http://supremetyrant.com/ubuntu/XF86Config-4)[/QUOTE]
 use 1024x768 at 16 - that should work then try 24

Section "Screen"
    Identifier  "Screen 1"
    Device      "GX260 Onboard"
    Monitor     "Dell D1025TM"
    DefaultDepth 16

    Subsection "Display"
        Depth       8
        Modes       "1152x864" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1152x864" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection



Basically lower the colors and resolution until it works- it will probably do 1600x1200 but not with that driver 
so if 1024x768 at 16 doesnt work try 800x600 16

---

### Post by Defiler on 2004-11-24
Well, making some progress. If I set the config file to default to 800x600x16, and restart the system, it will boot into the GDM login screen.
However, it's running in 640x480 mode, and that is also the only resolution listed in the Desktop Resolution Properties page.
Just for grins, I tried switching it back to the i810 driver, and it behaves the same way as with VESA.

---

### Post by Magneto on 2004-11-24
yup - i have an old g200 matrox card with a similar situation- if you really want it to work at a higher resolution change the version of xfree86 to an older version or swap the drivers-  the older drivers will show more-  xorg will definitely do less
I had to do the same in FedoraCore2 - support for older cards gets done like this all the time

---

### Post by Defiler on 2004-11-24
I wouldn't exactly call this an old system. It's still under Dell warranty.
Does Ubuntu's default package set seriously require a newer card than this?
Guess it's back to FreeBSD for me.  :|

---

### Post by Magneto on 2004-11-24
I heard Ubuntu billed as a "high performance" OS while I was using Gentoo
I have an I745 with 8mb of ram and its like 5 years old- the ram is what is killing the resolution options in the newer versions of X - they say that card shouldnt be able to display certain resolutions
I only have Ubuntu on my laptop so I dont know about other systems 1st hand but you'd get the same from Fedora Core and Slackware w/Dropline.
If you really want to give it a go without getting too crazy-  google for Debian i845 xfree86 4.3  - ubuntu is debian and im sure there are some debian users using that card at a higher resolution

---

### Post by shanmuha on 2004-11-25
The problem is not ubuntu specific - Its got to do with the default video memory allocated in the BIOS. I had the same problem with a DELL GX270 - the solution was to increase the video memory to 16 MB - I have X running at 1280X1024@16 bits...

Good Luck!

---

