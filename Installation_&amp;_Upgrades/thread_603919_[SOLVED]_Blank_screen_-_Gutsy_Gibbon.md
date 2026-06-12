---
title: "[SOLVED] Blank screen - Gutsy Gibbon"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by Hillerd on 2007-11-05
I just installed Gutsy Gibbon on my Acer Travelmate 4002LMi as 3rd boot (to keep WXP and the Fawn alive.
Blank screen has already been anounced for ATI 9600/9700 graphics cards, so I was not surprised to find it as well. Therefore I edited my /etc/x11/xorg.con, adding the 2 option lines:
> Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"LVDSBiosNativeMode" "false" 
	Option 		"DRI" "off"
EndSection

This didn't change a thing. The screen remains blank, harddisk is working, fan is heating my living room.

:confused:But now comes the funny part: I can start without problems in the recovery mode and then type "exit" to normally boot and get to the logon screen.

But anyway, I do not like this work around. How do I solve this issue?
Would it be gone if I installed the proprietary drivers?

Thanks for your help and good night for today.

---

### Post by Hillerd on 2007-11-06
:)Since I marked it as solved, here is how I made it work (well, first of all thanks to many ubuntuforums users, who gave me some hints).

Okay, first what I observed:
After installing Gutsy Gibbon from CD (fresh install) the rebooting showed a blank screen.
I found out, that if I boot in recovery mode (thanks to GRUB) and then just type "exit" I can login and everything works fine. 
So this means, that the graphics driver IS working, just not at the right time.

Next I checked the difference in the booting (highlight the line in the GRUB menu, press e(dit) ... :
normal boot has the "splash" option, recovery not.
So I changed that to "nosplash", pressed b(oot) and everything worked fine.

Now this change has to be made permanent:
Type ```
sudo gedit /boot/grub/menu.lst
```
find the right kernel and replace there "splash" by "nosplash" 
!!! be very careful with modifying menu.lst. If you make a mistake, GRUB is broken - but that can be repaired with the live CD !!!!

That's been it for me!
Bottom line: "splash" boot option does not work for ATI graphic cards.
Forget about modifying xorg.conf etc.

PS: as mentioned before: ATI Radeon 9600 or 9700, ATI drivers (not yet fglrx installed)

---

### Post by pdaigneault on 2007-11-07
It worked for me. I am new to this and my AMD/ATI setup using an X800 PCIE card was giving me same problem as yours. I followed your directions and was able to boot without any trouble. Had some work figuring the command thought i was a 1 but finally got it right. :lolflag: thanks Paul D

---

