---
title: "mouse, keyboard and video problem with lucid"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by a8jr on 2010-03-27
hi guys..
im using asus a8jr laptop, ati x2300 vga, intel x86. i dont know the brand of my usb mouse (wired) and keyboard is my laptop keyboard.

the problem will be about "focus" which i can't describe literally, but i hope you understand my problem after reading the explanation below (sorry for rather long)

after upgrading to lucid lynx my mouse and keyboard cannot change focus. that is if it is hovering on top of something, lets say the panel, then i could do anything with the panel, but i will not be able to click anything else (except what is on the panel) - this includes desktop, firefox, open office, amarok, nautilus... everything on the system.

so if i wanted to be able to click on, lets say firefox, i have to focus my pointer to the panel, click application -> open the firefox, hover over the firefox windows (i cant click on anything), unplug the mouse, then plug it in again. then i can do anything with the firefox, the menu, back forward refresh button, fill in passwords, drop down menus, etc... but i cant do anything with things on the panel.

so, to be able to click on things on other windows, i have to hover the pointer to the window i want to click on, unplug and plug in the mouse again - everytime.

the movement of the pointer is fine, the problem is that it cannot click on things. the touchpad is totally fine (does not have this problem), but will have the same problem if the usb mouse is plugged.

another clue is that if im doing administrative task, the ubuntu will indicate that it "cannot grab my mouse".

the keyboard follows the mouse. what i mean is that if the mouse focuses on the panel, then i can use alt+tab, for example. but after it maximizes one of the windows and the focus changes to that windows, i cant use alt+tab again. i have to hover the mouse to the maximized windows, unplug, plug in then i can use the alt+tab to minimize the windows. then the focus changed to the panels and i have to redo the unplug-plug in again and again.

about the video, since upgrading to kernel xxx-16 (forget the number in front) there is noise in my screen from the time ubuntu starts up. kernel xxx-17 (which i believe is the latest) also have the same problem.

kernel xxx-15 or before is fine with the video card, mouse and keyboard problems exist since the first lucid alpha upgrade.

the mouse, keyboard, video all work fine on windows 7 ultimate

suggestions?

thanks for your time reading the long explanation.

---

### Post by EPAstor on 2010-03-27
I'm having a very similar problem here - except I'd had no such problems until earlier today, when I ran an upgrade. I've been running Lucid since alpha 3, and upgrading as the updates came out - for me, this problem is a regression.

I can't quite describe the problem... the mouse and keyboard respond just fine, but the system will often fail to recognize that a mouse click or keyboard command was entered. Just as a8jr describes, the only problem seems to be when I'm attempting to change the window focus - at which point, I'm not allowed. When the problem is happening, I've managed to get an xev tester up - and attempting to click on the resulting window doesn't even issue a click event, though keypresses do register.

Running a failsafe GNOME session doesn't seem to help, either... the problem takes longer to set in, apparently, but still happens.

Any thoughts?

EDIT: A note - I'm running a COMPLETELY different system than a8jr. I'm running on a desktop system I built, with an ASUS motherboard, an nVidia GeForce 8800GT video card running the proprietary drivers, a wired Logitech keyboard, and a wireless Logitech mouse.

---

### Post by EPAstor on 2010-03-27
Even better - I just got my system to fail with xev as the window in focus. Same problems occurring as described above, but I can see that ButtonPressed and ButtonReleased events are getting through. Interestingly, these events even show up when I'm clicking on another window, trying to change the focus...

---

### Post by EPAstor on 2010-03-27
Weirder and weirder - the system DOES respond to Alt-F2, and I was able to open a second terminal window, but the result is an "incomplete change" of focus. Mouse movements and clicking events show up in the old terminal attached to the xev instance - but keyboard events don't, and result in input to the new terminal.

---

### Post by a8jr on 2010-03-27
@epastor: hmmm i dont understand that much, but indeed it should have something to do with the way ubuntu responses to clicking events. do you know how to put what the ubuntu are focusing on in the terminal? maybe we can see whats happening.

anyway i noticed that the program "mousetweaks" suddenly crashed and because i haven't update i cant put the log into launchpad. any ideas?

---

### Post by nurd6 on 2010-03-28
I have this same issue (Or at least one extremely similar) 

I am using an Ideazon USB Mouse and Keyboard. 

