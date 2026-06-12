---
title: "installed ubuntu 12.10, now I can't boot windows or ubuntu"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by tnmedic on 2013-02-03
I installed Ubuntu 12.10 on a xp machine last night. I installed it from a live usb. It let me install it fine, but when it restarted the computer I could not boot into windows or ubuntu. When I try to boot windows, it goes to a blank screen with a blinking underscore at the top left, when I try to boot Ubuntu it says several things are ok then it gives me this error.
 
(different numbers here) [drm:drm_crtc_helper_set_config] *error* failed to set mode on [crtc:10]
 
I tried reinstalling Ubuntu, did the same thing again.
 
so I ran Ubuntu off the live usb, and installed boot repair, ran it and when it restarted it still does the same. This is the URL boot repair gave me.
 
[http://paste.ubuntu.com/1603766/](http://paste.ubuntu.com/1603766/)
 
Any and all help would be greatly appreciated

---

### Post by Bashing-om on 2013-02-03
tnmedic; Hi ! Welcome to the forum.
Appears you are afflicted with two problems, graphics and the bootloader.

Let's see what we can do to get ubuntu up and then fix the bootloader.

Boot to the grub menu, with the ubuntu "normal" kernel line highlighted press the "e" key for edit mode -> boot parameters: arrow down to the line containing the term "quiet splash" and arrow across to this term and insert "nomodeset" -with out the quotes. ctl+x to continue to boot. -> GUI login.

Login: 
Install graphics driver:
Ubuntu software center ->software sources (task bar menu)-> Additional Drivers(tab); install the recommended driver.
Reboot.

Does this get you into ubuntu, or do we first have to work on grub to get to the point to install a graphics driver ?
[INDENT][INDENT]try'n to help

[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2013-02-03
I would strongly advise AGAINST installing any additional video drivers until you confirm it is booting OK -- and does NOT work well with the default video drivers.

Folks running 12.10 have reported LOTS of problems installing restricted video drivers -- some of which could have been avoided by simply NOT installing them.

An example is that AMD dropped restricted driver support for ALL their HD 2x/3x/4s video chipsets, so anyone installing the restricted driver with this chipset would end up with no useful display  -- and a LOT of work ahead of them to get it working again.

---

### Post by Bashing-om on 2013-02-03
@ Mark, Thanks for the heads up// But am I not reading this correctly:
>  [drm:drm_crtc_helper_set_config] *error* failed to set mode on [crtc:10]that  the kernel can not find a driver for the monitor ?

I look at it like this; not much one can do 'till there is a display ???
[INDENT][INDENT]- still learning even after all these years -
[/INDENT][/INDENT]

---

### Post by tnmedic on 2013-02-03
Thanks, adding the nomodeset got me into ubuntu.  I think I am to understand that I am not to install video driver correct?

---

### Post by Bashing-om on 2013-02-03
tnmedic; 

Let us by all means take Mark's advise and Not at this time install any drivers. What needs done next can be done with the the display running on the default "vesa" driver - "nomodeset" disables kernel mode setting.
Now we want to get to windows from ubuntu:
Command line interface -> key combo ctl+alt+t
terminal code:
```
sudo update-grub
``` I expect the bootloader config files to be regenerated and pick up windows and chainload window's bootloader to ubuntu grub menu.
Reboot.

Is Windows now an option in ubuntu's grub boot menu ?

[INDENT][INDENT]try'n to help

[/INDENT][/INDENT]

---

### Post by tnmedic on 2013-02-03
I'm getting ready to do the grub update, just wanted to clarify.  Windows is currently an option in the grub menu, but when you try to load it it just gives the blank screen with the blinking cursor.
 
updating now

---

### Post by tnmedic on 2013-02-03
Alright, updated grub, it does the same thing.  There is a windows xp option, but when you select it.  It goes to the blank screen blinking cursor.

---

### Post by Bashing-om on 2013-02-03
tnmedic;

Apparently window's bootloader does not exist. Will require windows to fix. Mark is great with windows, lets see what he has to advise.


[INDENT][INDENT]windows is not in my depth 

[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2013-02-04
We should first confirm that the XP partition is there and of the proper format.  Open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one). That will list out the partitions, their formats and their sizes.

When you get into Ubuntu, you should be able to mount the XP partition from the "home" tile in the nav bar on the left.

When you do that, see if there is a boot.ini file. If so, paste the contents back here.

Sorry, but the only way I know to fix XP boot problems is from an XP CD.  If you don't have such a CD, I don't know what to tell you to rebuilt the boot loader files.

---

### Post by oldfred on 2013-02-04
Boot script shows sdb1 with the normal Windows boot files. 

Two possible issues. After any resize, Windows needs chkdsk. I would run chkdsk from your XP disk.
But your Windows says it is the first drive in boot.ini, but Ubuntu is seeing it as sdb or second drive. First drive seems to be your flash drive installer and some BIOS do promote that to the first drive. 
Grub is also trying to do a drivemap to make Windows think it is hd0 even though you booted from hd1, but that may be confusing things.

I would run chkdsk and try removing flash drive. Ubuntu uses UUIDs so it still should boot if drive number is changed.

---

### Post by tnmedic on 2013-02-04
This is the Boot.ini
 
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\windows
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\windows="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
 
I used to have a XP disk around somewhere.  I'll have to try and find it again.

---

