---
title: "Wrong screen resolution with U9.10 and Nvidia"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by Zeke1 on 2010-01-15
Just changed from Suse 10.3 to Ubuntu 9.10. The system asked if I want to install Nvidia prop driver (185) which I did. After reboot the screen resolution is 1024x768. I have an Acer AL1916 lcd with 1280x1024 60Hz resolution and a Nvidia GeForce 8400GS graphic card. Open the Nvidia X server settings but the correct 1280x1024 isn't in the list. Only widescreen settings like 1360x768, 1152x864 and so on.. 
Do anyone know how to get the system to understand what monitor is connected?

---

### Post by Zeke1 on 2010-01-16
Just tried to erase ubuntu 9.10 and replace it with opensuse 10.3. No problem there to find the correct 1280x1024 60Hz resolution for my screen. Worked like a charm. I suppose that I have to stick to good old suse 10.3 (the new opensuse 11.2 have the same problem as ubuntu 9.10).

---

### Post by Zeke1 on 2010-01-16
New opensuse 11.2 also works with 1280x1024 if you first download nvidias linuxdriver and then open sax2 (you have to search for it in the search-field because they have removed it from yast systemsettings).

The problem is that I like the way ubuntu looks and feels. I'd really want to give it a try. Formatting the harddrive was easy. Installing networking printers worked at first attempt.

Is there any backdoor into the graphical system in ubuntu so you can manually get the correct settings when ubuntu fails to auto-reqognize??

---

### Post by grubdude on 2010-01-16
I have been having the same issue for several weeks with my 9.10 only I am stuck with 800x600 resolution...It is like using a large cell phone display...No problems with other linux distros...

Since they went to automatic screen res config in this release there are problems and no longer an easy way to get into config via terminal to correct it...

I have asked numerous times for help but no responses.....I guess that it is back to Red Hat for me until someone tries to fix this instead of adding more bells and whistles...

---

### Post by Tourdog on 2010-01-16
System -Admin-Nvidia X server settings.   Follow the menu prompts and you probably can with about a dozen key-strokes set the 1280x1024 screen.  

The problem is this only sets it for that boot session.  Another boot means another dozen key-strokes to set it again.

I wish there was better news.   Even the "Terminal" and "Gedit" is only a probable % of success..................   and same with the "script" method.   :(

---

### Post by Zeke1 on 2010-01-17
Just stumbled upon a good guide.

[http://ubuntuforums.org/showthread.php?p=8302145](http://ubuntuforums.org/showthread.php?p=8302145)

It removed my nvidia-driver but after reinstall the driver I was able to choose the 1280x1024 resolution.
The only problem is that when trying to save the xorg.conf from inside the Nvidia software I got the error message  "cannot move the xorg.conf.backup". So I have to reinstall after every reboot.

I will try to manually (I'm not a good terminal man) edit the etc/X11/xorg.conf.

---

### Post by Zeke1 on 2010-01-17
Now it works.

I open a terminal window. Write "gksudo gedit" which brings up the editor after giving the root password.
Open the file /etc/X11/xorg.conf. In the section "Monitor" I change the values of Horizsync to 28.0 - 63.67 and VertRefresh to 43.0 - 60.0 (see thread 8302145 for more info).
In the section "Screen" I write a new row: 

Option "metamodes" "1280x1024 +0+0"

Hit the save button. Restart the computer and voila the screen resolution is 1280x1024.

Not an easy way but we can only hope that the developers of ubuntu and other linuxsystem remember that behind the nice automated procedures there must always be a simple way to change settings manually.

---

