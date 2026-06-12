---
title: "NX not working after upgrade from 11.04 to 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by johnjanney on 2011-10-14
Two computers:

[LIST]
[*]Workstation running Ubuntu 11.10 (just upgraded from 11.04)
[*]Laptop running Ubuntu 11.10 (just upgraded from 11.04)
[/LIST]

I upgraded the laptop the day 11.10 came out. I upgraded the workstation today and installed the latest NVIDIA driver because I could not get my second monitor to work (Twin). Now it works fine (actually better than before under 11.04). 

I've been using NX to work remotely on my workstation with no problems (even after upgrading my laptop to 11.10). After upgrading my workstation to 11.10, I can log into it from my laptop but I only see the wallpaper and can't do anything. No keys work, no mouse clicks work, nothing. I can't see Docky, but I can sometimes see the labels of the icons I have stored on Docky, but nothing works if I click on the label (the icon doesn't show up). 

I use NX full screen, so when I logged in and only got the wallpaper, I had to actually hold my laptop's power button to reboot because I couldn't even log out of the NX session because I had no menus. I even selected to run NX in a window and it still went to full screen, causing me to hard-shutdown.

I read somewhere that perhaps it might work if you use the "Custom Settings" and enter "gnome-session-fallback" as the "custom command." I don't want to keep trying things and keep having to hard-shutdown every time it doesn't work. 

I really need to run NX for work. 

Any ideas?

*****UPDATE 1:*****
The "gnome-session-fallback" did NOT work. However, I set the window size to 800x600 and the session to use GNOME (like before the upgrade) and it worked, but it seems to offer me a different, very limited menu. I attached a screen shot so you can see. The new, very limited menu is the gray menu at the top of the NX window (File, Edit, View, Go, Bookmarks, Help). Very strange. 

How can I get the normal Unity or Classic menu back?

*****UPDATE 2:*****
I installed the "gnome-session-fallback" on the workstation, logged into it from my laptop and everything totally freaked out. It went full-screen on me, I would see menus like the Classic interface in 11.04, but most of the icons were broken and the system became unresponsive at times... eventually had to hard-shutdown :(

I read up on it and it seems the very very limited menu is the new GNOME 3 fallback interface. There is no menu to any applications, which means it's pretty much useless. Sad. Looks like I'll just be very very limited on what I can do remotely on my workstation, which really hurts my case for Ubuntu at work. This is very very bad. 

If anyone has any solutions, please post them. I'm at a loss. 

Thank you.

---

