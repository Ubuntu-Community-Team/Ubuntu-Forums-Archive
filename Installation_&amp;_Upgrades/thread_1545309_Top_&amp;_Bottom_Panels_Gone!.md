---
title: "Top &amp; Bottom Panels Gone!"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2010-08-03
Just did my updates (~95 megs worth) today on 32 bit Lucid, on a Dell P4 that was running 32 bit Lucid fine but a PC I haven't used in a couple weeks.

The update included the addition of Ubuntu, Linux 2.6.32-24 gereric

Reboot as instructed and all seemed fine. 
Then shutdown went into XP for a few minutes to check something on this dual boot Dell. Then reboot back into Lucid and all I get is the purple Lucid screen with No top or bottom panels! No taskbars, no clock, no trash, nothing but a purple screen.

Hit control/alt/delete to get PC to restart and the same thing happens. 
Only a purple screen with no icons or anything I can use the mouse with or right click on.

Tried going back to earlier settings listed than, Linux 2.6.32-24 gereric but the same thing happens, just a purple screen. Recovery mode doesn't help. It keeps saying I'm using the wrong password.....which I am not!

What happened? 
How can I get back to normal?

---

### Post by Darkness Des on 2010-08-03
When you get to that screen, press Alt+F2. In that box, type in
```
gnome-panel
```
and tell me if that works. If it does, then I'll get back to making it happen on startup

---

### Post by David Andersson on 2010-08-03
When it says password is wrong, can you see if the right keyboard layout is used then?

I recall once I got the purple screen and nothing more after login, like it was hanging, but after a minute or two the panels appeared. I don't remember how it was fixed. Have you waited a minute or more to see if it finally is logging in?

---

### Post by cybrsaylr on 2010-08-03
> **Darkness Des said:**
> When you get to that screen, press Alt+F2. In that box, type in
```
gnome-panel
```
and tell me if that works. If it does, then I'll get back to making it happen on startup

Did that and that 'Run Application' box just vanishes back to the purple screen after trying it a couple times.

---

### Post by cybrsaylr on 2010-08-03
> **David Andersson said:**
> 

I recall once I got the purple screen and nothing more after login, like it was hanging, but after a minute or two the panels appeared. 

That happened to me a couple times in the past also.
After a short time the panels came back, or they came back after a reboot.

This time they are not coming back.

---

### Post by cybrsaylr on 2010-08-03
When I press Alt+F1, the Applications Tab drops down:
Accessories
Games
Graphics
Internet
Office
Sound & Video
System Tools
Ubuntu Software Center

This is all that opens and they seem to function OK.

---

### Post by cybrsaylr on 2010-08-03
Used Google and found the solution with this link:

[Restore Ubuntu Panels Back To Their Default Settings]("http://helpforlinux.blogspot.com/2009/08/restore-ubuntu-panels-back-to-their.html")

> Open the Terminal. 
Once the Terminal window opens, enter the following command at the prompt:
gconftool - -recursive-unset /apps/panel 
(Remember: There should be no spaces between the two dashes before shutdown.)
Then enter the next command:
rm -rf ~/.gconf/apps/panel
And enter one more command:
pkill gnome-panel


Both top and bottom panels will appear (if missing) with their default settings.
Hope this helps. 

Put that code in terminal and it works like a charm.
Got the top & bottom panels back.

PS:
OMG!
Just booted up my laptop which hasn't been used in over a month. Love using my snappy i7 most of the time now. Update manager says ~200 MB of updates  are needed to be done on 64 bit Lucid! In the process of updating the laptop and hope the panels are not lost in the process again.


PPS:
Just completed those ~200 MB of updates and 64 bit Lucid looks fine after a couple reboots to test LL out.....knock on wood.

FWIW after using both 32 & 64 bit Lucid, IMHO 64 bit runs better. 32 bit Lucid has had a couple bugs in the past, like the one experienced in this OP.

---

### Post by cybrsaylr on 2010-08-05
Well it happened again earlier today.

Booted up and both top and bottom panels were missing on 32 bit Lucid. Only the purple screen was showing.

Put that code in terminal again from post #7 above and the panels were restored again. Don't have a clue what makes the panels vanish.

---

### Post by tron^qld on 2010-08-06
Hi cybrsaylr,

I am having the same issue but also having issues with accessing a terminal window when you don't have any menus to access.

I am able to get a *run application* box when I press Alt+F2, but not sure what the command is to get a terminal window with that...

---

### Post by cybrsaylr on 2010-08-06
tron^qld,

Alt+F1 

Will allow you to get to terminal.



I am having lots of problems with both top and bottom panels vanishing!
This happened a couple more times since my last post. 
When I reboot sometimes the panels are there but mostly now they are gone and I have to restore them by putting the code in Post #7 in terminal.

This only seems to happen with 32 bit Lucid on a desktop.
64 bit Lucid on my laptop has none of these issues.


PS: Just discovered this code is all you need to put in terminal to restore top and bottom panels:
> rm -rf ~/.gconf/apps/panel

pkill gnome-panel

Well it works for me.

---

### Post by cybrsaylr on 2010-08-06
Just want to point out this problem started on my desktop after the last update to:

Ubuntu, Linux 2.6.32-24 generic 

a couple days ago with 32 bit Lucid.


My laptop running 64 bit Lucid with 

Ubuntu, Linux 2.6.32-24 generic 

has no problems.....knock on wood.

---

### Post by tron^qld on 2010-08-07
Nuh seems that I can't get the ALT+F1 to work to get a terminal...

Getting a few other errors as I boot up as well, particularly one stating that Naultius (sp?) can't create or access my home folder...

So I am thinking that it is something a bit more serious than just the Panels disappearing...

Think I might have to do a fresh install, (lucky that I did a seperate partition for the OS and one for the home folder)

---

### Post by cybrsaylr on 2010-08-08
> **tron^qld said:**
> Nuh seems that I can't get the ALT+F1 to work to get a terminal...
Doing that is even buggy.
Sometimes it works great, other times you have to hit ALT + F1 a couple times to get it to work.


> **tron^qld said:**
> Think I might have to do a fresh install, (lucky that I did a seperate partition for the OS and one for the home folder)

Heard about this. It sounds like a good idea.
How is the best way to do this and set this up?

---

### Post by cybrsaylr on 2010-08-10
Well this bug is still happening on this extra PC.

Booted up yesterday and top and bottom panels appeared as they should.
Boot up today and NO top and bottom panels!

Put this in terminal and both panels were restored:
> rm -rf ~/.gconf/apps/panel

pkill gnome-panel

---

