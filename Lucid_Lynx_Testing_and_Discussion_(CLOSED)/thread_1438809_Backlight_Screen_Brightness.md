---
title: "Backlight/ Screen Brightness"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Chris_cur on 2010-03-25
Is any one working on this issue or is it not happening enough for the developers and community to really care about? I have seen it a few times but no [Solved] tags yet. and none of the advice has fixed my issues.

9.04 - I cannot change screen brightness but it is bright enough to see.
9.10 - I could not change screen brightness, very dim, can only see if I put my nose 2 inches from screen.
10.04- cannot change brightness, not as dim as in 9.10.

I am running an Asus UX50V. Which has two graphics cards. Installing the Nvidia drivers do not help, I have more issues than brightness if I install.

> 00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: nVidia Corporation Device 06f1 (rev a1)


I have ran into some supposed fixes
 	Code:
 	sudo echo 100 > /proc/acpi/video/VGA/LCDD/brightness 
 is supposed to work... 

also
 	Code:
 	sudo gedit  /proc/acpi/video/VGA/LCDD/brightness 
 then when the file comes out you should see something like:
 	Quote:
 	 	 		 			 				levels:  0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
current: 0 			 		 	 	 
you should be able to change the current value.

Unfortunately I have two VGA files, VGA and VGA1. VGA's brightness is 0,  VGA1's brightness is 15.  
I keep getting permission denied to edit the file as well... even though  I go in as root...

I have also tried the brightness buttons to add to the panel = nothing.
My keyboard's hotkeys Fn+F5,6, do not work. 

Gnome Power management does not register a change between battery and AC power. Changing the brightness through GPM doesnt work.

Anything else? This is a deal breaker for me.

---

### Post by Arla on 2010-03-25
Not sure if this will help or not, for my Lenovo Y450 the command is

"
This is the only way I have been able to get the brightness to change. 

 

sudo setpci -s 00:02.0 F4.B="20" The 20 means it's at 20% brightness. It goes from 1-FF, FF being 100% brightness. Also, make sure you remove the quotes. This is with 64-bit 9.10."

This was copied from the Lenovo forums, the part about 20 meaning 20% brightness is actually wrong, it's hex, so 20 is really 12.5% (approx) FF is the brightest.

Not sure where the value(s) for setpci came from I may try to research it soon just because I would like to be able to change it without running a command.

Out of interest, are you dual booting, and if not, are you booting with power? My Lenovo is always darker if I boot without power plugged in, and if I boot into windows and it changes my brightness, that change persists to when I boot into Ubuntu.

---

### Post by Chris_cur on 2010-03-25
Thank you Arla for your reply.

I have not tried your suggestion yet because I completely stumbled across my own fix.

I am booting solely with Ubuntu. This happens with AC & Battery.

My fix to this came from [http://blog.manki.in/2008/01/more-linux-fun-screen-brightness.html](http://blog.manki.in/2008/01/more-linux-fun-screen-brightness.html)

This fix was WAAAY over my head! So I have rigged my backlighting up thus far by..
-Navigate to /sys/class/backlight/acpi_video0
-There should be 3 text files: "actual_brightness", "brightness" & "max_brightness"
-Open "actual_brightness with gedit, enter your password when prompted
Chances are the numbers are: 0 if too dim or 15 if too bright
-Set the number to 10
-Save. Your brightness should immediately change.

If you are more savy than I am with your hacking and programming the above link should help you a little more in-depth.

I am about to restart to ensure this is an actual fix.

EDIT: Upon restart, setting still works. I will keep updating this as I work to make it a little easier.

P.S. This is my first fix, I feel so happy!

---

### Post by Arla on 2010-03-25
Hmm, will have to take a look, because in theory that's what (or at least I thought) gnome-power-manager was supposed to do with relevant function keys, and while it works for me, in that the display of brightness changes, the actual brightness stays exactly the same.

However the website gives me some ideas for how to make mine automatic (mostly I don't change it, so don't really care, but it would be nice if I COULD change it).

---

### Post by lidex on 2010-03-25
There are some utilities in the repos that may be of service. Try a search in synaptic for "laptop" or "backlight" ;)

---

### Post by Chris_cur on 2010-03-25
> **lidex said:**
> There are some utilities in the repos that may be of service. Try a search in synaptic for "laptop" or "backlight" ;)
What where you thinking of? xbacklight?  I install xbacklight from synaptic and then I can't find it...:-k

Also, my fix was temp. Backlight somehow reset back to 0.

---

