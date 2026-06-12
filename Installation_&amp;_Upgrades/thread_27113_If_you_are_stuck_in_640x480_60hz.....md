---
title: "If you are stuck in 640x480 60hz...."
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by mstrymn on 2005-04-14
This must be a gap in auto-detection for monitors.  I had this problem and just compared Ubuntu's xorg.conf to my Slax xorg.conf, the monitor refresh rates and specs aren't defined by default.  I found a temporary fix, it should work but don't blame me if your monitor explodes (mine is like a generic CRT, be wary of these specs LCD users).....

If you feel like being safe, I would reccomend searching for your monitor model's specs on google or downloading Slax live cd and checking it's generated xorg.conf and using their monitor specs.



1- Open root terminal and type "sudo gedit"

2- Find xorg.conf file in /ect/x11 (or open terminal and 'sudo gedit /etc/X11/xorg.conf'), open and find (monitor model may vary):
------------------------------------------------------------------
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection
-------------------------------------------------------------------

3- add this (you can put the correct numbers for your monitor, these numbers are from a generic CRT monitor and should work):
-------------------------------------------------------------------
HorizSync 31.5 - 150.0
VertRefresh 40-75
-------------------------------------------------------------------

so it looks like this:
-------------------------------------------------------------------
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 31.5 - 150.0
VertRefresh 40-75
EndSection
-------------------------------------------------------------------

4- Save and reboot. You should now have more options in 
System->Preferences->Screen Resolutions.

5- *Hopefully* ENJOY!

---

### Post by wfx on 2005-04-15
> ...4- Save and reboot. You shoul... 
or logout Gnome and hit [ctrl]+[alt]+[backspace]

---

### Post by murrowman789 on 2005-04-16
i tried doing everything you said...but i couldnt edit the xorg.conf file because at the top it said read-only, so i tried to edit permissions of the file and of the user and still nothing happened...

what do i do now?

---

### Post by gunnyman on 2005-04-16
sudo gedit /etc/X11/xorg.conf

---

### Post by murrowman789 on 2005-04-16
i try that and it opens a new text doc...

eh?

---

### Post by ssam on 2005-04-16
if it opens a new text document that means that you don't already have to file.

are you running warty or hoary? warty has the X config file in a slightly diferrent place because it use XFree86 rather than the newer Xorg

---

### Post by murrowman789 on 2005-04-16
i am running hoary

and i am positive that the xorg.conf file is there...i can see it just not edit it....thats why it is read only...

---

### Post by murrowman789 on 2005-04-16
if i could get write permisions i could do it...but i have tried a lot of stuff in the user panel and nothing happens...

---

### Post by donar73 on 2005-04-16
[QUOTE=murrowman789]if i could get write permisions i could do it...but i have tried a lot of stuff in the user panel and nothing happens...[/QUOTE]
 Try it this way:
1. open a Terminal
2. type *sudo nautilus* and enter your user-pw when prompted -> Nautilus will open in root-mode
3. navigate to /etc/X11
4. double-click on xorg.conf -> it will open in Gedit in root-mode and you can apply your changes

---

### Post by murrowman789 on 2005-04-16
thanks..that worked perfect...now all i need is the software cd from the isp part of att and i can get online with llinux....thanks again...

---

