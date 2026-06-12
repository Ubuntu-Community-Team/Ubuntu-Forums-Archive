---
title: "No Dual Screen after upgrade"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by hmsslm on 2010-04-30
Hi All,

I have just updated my Ubuntu from 9.10 to 10.4.
But after restarting, my login screen didn't show up, instead it showed flickering screen.
After several times restarting, and trying to fix, at last, I went to the "Recovery Mode" in the boot menu, and choose to re-generate the display configuration.

After restart, I got my login screen again. But, now I got another problem.
The second monitor show nothing. And when I execute 'xrandr' or 'xrandr -q' it showed only my first monitor (before update, it showed both of my monitors). I tried to change the 'xorg.conf' to my previous configuration. The file wasn't there. When I re-created it, it didn't help. Auto Detection in System->Preferences->Display didn't help either (it showed only one monitor).

I've been looking through the forums, but found nothing brings to the solution.

As Info, I'm using NVIDIA GT8600 (dual DVI)

My question is:
- Is Ubuntu 10.4 not using xorg.conf anymore?
- How could I know which configuration used by the Xserver?
- How could I find out which graphic driver being used?
- How could I change my graphic driver?
- How to configure my computer so that I can get my dual screen again?

Thanks for your help before.
Please tell if I should submit any information needed to solve this problem.

Best regards,
hmsslm

---

### Post by Grenage on 2010-04-30
> **hmsslm said:**
> My question is:
- Is Ubuntu 10.4 not using xorg.conf anymore?
- How could I know which configuration used by the Xserver?
- How could I find out which graphic driver being used?
- How could I change my graphic driver?
- How to configure my computer so that I can get my dual screen again?

9.10 didn't need an xorg.conf, but like 10.04, it will still use one if present.  Do you have the nvidia-settings app installed?

---

### Post by hmsslm on 2010-04-30
> **Grenage said:**
> 9.10 didn't need an xorg.conf, but like 10.04, it will still use one if present.  Do you have the nvidia-settings app installed?

Thanks for your fast reply.
Which configuration file will be used then, when no xorg.conf found?

I have tried 'nvidia-settings', but got this message box dialog 'You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.'
When I run the 'nvidia-xconfig', it just generated an xorg.conf (which also doesn't help).

PS: as additional info, in the first terminal, I got this message before the login prompt 'mountall: Disconnected from plymouth'

---

### Post by strange_cathect on 2010-04-30
I'm having a similar problem. Dual screen is gone. I'm in low-graphics mode. When I try to change my monitor settings in the Control Panel, I am told the following:

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

However, running x-config does not allow me to use the NVIDIA resolution tool.

---

### Post by Grenage on 2010-04-30
It's done automatically, in the background; I don't 'think' there is a config file specifying the settings.

*System/Administration/Hardware Drivers*

Can you enable an Nvidia driver there?  If so, then run nvidia settings again:

```
gksu nvidia-settings
```

---

### Post by strange_cathect on 2010-04-30
My recommended driver is already enabled. There is a separate program called nvidia-settings but it appears broken in 10.10.

---

### Post by Grenage on 2010-04-30
I am performing an upgrade to 10.04 as we speak, and this machine uses Nvidia twinview across two monitors.  If you don't get a result before I'm done, I'll be in a much better position to see what your situation is.

Out of curiosity, **strange_cathect**, do you have an xorg.conf?  If so, can you laste it here?

---

### Post by hmsslm on 2010-04-30
> **Grenage said:**
> I am performing an upgrade to 10.04 as we speak, and this machine uses Nvidia twinview across two monitors.  If you don't get a result before I'm done, I'll be in a much better position to see what your situation is.

Out of curiosity, **strange_cathect**, do you have an xorg.conf?  If so, can you laste it here?


Hi Grenage,
I did it.... At last........... Thanks a lot.

After I tried your suggestion, to open 'System->Administration->Hardware Driver' , I was asked to activate/select the proprietary nvidia  drivers. After activating it, I was asked to restart. After restart... hoopla.... I can run my nvidia-settings, and my second monitor is shown as 'disabled'. After enabling it, apply, then the second screen shown up...

After that I got another problem  that after logout, and re-login, the second screen is gone. I found out later, that I need to 'Save to X Configuration File'

After that, everything goes as I expected.
Thanks a lot for your help.

That it is solved for me, how could I change the prefix of the thread to  [SOLVED] ?

For strange_cathect, or other user, in case you need it, I post my xorg.conf below:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Fri Mar 12 01:42:27 PST 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2208WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0                                                                                                                                                     
    Option         "DPMS"                                                                                                                                                           
EndSection                                                                                                                                                                          
                                                                                                                                                                                    
Section "Device"                                                                                                                                                                    
    Identifier     "Device0"                                                                                                                                                        
    Driver         "nvidia"                                                                                                                                                         
    VendorName     "NVIDIA Corporation"                                                                                                                                             
    BoardName      "GeForce 8600 GT"                                                                                                                                                
    Option         "NoLogo" "True"                                                                                                                                                  
EndSection                                                                                                                                                                          
                                                                                                                                                                                    
Section "Screen"                                                                                                                                                                    
    Identifier     "Screen0"                                                                                                                                                        
    Device         "Device0"                                                                                                                                                        
    Monitor        "Monitor0"                                                                                                                                                       
    DefaultDepth    24                                                                                                                                                              
    Option         "TwinView" "1"                                                                                                                                                   
    Option         "metamodes" "DFP-0: 1680x1050_60_0 +0+0, DFP-1: nvidia-auto-select +1680+0; DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1680+0"                   
    SubSection     "Display"                                                                                                                                                        
        Depth       24
    EndSubSection                                                                                                                                                                   
EndSection

```

---

### Post by Grenage on 2010-04-30
Glad you got it sorted.  Top right of the page, *Thread Tools*; you should be able to change the status there.

---

### Post by disciplefk on 2010-04-30
I too had a lot of trouble getting my dual monitor setup to work.  I even when from a fresh install.  I did get everything to work, but lagged horribly when I enabled xirrama.  So I had to revert back to unrestricted drivers.  Would there be a fix for it?  Without xirrama enabled I could not drag windows across the two screens.

---

### Post by Grenage on 2010-04-30
What card do you have?

---

### Post by disciplefk on 2010-05-10
nvidia 7950

---

### Post by TheFu on 2010-05-13
I just updated from xubuntu 9.10 to lubuntu 10.04 and had similar issues with my dual monitor config. I did a fresh install, not an upgrade due to cockpit error.  Anyway, I wrote a blog entry on how to get dual monitor support working in Ubuntu. 

It should work for any desktop environment (gnome, kde, xfce, lxde or pure X/Windows), since it doesn't use any menu'd programs.
[http://jdpfu.com:82/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver](http://jdpfu.com:82/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver)

---

