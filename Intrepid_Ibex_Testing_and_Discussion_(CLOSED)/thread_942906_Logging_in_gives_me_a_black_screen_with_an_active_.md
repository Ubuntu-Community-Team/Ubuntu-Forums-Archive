---
title: "Logging in gives me a black screen with an active cursor. Dell C400 Laptop."
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by elcman on 2008-10-09
I searched a bit on this and couldn't find much... So here it goes.

I've upgraded from 8.04 to 8.10 on my laptop and upon reboot I got to the GDM screen without an issue. I noticed that the screen was in a lower color depth than usual. (There was banding on the logo, probably 16-bit color.)

After logging in, I got to a brown screen with a cursor. No bars at the top or bottom, but the cursor would be active. I'd hit the power button and it would freeze up with screen artifacts and then shut down after about a minute of processing.

I booted to the Failsafe terminal and spent some time doing "sudo apt-get update" "sudo apt-get upgrade" calls in order to get the latest updates and then reboot again to see if anything took. 

I've had very little change since then. The brown screen is now black. The cursor will freeze the cycling busy cursor, but the cursor can still be moved. Sometimes it will get past the busy cursor and go to a white cursor.

When the busy cursor is showing, CTRL-ALT-BACKSPACE does not work. When the arrow cursor is showing CTRL-ALT-BACKSPACE seems to work, but it doesn't show anything different on the screen or give any sound, then I can hit the power button and it will do a shutdown process (without showing anything on the screen).

This is a weird weird thing... :mad: And I can't seem to make it work. The window manager isn't loading properly but GDM is. After logging in, it seems to be halted on loading *something* but I don't know what that something is.

OH, and booting from the LiveCD (which I should have done first) brings me to nearly the same state as the first time I rebooted with the brown screen and cursor. Failsafe Gnome also doesn't work.

Any help with this? I've attached my Xorg log file.

---

### Post by christianvaldes on 2008-10-09
Did your computer work ok with Ubuntu 8.04?

---

### Post by elcman on 2008-10-09
> **christianvaldes said:**
> Did your computer work ok with Ubuntu 8.04?

Yes, 8.04 worked well right from installation. I'll be moving back to 8.04 if I can't figure this out.

Right now I'm getting fluxbox and putting that in place as a window manager to see if it has something to do with Gnome not working.

Strangely enough, when I hit different buttons, I can see the hard drive light coming on. It's almost like it is just not displaying things to the screen correctly, but my mouse cursor is there... and I can move it.

*shakes head* Seriously, I'm at a loss. 

Ha! Fluxbox loads. It's something to do with Gnome.

---

### Post by elcman on 2008-10-20
Still running into this even with getting the latest updates.

I'm wondering, though, if this has something to do with my external video being enabled. I found that Fluxbox loads, but I don't believe that spanning over multiple monitors is not part of the suite that's associated with it.

Does anyone have any insight into this or perhaps how I can disable it so it doesn't bring me to a blank brown screen with a cursor in the middle. (The cursor in the middle is a good indication that it knows my laptop's LCD is the primary monitor) enabling or disabled the additional video display doesn't change the condition of the laptop... I'm trying to disable this on start up so the computer doesn't default to this to see if it works.

Again, I can get to everything from Fluxbox and I've been using that as necessary... but, geez... I would really like to get back into Gnome.

---

