---
title: "my desktop is...gone"
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mephist0pheles on 2009-09-27
so when i upgraded to karmic koala (alpha) and restarted my comp, something rather dreadful happened. it said something about my filesystem being corrupted, doing some sort of manual fsck or something, which froze and didn't really do anything, i don't think. 

now, my desktop is gone. it's completely blank. as in, it's not there...at all. if i move a minimized window around on it, it moves with slow, choppy movements. 

help, please :confused::sad:

---

### Post by ibuclaw on 2009-09-27
Karmic is still an alpha system, and so it is - as always - advised that you don't use it on a production system.


Now, when you say slow/choppy, do you mean just the overall performance?
What graphics card/drivers are you using?
Open a terminal and type in:
```
ls Desktop
```
and post the output.

Check the Hardware Drivers app and ensure that you are on the most recent version for Karmic.

Regards
Iain

---

### Post by mephist0pheles on 2009-09-27
mephisto@ubuntu:~$ ls Desktop
ePSXe                         meow       Python, etc.
gnome-system-monitor.desktop  Music      Terry Goodkind - The Sword of Truth
Incomplete                    My eBooks  The Erenion Project
Jeff Lindsay - Dexter Series  Pictures   ubuntupocketguide-v1-1.pdf
LanguageTool-0.9.9.oxt        PSX Games

^there's the output for ls Desktop

by slow/choppy, i mean anything that moves over the desktop that's not there moves...unnaturally. i never had any problems with it before, so it's not a graphics card problem, i don't think.

---

### Post by lidex on 2009-09-27
Try rebooting into recovery mode. Just choose the option from boot menu. It will walk you through a few screens then give options for creating a new xorg.conf. Good place to start.

---

### Post by Tompalaz on 2009-09-27
You might want to try to remove your .gnome2 folder. Your settings won't stay but you've got a working desktop (maybe)

---

### Post by inportb on 2009-09-27
> **Tompalaz said:**
> You might want to try to remove your .gnome2 folder. Your settings won't stay but you've got a working desktop (maybe)

Or simply rename it, if you want to be able to get it back.

---

### Post by NormanFLinux on 2009-09-27
Ah... GDM is gone. Without GDM, you get a black desktop!

---

### Post by NormanFLinux on 2009-09-27
Do NOT install Karmic on a stable system! The only exception are upgrades in advance of an official release to update say GNOME or KDE to the latest stable version through backports.

---

### Post by lidex on 2009-09-27
These threads may help for GDM
[http://ubuntuforums.org/showthread.php?t=1253012]("http://ubuntuforums.org/showthread.php?t=1253012")
[http://ubuntuforums.org/showthread.php?t=1213785]("http://ubuntuforums.org/showthread.php?t=1213785")
[http://ubuntuforums.org/showthread.php?t=1259121]("http://ubuntuforums.org/showthread.php?t=1259121")

---

### Post by inportb on 2009-09-27
> **NormanFLinux said:**
> Ah... GDM is gone. Without GDM, you get a black desktop!

Um... no.
What would GDM have to do with the window manager?

---

### Post by nukie77 on 2009-10-21
I have a similar problem.  When i boot from the 9.10 beta live CD or from my 9.10 beta install, I get the same black background/desktop.  

The strange thing is anything on the desktop is still there, you just can't see it.  If you know where the file is on the desktop, you can even double click on it to run the file.  Did anyone discover how to fix this?

---

### Post by lidex on 2009-10-21
Guys,
Seems you're not alone. Read this thread - it points to some workarounds:
[http://ubuntuforums.org/showthread.php?t=1278410]("http://ubuntuforums.org/showthread.php?t=1278410")

---

