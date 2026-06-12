---
title: "Cannot see GUI"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by Duckinabox on 2008-03-02
I'm installing the latest version of Ubuntu on a system with 512MB RAM, AMD Sempron processor and a 160GB HD (I'm not giving it the whole drive as I'm dual-booting XP (:P))

The system starts up from the disc, and I select "Install or run Ubuntu" (I can't remember exactly what it says). I get the lovely loading bar...then the other one. After it has loaded I get a blank screen. The logon sound plays, but I can't see anything.

Actually, I lied about the screen. It's not entirely blank. I have thick bars of coloured noise across it and at the top I have the Ubuntu logo (tiled) seemingly made out of "red noise". I assume this is a problem with my graphics card settings. Can anybody help?

Thanks. I'd really love to use Ubuntu ;)

---

### Post by Pumalite on 2008-03-02
Try the Alternate CD.

---

### Post by kdarkentity on 2008-03-02
> **Duckinabox said:**
> I'm installing the latest version of Ubuntu on a system with 512MB RAM, AMD Sempron processor and a 160GB HD (I'm not giving it the whole drive as I'm dual-booting XP (:P))

The system starts up from the disc, and I select "Install or run Ubuntu" (I can't remember exactly what it says). I get the lovely loading bar...then the other one. After it has loaded I get a blank screen. The logon sound plays, but I can't see anything.

Actually, I lied about the screen. It's not entirely blank. I have thick bars of coloured noise across it and at the top I have the Ubuntu logo (tiled) seemingly made out of "red noise". I assume this is a problem with my graphics card settings. Can anybody help?

Thanks. I'd really love to use Ubuntu ;)

Try booting from the live -cd in safe graphics mode, its one of the advanced settings uder one of the F keys.

---

### Post by Duckinabox on 2008-03-02
Safe graphics doesn't work...I'll try the alternate CD

---

### Post by Pumalite on 2008-03-02
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on your iso, burn at 4x or less as image in good quality CD-R media, check CD integrity before install.

---

### Post by Duckinabox on 2008-03-03
I did md5 check it and integrity check it and everything. Next time I boot Linux I'll try and get to a terminal and see if xorg is set up right.

---

### Post by Duckinabox on 2008-03-04
I've successfully installed Ubuntu from the Alternate CD...can anyone please tell me how to setup xorg from the terminal? Sorry about this - it seems to be different from the Mandriva terminal.

---

### Post by Pumalite on 2008-03-04
Are you at the Desktop and what do you want to accomplish? Have you enabled 'Restricted Drivers?
gksudo gedit /etc/X11/xorg.conf
Backup your file first.

---

### Post by dstew on 2008-03-04
Use **sudo dpkg-reconfigure xserver-xorg** for a text-based reconfiguration utility.

---

### Post by Duckinabox on 2008-03-04
No I haven't got the desktop - it still gives me the white bars and the dodgy Ubuntu logo. I think it's just the graphics that are wrong - I can type in my username <Tab> password <Return> and I hear the logon sound etc. I'll get back when I've tried the above text -based configuration.

---

### Post by Pumalite on 2008-03-04
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver, then:
startx

---

### Post by Duckinabox on 2008-03-05
I've tried the text-based configuration to no avail. Ubuntu didn't automatically detect my nVidia 7600GT card or my 1280x1024 Hanns-G monitor, so I probably set it to the wrong drivers etc.

Does somebody know how to reconfigure xorg (text-based) for this configuration?
Thanks

---

### Post by dstew on 2008-03-05
From the command line, do ```
sudo dpkg-reconfigure xserver-xorg
```Choose the vesa driver. That should at least get you a desktop. Once you have the desktop, check the System --> Administration --> Restricted Drivers Manager to see if you can install a driver for that card.

---

### Post by Duckinabox on 2008-03-05
The vesa driver doesn't seem to work. Are there any other settings I need to give it too? I'm telling it to use 1280x1024@24 bit. Should I set a lower resolution/colour depth etc.? Oh and do I have to reboot each time?

---

### Post by dstew on 2008-03-05
Maybe the vesa driver can't handle that resolution. Try 1024 x 786 (I think that is one).

Each time you reconfigure you have to restart the xserver. The command is **startx**. You can also try ctrl-alt-backspace. That key combination restarts the xserver. However, sometimes if the xserver becomes unresponsive, you have to reboot. Or, you can try to kill the xserver process with **sudo killall gdm** (for "Gnome Dislpay Server").

If vesa won't work you can try the **vga** driver. That I think can do 1024 x 786.

---

### Post by Pumalite on 2008-03-05
When it ask you for your video card, put Nvidia Ge Force 7600GT (ot whatever); when it asks you for driver, try 'nvidia' or 'nv'

---

### Post by firecrow8 on 2008-03-06
I have the Same Problem. i just tried to open the live cd to install it and see that blank screen fade horozontal bars thing. 

Compaq Presario
Windows Vista as Alter OS
1G RAM
AMD 64 Athlon X2
NiVidia GeForce Go 6100
widescreen 1280 x 800 resolution

---

### Post by dstew on 2008-03-06
firecrow, your problem is different than the problem the original poster that started this thread had (or maybe still has). He is having trouble with an installed system, you are having trouble booting the Live CD. In your case, consider trying to run the Live CD in Safe Graphics mode. It is either a menu choice, or you get it by pressing F6 at the opening Live CD menu.

---

### Post by Duckinabox on 2008-03-06
No sorry I wasn't clear. I had this problem at first with the Live CD and then installed Linux using the alternate text-based installer (God has given me a large HDD :)). Now I have exactly the same problem with the installed version. None of the above drivers seem to work in 1024x768 either; should I try disabling the kernel framebuffer thing?

---

### Post by Pumalite on 2008-03-06
That's another choice you have; when reconfiguring your xserver, you get to a point where you can choose 'noframebuffer'. Do it and see if it works.

---

### Post by firecrow8 on 2008-03-06
thanks for clarifying dickinabox (great name by the way best SNL skit ever) . I'm a dick outside the box...heheh. 

back to business.

I tried botting with all sorts of configurations. nothing made a difference.
boot: **live noacpi**
boot: **sudo killall gdm**
boot: **acpi=off**
boot: **sudo dpkg-reconfigure xserver-xorg**
boot: **all_generic_ide**

one clue that has come up is that when the system loads the checklist e.g. *building system keys  [ OK ], * loading divice hardware drivers [ OK ].** it displays an error after * loading Gnome Dislay Manager **. and error is also displayed for * Unix Printing Something or Another

what puzzles me is this:
**is there a way to turn off the monitor driver?** because the screens before booting into the live CD look fine. the initial screen looks fine. the one with the menus of how to boot. and then the loading bar looks fine.

---

### Post by Pumalite on 2008-03-06
> **firecrow8 said:**
> thanks for clarifying dickinabox (great name by the way best SNL skit ever) . I'm a dick outside the box...heheh. 

back to business.

I tried botting with all sorts of configurations. nothing made a difference.
boot: **live noacpi**
boot: **sudo killall gdm**
boot: **acpi=off**
boot: **sudo dpkg-reconfigure xserver-xorg**
boot: **all_generic_ide**

one clue that has come up is that when the system loads the checklist e.g. *building system keys  [ OK ], * loading divice hardware drivers [ OK ].** it displays an error after * loading Gnome Dislay Manager **. and error is also displayed for * Unix Printing Something or Another

what puzzles me is this:
**is there a way to turn off the monitor driver?** because the screens before booting into the live CD look fine. the initial screen looks fine. the one with the menus of how to boot. and then the loading bar looks fine.

Have you tried the Alternate CD?

---

### Post by firecrow8 on 2008-03-06
no. what alternate CD? where do I get it? 
are you refering to a different download?
or simply reburn the download and see if that works?

---

### Post by Pumalite on 2008-03-06
Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'

---

### Post by Duckinabox on 2008-03-07
Well I'm back and I've tried turning off the kernel framebuffer thing with limited success. I now get a white screen with the mouse cursor when I start up. I type my username and password and hit enter, and the white changes to a different kinda brownish colour with white bars at the top and bottom (the gnome toolbars with no buttons). Then the desktop background changes back to the stripes of noise. I can still move the mouse cursor and see the blank white toolbars though...

The above was using the "nv" driver. The other two ("vesa" and "vga") just give me the original problem.

---

### Post by firecrow8 on 2008-03-08
The **Alternate CD** referred to above is from the downloads page. obtained by checking the box at the bottom that says something like. "alternate CD text installer isntead of live CD".

so the instalation worked. YAY right!!!!!!!!!!!!!!! **no.**................ now it boots with the same problem from my hard disc instead of the CD.

blank screen. with horozontal lines.

whatever the issue is **it has something to do with the monitor**. does anyone know how to disable the monitor driver or somehow tell UBUNTO to stop trying to load whatever it's loading so I can get into the settings???????????????????????

---

### Post by Pumalite on 2008-03-08
This is the moment you have to reconfigure your xserver:
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver or, then 
startx

---

### Post by firecrow8 on 2008-03-08
**IT WORKS IT WORKS ** I'm posting while booted up in linix now **WOO HOO** I found another thread on the forum listing my specific computer model (compaq presario F500) with the same issue and the settings of 'noapic nolapic vga=792'

it makes sense that it was the vga setting just had to find the right code.

---

### Post by Pumalite on 2008-03-08
Glad you got it working.

---

### Post by Duckinabox on 2008-03-08
I would like to try this. Can anybody please give me specific instructions, from GRUB, of how to do the above?

---

### Post by Duckinabox on 2008-03-09
Oh and another thing - I don't seem to have the "nvidia" driver. Do I need that? I've got "nv".

---

### Post by uberlube on 2008-03-09
are you running Ubuntu from your HD or the live CD. Either way you will need to set the proper vga into the boot process to get into the desktop. Then from there you install your nvidia drivers using ENVY. There are 2 ways of editing the boot process but they depend on what you are booting from. Ill let you know what to do once you tell me.

---

### Post by Duckinabox on 2008-03-09
I'm running from the HD (GRUB bootloader)

---

### Post by uberlube on 2008-03-09
OK during GRUB, while the login to Ubuntu line is highlighted, press 'e' to edit. It will bring you to a new page with a few options. Highlite the line that says kernal and press 'e' again. Then at the end of the line, delete 'quiet splash --' and add 'vga=791'. Then press enter which will bring you back to the menu and then press 'b' to boot.

---

### Post by Duckinabox on 2008-03-09
OK I've tried that...and it didn't work :(
At the end of my "kernel" line it said "quiet splash" instead of "quiet splash --". Is that a problem? I deleted it anyway and tried it. I got the later problem I mentioned in this thread - I can see my cursor but on a white screen. However when I press Ctrl+Alt+F1 to get to terminal mode, all I see are vertical pink lines.

The cursor and the white screen are courtesy of the "nv" driver, I think. Should I reconfigure to use "vga"?

Thanks

---

### Post by Duckinabox on 2008-03-14
Did anyone find a solution to this?

---

