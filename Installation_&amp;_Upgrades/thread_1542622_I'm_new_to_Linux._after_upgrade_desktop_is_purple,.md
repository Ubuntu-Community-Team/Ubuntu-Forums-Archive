---
title: "I'm new to Linux. after upgrade desktop is purple, but nothing else."
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by canonge2 on 2010-07-30
Hi,
I tried to download the iso for a fresh install, but I couldn't get it to run without errors. So, I found an old copy of 8.04 LTS I had ordered a couple of years back and used that. I updated my system and then upgraded to 10.04 LTS. It just finished downloading, cleaning up, and restarting. 

My problem is after it asks for my login info and I login, the screen is empty except for the purple background. The only thing I can do is right click on screen and get a menu. It doesn't have any buttons anywhere.

Can someone please help?
Thanks,
Melissa

---

### Post by canonge2 on 2010-07-31
Hello,
Just wanted to post my solution in case anyone has the same problem. Now I just have to figure out how to change resolution.

[http://www.troublefixers.com/solved-ubuntu-desktop-does-not-load-after-entering-the-username-and-password/](http://www.troublefixers.com/solved-ubuntu-desktop-does-not-load-after-entering-the-username-and-password/)

---

### Post by canonge2 on 2010-07-31
Hello, 
I want to post my resolution error in case someone else is having a problem.

[http://ubuntuforums.org/showthread.php?t=1491414](http://ubuntuforums.org/showthread.php?t=1491414)
Here is the excerpt that helped me!

 Re: How to change Screen Resolution in Old P-3 Desktop
your video card is
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)

try this:

open a terminal and run
Code:

sudo touch /etc/X11/xorg.conf

then
Code:

gksudo gedit /etc/X11/xorg.conf

in the previous 2 commands make sure you put X11 and not x11 as Linux is case sensative. then add
Code:

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS" "true"
	HorizSync	30.0-60.0
	VertRefresh	50.0-70.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
			Depth		24
			Modes		"1024x768" "800x600"
	EndSubSection

EndSection

save and reboot and you should have 1024x768 resolution.

**FYI Make sure you type it exactly or Ubuntu wont load. I had forgotten to add EndSubSection, so I know from experience. LOL
HTH,
Melissa
__________________

---

