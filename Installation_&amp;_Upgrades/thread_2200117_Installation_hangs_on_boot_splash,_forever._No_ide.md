---
title: "Installation hangs on boot splash, forever. No idea how to fix/debug."
date: 2014-01-17
forum: Installation &amp; Upgrades
---

### Post by neph01 on 2014-01-17
[COLOR=#000000][FONT=verdana]Now I wouldn't normally call myself a noob, exactly. I've been using linux for years, I know my way around a terminal. I've installed various distributions numerous times in the past 5 years, and never had any problems like this.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I'm completely stumped.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I recently rebuilt my desktop. I want to install a fresh installation of Ubuntu on one of my hard drives. I have been trying to install either Ubuntu 13.10 (specifically 'ubuntu-13.10-desktop-amd64.iso') or, preferably, Ubuntu Gnome 13.10 ('ubuntu-gnome-13.10-desktop-amd64.iso'). I have tried both of those .iso's each as both live DVDs burnt to disk and as live USB's flashed using the program [LiLi]("http://www.linuxliveusb.com/")[1] .[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]In all cases (4 methods each tried numerous times in the last three days), across all forms of installation, I get the GRUB like screen asking if I want to Try Ubuntu before installing, install now, etc etc.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I select install, and then the boot splash screen comes up...and stays there. Forever. Well, until I hard reboot using the power button.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Screenshots:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][http://i.imgur.com/a6ko4pV.jpg](http://i.imgur.com/a6ko4pV.jpg)[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][http://imgur.com/q6mW9OI]("http://i.imgur.com/q6mW9OI.jpg")[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I can't imagine it's a problem with the distribution, since I've tried two separate ones. And I can't imagine it's a problem with the media, since I've tried multiple flash drives and two CDs. Is this something with my motherboard? Or...idk. I'm just stumped, and having trouble finding anything to help me online.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Any and all help would be much appreciated.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]**tl;dr: Install hangs at boot splash, see screenshots above. What do?**[/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-01-17
Welcome. When you get to the 'Try Ubuntu' 'Install Ubuntu' screen, have you tried hitting 'Try Ubuntu' and can you get to a desktop?

Either way, when at that screen, hit F6 and choose 'nomodeset' from the popup menu. Proceed.

---

### Post by neph01 on 2014-01-19
Alright, so I thought you meant press F6 in the grub screen, but that doesn't do anything. None of the Fx keys do anything there. During the boot splash screen, pressing F6 does bring up a sort of output console, but there's no popup menu of any sort, and no where to input 'nomodeset'. It shows a log of what's going on during the boot, and here's what it looks like when it freezes:
[http://i.imgur.com/wjMCupg.jpg](http://i.imgur.com/wjMCupg.jpg)

Any ideas?

---

### Post by Bucky Ball on 2014-01-20
I meant when you boot from the install CD and get to the screen that says 'Try Ubuntu' 'Install Ubuntu' ...

---

