---
title: "Problems With Ubuntu Installation on Dell Studio 15 Laptop"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by fluoridemindcontrol on 2010-01-18
It took me roughly 15 hours of trial and error after reading through numerous posts to properly install Ubuntu 9.10 on my brand new Dell laptop.  For those running into similar installation issues (there appears to be a lot based on the number of posts I found out there) I decided to post what worked for me.  This is gathered from many different posts on several different sites.  Sorry if it appears elsewhere and I am just rehashing old knowledge.  Also, no guarantees this will work for you or that there are not easier ways to do it;  this is just what worked for me. 



  The problem is that it appears that Dell is using a quasi-unsupported graphics chipset.  To complicate matters the 915resolution hack will not work.  On a side note,  I find it very disturbing that Dell sells a laptop that they claim works (and ships!) with Ubuntu out of the box, but really  does not...  but that is for another post.
 

 
[LIST=1]
[*]Install the distribution in text     mode (both 32 and 64 bit work).  The graphical interface mode will     NOT work.
[*]After installation boot up the     operating system.  You need to use text mode to do everything     initially.  I needed to press ctrl+alt+fn+F1 to first have the OS     recognize the monitor.  Then I could enter into text mode     (ctrl+alt+F1).
[*]Kill Xserver (sudo /etc/init.d/gdm     stop)
[*]Allow the system to make a new     xorg.conf file (sudo Xorg -configure).  This will give you a new     xorg.conf file (xorg.conf.new in your directory)
[*]Move this to the /etc/X11/ and     rename it as xorg.conf.  This will allow the GUI to operate in low     resolution mode.
[*]Restart Xserver (sudo     /etc/init.d/gdm start).
[*]Logout and reboot.
[*]You will get an error message that     only the low resolution mode will work.  That is OK, proceed in low     resolution mode.  Open up xorg.conf file (sudo vi /etc/X11/xorg.conf     using the vi editor).
[*]Configure the following sections     in the configuration file:
[/LIST]
 

 Section "Monitor"
     Identifier "Configured Monitor"
     Vendorname "Generic LCD Display"
     Modelname "LCD Panel 1280x800"
     Horizsync 31.5-50.0
     Vertrefresh 56.0 - 60.0
     modeline "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
 EndSection
 

 Section "Screen"
    Identifier   "Default Screen"
    Monitor      "Configured Monitor"
    Defaultdepth   24
    Device      "Configured Video Device"
    Option       "AddARGBGLXVisuals" "True"
    Option       "DisableGLXRootClipping" "True"
 EndSection
 

 Section "ServerLayout"
         Identifier      "Default Layout"
         Screen          "Default Screen"
        InputDevice     "Mouse0" #identifier for my mouse
 EndSection
 
[LIST=1]
[*]logout and reboot
[*]You will get the same error     message as when you used the self configuration setting.  Select the     second option in (the list that deals with fixing the problem).
[*]You will then be given an     additional list of option.  Select the “Use previous settings”     option.
[/LIST]
 

     On steps 11 and 12 I am not sure about the exact phrasing of the options, but it should be obvious which ones to select.
 

 
[LIST=1]
[*]You should now have a login-screen     in near optimal resolution for this system ( verify by using xrandr     in the terminal.  It yields the following for me:
[/LIST]
 

     Screen 0: minimum 320 x 200, current 1366 x 768, maximum 1366 x 1366 
     VGA disconnected (normal left inverted right x axis y axis) 
     LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm 
            1366x768       59.6*+ 
            1360x768       59.8   
            1024x768       60.0   
            640x480        59.9   
     HDMI-1 disconnected (normal left inverted right x axis y axis) 
     TV disconnected (normal left inverted right x axis y axis)

---

### Post by clevertomato on 2010-01-26
I just want to say that I have a Studio 15 (1555 to be exact) that did not require the above installation steps. I just installed Karmic 64-bit the normal way. It went fine. Only problem was resume (ATI proprietary drivers fixed that) and brightness Fn keys & lid closure awareness (adding " noapic" to Grub fixed these).

I have an ATI 4570 GPU.

---

### Post by fluoridemindcontrol on 2010-02-16
I just did a clean instal of 9.10 (removed that pesky Windows partition) and had none of my previous problems this time (added noapic this time though).

---

### Post by fluoridemindcontrol on 2010-02-17
> **fluoridemindcontrol said:**
> I just did a clean instal of 9.10 (removed that pesky Windows partition) and had none of my previous problems this time (added noapic this time though).

And by I had no problems, I mean on the instal and initial boot after the instal.  To obtain anything other than 800x600 resolution I still needed to manually edit my xorg.conf file.

---

