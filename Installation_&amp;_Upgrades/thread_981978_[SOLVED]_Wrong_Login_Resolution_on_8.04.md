---
title: "[SOLVED] Wrong Login Resolution on 8.04"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by kracheck on 2008-11-14
I've just installed Ubuntu 8.04 on my old Dell Desktop.  It has a "Ati Radeon 7200" videocard attached to a Sony "SDM-N50 LCD Monitor".  I have a problem with my Gnome login screen resolution; the resolution of the login screen is different (800x600) to the one I'm actually using on the only session I have for Ubuntu in this computer (1024x768@60).
Is there any way you can adjust the login screen resolution in order to match it with the one of the session??

I have tried switching themes without any luck.
I have tried, again without any luck, to change the /etc/X11/Xorg.conf file as follows :

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes	"1024x768@60"
		Virtual	1024 768
	EndSubSection
EndSection

I came across a solution for a "login text size issue" by changing the /etc/gdm/gdm.conf file.

sudo gedit /etc/gdm/gdm.conf
(Find)
[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0
(Change to)
[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 -dpi 96

What would be the similar steps to adapt the above gdm.conf for let's say 1024x768 resolution ?

Or Would it be better to try using a boot script ? Something along these lines :

#! /bin/sh
# /etc/init.d/CustResolution
xrandr --size 1024x768

Make it executable and drop it in /etc/init.d
Make a symbolic link to cause the script to be executed when the system boots using :
sudo update-rc.d CustResolution defaults.

Thanks in advance.

---

### Post by lyni on 2008-11-15
sorry this is the obvious question.  have you tried System>Preferences>Screen Resolution?

---

### Post by Mr_JMM on 2008-11-15
> **lyni said:**
> sorry this is the obvious question.  have you tried System>Preferences>Screen Resolution?

AFAIK that won't help with the login screen.

Are you using ATI graphics card?

[http://ubuntuforums.org/showthread.php?t=359310]("http://ubuntuforums.org/showthread.php?t=359310")

---

### Post by snaggapuss on 2008-11-15
Check out this link it helped me with log in screen
[http://ubuntuforums.org/showthread.php?t=913465&highlight=large+login+screen](http://ubuntuforums.org/showthread.php?t=913465&highlight=large+login+screen)

---

### Post by kracheck on 2008-11-15
Yup I have tried System > Preferences > Screen Resolution.
I have a 1024x768 Resolution with a Refresh Rate of 60 Hz and a Rotation set to normal.
That's the strange thing about all this, once I'm at the desktop level everything is ok, it's the Login Screen that has a totally wrong resolution.

---

### Post by kracheck on 2008-11-15
Yes I'm using an old Ati card.
The lspci output is :
01:00:0 VGA compatible controller : ATI Technologies Inc Radeon R100 QD [ Radeon 7200]

I'm afraid that the suggested solution on 
[http://ubuntuforums.org/showthread.php?t=359310](http://ubuntuforums.org/showthread.php?t=359310) will not work because typing aticonfig requires the installation of the xorg-driver-fglrx and as far as I know that doesn't work on my machine. I installed it manually using EnvyNG (manually because Envy was unable to do it automatically) and that screwed up the machine big time.
Also I think it's a rather drastic sollution since my card works just fine pas the Login screen.  The trouble here is that my login is always in low graphics mode.  It seems that pas the login, GDM reads the xorg.conf file and all is well.

---

### Post by kracheck on 2008-11-15
The suggested solution in [http://ubuntuforums.org/showthread.p...e+login+screen](http://ubuntuforums.org/showthread.p...e+login+screen) doesn't help either

---

### Post by kracheck on 2008-11-15
For the record, the sollution I was thinking of using XrandR didn't work either.

#! /bin/sh
# /etc/init.d/CustResolution
xrandr --size 1024x768

chmod 777 (Make it executable and drop it in /etc/init.d)
Make a symbolic link to cause the script to be executed when the system boots using :
sudo update-rc.d CustResolution defaults.

The above doesn't work

---

### Post by kracheck on 2008-11-15
Since the resolution is wrong it's almost impossible to read the user input at login (username).  The only solution I could come up with for that was :
sudo cp /usr/share/gdm/themes/Human/Human.xml /usr/share/gdm/themes/Human/Human.xml.bak
sudo nano /usr/share/gdm/themes/Human/Human.xml
change every entry "font="Sans 11" and change it to "Sans 20"

That at least made the userinput readable but didn't solve the initial problem.

---

### Post by kracheck on 2008-11-27
While browsing for a solution to the stated problem I came across this website :
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

A few commands from that site and the problem was solved :
1. Back-up
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
2.Forcing a preferred mode
"If the preferred mode reported by your monitor isn't the one you want by default, or if there is no preferred mode and the driver does not choose the right one, you might want to force another mode on an output."

In my case I obtained the modeline by typing at the prompt : 
gtf 1024 768 60 (that is screen resolution 1024x768 at 60hz)

I pasted the outcome in my xorg.conf in the section "Monitor"
Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795 $
and also added       
Option "PreferredMode" "1024x768_60.00" to that section obtaining something like this :

Section "Monitor"
        Identifier      "Configured Monitor"
        Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795 $
        Option "PreferredMode" "1024x768_60.00"
EndSection



3.Reboot and off you go :-)

---

