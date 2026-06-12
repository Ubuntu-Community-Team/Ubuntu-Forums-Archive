---
title: "Maybe its simple? Edgy lcd displays video out of range"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by frankelr on 2006-10-27
I know everyones busy, but You might know the answer.
1st) 6.06 ran and runs fine.
2nd) 6.10 starts up ... gets to linux boot and my Dell LCD Display
goes to "Video mode not supported", after the boot switches to
graphical mode 6.10 resumes proper operation.  On shut down after leaving graphics mode, the "mode not supported message" reappears.

When I run 6.10 in rescue mode, the boot displays on screen
When I use Init5 graphics starts and runs, on shutdown all is ok again

Any clue where the trouble might be? grub?, kernel? 

Bob

---

### Post by mgmiller on 2006-10-30
It sounds like your monitor is only going out of range during the non graphical part of the boot.  You can change this behavior by editing /boot/grub/menu.lst

back it up first
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lstold

```

Next, open menu.lst with gedit
```
sudo gedit /boot/grub/menu.lst
```

Scroll down till you reach the following area:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash 

you will edit the last line to add a vga option to it.  for example:
# defoptions=quiet splash vga=791

To know which vga= number to use, consult this handy chart:

640x480 800x600 1024x768 1280x1024
......768...........771.............773...........775.................256 colors
......784...........787.............790...........793.................(8 bit)
......785...........788.............791...........794.................(16 bit)
......786...........789.............792...........795.................(24 bit)


So to use 24 bit color at 1024x768 resolution you would use vga=792

Next, save the document, and finally to make these changes active and make sure they carry through to future kernel updates run the following command:

```
sudo update-grub
```

This will append the change to all kernel lines.

reboot and see if it works, if not try a different vga=number till you hit one that is in range for your monitor.  Most flat panels of 17 and 19" are 1280x1024 native resolution, so maybe the 794 or 795 options will work best.  You won't know till you try.  

Good Luck

---

### Post by cholly on 2006-10-30
I have the reverse problem.

I upgraded via update manager. After restart everything works fine *until* it starts "graphics mode." I'm using an old CRT and it tells me the frequency is out of scan range. It's low, like for a in the 20's. 

I can hear the login prompt sound and can log in and then hear the startup sound. I switched to a virtual terminal and examined the xorg.conf file and the backup and they appear to be the same in the display section.

I don't have a grub menu of any kind. likely because ubuntu is the only OS on this machine. I get a brief grub count down then the typical Linux start up.

Any ideas?

---

### Post by DuncanNZ on 2006-11-07
Please file a bug at [http://launchpad.net](http://launchpad.net) so a developer has a chance to look at it.

---

### Post by dcymbal on 2006-12-05
I have been struggling with this issue for a couple days since my upgrade from dapper to edgy.  My problem sounds like the original poster's.  I get the grub menu, boot the default kernel.  For what should be the ubuntu splash screen and services loading screen my monitor goes "Frequency out of range" this lasts until X starts and I get my gdm login.  At this point all is well and you can run graphical or switch to text-based virtual consoles.  Likewise on shutdown the monitor again goes "Frequency out of range" for what would normally display as the shutdown sequence screen.  I tried a whole slew of vga=xxx in menu.lst with no luck.  I have had ubuntu since 5.04 on this system with no previous problem.  

Video card is a SiS 630/730.  Monitor is an Envision EN9410e.  Let me know if there is anything else I can try or more info I can provide.  It is not a huge issue but it is handy for users to see the system boot process going ok and not freak out when they see the unexpected "Frequency out of ranger" message.

---

### Post by giovaea on 2006-12-08
> **dcymbal said:**
> I have been struggling with this issue for a couple days since my upgrade from dapper to edgy.  My problem sounds like the original poster's.  I get the grub menu, boot the default kernel.  For what should be the ubuntu splash screen and services loading screen my monitor goes "Frequency out of range" this lasts until X starts and I get my gdm login.  At this point all is well and you can run graphical or switch to text-based virtual consoles.  Likewise on shutdown the monitor again goes "Frequency out of range" for what would normally display as the shutdown sequence screen.  I tried a whole slew of vga=xxx in menu.lst with no luck.  I have had ubuntu since 5.04 on this system with no previous problem.  

Video card is a SiS 630/730.  Monitor is an Envision EN9410e.  Let me know if there is anything else I can try or more info I can provide.  It is not a huge issue but it is handy for users to see the system boot process going ok and not freak out when they see the unexpected "Frequency out of ranger" message.


I think to have the same problem. I can see the splashscreen, but when there would appear display login, the monitor goes out of frequence, if I write my userid and password everything run. Have you any suggest to see the login prompt? 
Video card GeForce FX5200 + Monitor Atlantis I-See171.
Bye

---

### Post by _simon_ on 2006-12-08
> **giovaea said:**
> I think to have the same problem. I can see the splashscreen, but when there would appear display login, the monitor goes out of frequence, if I write my userid and password everything run. Have you any suggest to see the login prompt? 
Video card GeForce FX5200 + Monitor Atlantis I-See171.
Bye

I'm not sure if this will help but once you have logged in, from terminal do:

```

sudo gedit /etc/X11/xorg.conf

```

Scroll down to 

```

Section "Screen"

```

Remove any resolutions that your monitor does not support and add any common ones in that are missing.

My Screen section looks like this:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TripleBuffer" "true"
    Option         "DynamicTwinView" "False"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by giovaea on 2006-12-09
Thanks, I have erased in xorg.con from <<SubSection "Display">> modes over "1280x1024".
Now I can see Login display
Thank you

---

### Post by _simon_ on 2006-12-09
:)

---

### Post by dcymbal on 2006-12-09
> **giovaea said:**
> I think to have the same problem. I can see the splashscreen, but when there would appear display login, the monitor goes out of frequence, if I write my userid and password everything run. Have you any suggest to see the login prompt? 
Video card GeForce FX5200 + Monitor Atlantis I-See171.
Bye

Actually your problem is different from mine.  You see the splashscreen but have problems seeing the gdm login.  I don't see the splashscreen but I do get the gdm login.  In my case it would appear the issue is not X-related.

---