I have found that I can trick the focus into going where I want if I right click on the window that has mouse focus (to bring up context menu) and then left clicking on the window I want to have mouse focus. 

So if I want to move the mouse focus from my browser to the gnome panel I right click on the browser, wait for the context menu to load, then left click on the panel, the panel will then have focus for now.   I can then click on whatever item I want on the panel.  


This machine was upgraded from Karmic to Lucid yesterday. 
This issue occurs in both Gnome and KDE. 

Perhaps this will help someone determine the root cause.

---

### Post by a8jr on 2010-03-29
> **nurd6 said:**
> I have this same issue (Or at least one extremely similar) 

I am using an Ideazon USB Mouse and Keyboard. 

I have found that I can trick the focus into going where I want if I right click on the window that has mouse focus (to bring up context menu) and then left clicking on the window I want to have mouse focus. 

So if I want to move the mouse focus from my browser to the gnome panel I right click on the browser, wait for the context menu to load, then left click on the panel, the panel will then have focus for now.   I can then click on whatever item I want on the panel.  


This machine was upgraded from Karmic to Lucid yesterday. 
This issue occurs in both Gnome and KDE. 

Perhaps this will help someone determine the root cause.

owwww this works for me to. bring up the context menu then left click on what we want. hmmm but thats makes me feel the problem is even weirder... what is wrong then

---

### Post by a8jr on 2010-03-29
hey i have just found another interesting things...

this time i found out that if there two overlapping windows, with one maximized at the back and with the other one being in smaller size up at the front, we can use the context menu trick to change the focus but it will not "totally" change focus.

like if we have, for example, system monitor at the back and firefox with smaller window size at the front. first we put the focus on the firefox. then use the context menu trick and change the focus to the system monitor (at the back). what surprising is that the system monitor does NOT go up front (when we select a window it should overlap the unselected window). however i still can clicks on things on the system monitor although it is being blocked by the firefox window.

another interesting thing is that the window title for the system monitor does not light up (the firefox still light up) although the focus has changed. i do feel that there is a misconnection between the mouse, application and window manager.

it seems that the window manager could not "see" what the mouse is clicking so it does not change the focus. and moreover it seems that the application cannot "tell" what the mouse is doing on them to the window manager (to tell the window manager to change focus)

the bug is getting nastier for everytime i plug in my mouse and do any administration task it will almost always crashed (the root terminal, update manager, synaptics etc).

what i hated the most though, is that everytime the appreport (if i do not mistaken the name) gathers the crash report for my computer it says that my crash cannot be reported because I havent update some of the packages. the problem is is that the update manager and root terminal who is crashing... (so how could i ever report the problem?)

so far the only way for me to upgrade the packages is by unplugging my mouse and use the touchpad instead. (without having the problems at all, because the mouse is unplugged)

this make me sick...

---

### Post by a8jr on 2010-03-29
OH YEAHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH

the mouse problem solved after i disabled "assistive technologies"

system -> preferences -> assistive technologies -> uncheck the "enable assistive technologies"

i was wondering though this technologies should be assisting handicapped people to use the computer, but why it makes normal people handicapped???

---

### Post by artcarney on 2010-03-30
Unfortunately my assistive technologies is already unchecked.

I have an HP Pavilion dv6000 laptop.

I have found if I press the button on the trackpad that turns it off, then I cannot select hardly anything with my wireless mouse.

If I try to select a menu on the main panel the menu heading will light up but I cannot get the menu to drop down.

Two things that will work are Firefox and the calendar you get when you click on the clock.

I discovered that once this anomaly occurs I can hit ctrl-alt-f1 and go to a terminal. Then if I hit ctrl-alt-f7 I come back to Gnome (of course) but now my mouse works again. And the bonus is the trackpad is still turned off.

Go figure ...

---

### Post by nurd6 on 2010-03-30
Ah Ha!  Mine wasn't enabled there but under System -> Settings -> Startup Applications it was set to run Visual Assistance so it would turn on at startup even if it was disabled.. 

Thanks for the assistance!

---

### Post by nurd6 on 2010-04-05
As an odd note, every time this computer reboots this problem comes back until I go in and enable or disable Assistive Technologies (if it's enabled I have to disable it and vice versa)

It's a strange issue indeed.

---

