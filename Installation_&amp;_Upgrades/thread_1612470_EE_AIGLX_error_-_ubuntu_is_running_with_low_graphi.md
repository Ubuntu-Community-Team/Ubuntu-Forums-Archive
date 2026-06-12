---
title: "EE AIGLX error - ubuntu is running with low graphicmode"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by AstroPhysik on 2010-11-03
Hi,

My ubuntu 10.04.1  - 32 bit was running fine quite a while. Two days ago i did the new kernel update to 2.6.32-25-generic #45 ubuntu sat oct 16, 19:48:22 UTC 2010 - i686

Now i have a problem:**[COLOR=Red] (EE)AIGLX error: dlopen of usr/lib/dri/nouveau_viex_dri.so[/COLOR]**   could not be found or opened.


**1st Problem**: I could not logg into the desktop automatically without password. (i have deactivated it) I only had a Display of my installed user, but clicking at it, Linux reloded the graphical login screen again..

**2nd Problem**: Today i could not even log into the xserver, it said: Ubuntu is running in low graphics mode. (see digi cam photos..) 
And there i'm stuck. (this came without any try to solve 1st problem..??)


I'm able to get into the console and log in manually. I guess it had something todo with my nopassword settings, so i removed it with:  

```
sudo gpasswd -d username nopasswdlogin
``` (credits to sisco311 :P)

But the xserver is still in low mode? i have several menus to click(see picture)
1) Load ubuntu with low resulution:   ...this is not working, i got a freeze..
2) New grapic configuration: or load standard resolution or restore previous settings, or create new    
    settings are not working. (programming error?) clicking OK has no effect..
3) solve this problem:  ....has no effect
4) Exit and goto terminal ...YES this is working (-:
5) start xserver new:    ... got a freeze...



thank you for any help,
Astrophysik

---

### Post by AstroPhysik on 2010-11-03
In the directory of: [COLOR=Black]usr/lib/dri/   is no [/COLOR]**[COLOR=Red] nouveau_viex_dri.so[/COLOR]**   driver..
only... (see picture3)

lspci | grep vga   says:
01:00.0 VGA compatible controller: nVidia Corporation NV17 [Geforce4 MX 460] (rev a3)

---

### Post by AstroPhysik on 2010-11-05
After a little search i guess the kernel-update deleted my previous good working nVidia driver..
Since it run well, i didn't looked at it, which name it had had.., but i don't think that one of the drivers of picture3 will work with my nVidia chipset?

I think i have to re-install one of the following drivers with sudo -get apt...
_**nouveau:**_
**_nv_**: "xf86-video-nv"
**_nVidia_**

But there's my problem. I have only mobile internet (a umts-HSPDA usb-stick). 
1) how do i connect + give the password from the console to the HUAWEI stick?
2) Or i connect to the internet over my laptop, and plug a cable to the desktop-pc and set up all the dhcp stuff?
3) Download a driver to a usb stick, and tell sudo somehow to take it from the usb stick..

can anyone give me a tip with one of these?

many thanks
AP.

---

