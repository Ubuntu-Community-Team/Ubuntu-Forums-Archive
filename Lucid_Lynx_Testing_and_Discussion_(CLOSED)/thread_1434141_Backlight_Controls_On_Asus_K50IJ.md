---
title: "Backlight Controls On Asus K50IJ"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hyperion285 on 2010-03-19
They where working fine in 9.10, but in 10.04b1 no control. Tried using gnome brightness applet and gnome power controls but nothing.

btw These laptops use a intel 4500 gpu, if that helps.

---

### Post by KlavKalashj on 2010-03-20
> **hyperion285 said:**
> They where working fine in 9.10, but in 10.04b1 no control. Tried using gnome brightness applet and gnome power controls but nothing.

btw These laptops use a intel 4500 gpu, if that helps.

Same thing on my Asus UL30a. Same gpu.

The hotkeys (fn+f5/f6) are recognized, and sometimes actually changes brightness, but it's very random in which direction or if even at all. This is the only issue I have with Lucid, I hope it will get fixed. I would file a bug report if it weren't so difficult!

---

### Post by pexi on 2010-03-21
In my asus UL30A isn't working too, neither with kubuntu works.

---

### Post by keithy on 2010-03-21
Nor on acer aspire 3935. didnt work under karmic either :(

---

### Post by pexi on 2010-03-21
I have found the bug report about our problem (ASUS laptops).

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429942](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429942)

---

### Post by KlavKalashj on 2010-03-21
> **pexi said:**
> I have found the bug report about our problem (ASUS laptops).

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429942](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429942)

I also posted a bug, today: [https://bugs.launchpad.net/bugs/543294](https://bugs.launchpad.net/bugs/543294) 

Should we mark this as a duplicate?

---

### Post by priegog on 2010-03-21
Ahh, I've got an Asus K50IN and can't even get it to boot... off to troubleshooting.

---

### Post by Chris_cur on 2010-03-24
I have had backlight issues on my Asus UX50 all along.
9.04- cannot change brightness, but it is bright enough to see
9.10- Cannot change brightness, dim as all get up
10.04- cannot change brightness, not as dim as in 9.10.

I have ran into some supposed fixes
```
sudo echo 100 > /proc/acpi/video/VGA/LCDD/brightness
``` is supposed to work... your file path may not be exactly like that so check yours out before you try the code.

also
```
sudo gedit  /proc/acpi/video/VGA/LCDD/brightness
``` then when the file comes out you should see something like:
> 
levels:  0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
current: 0

you should be able to change the current value.

Unfortunately I have two VGA files, VGA and VGA1. VGA's brightness is 0, VGA1's brightness is 15.  
I keep getting permission denied to edit the file as well... even though I go in as root...

Maybe this can help you guys. If you come across a good fix, let me know please. I am not too happy about this issue and no one else has been able to through anything at me, other than booting without acpi..

---

### Post by Chris_cur on 2010-03-25
Hey guys, I hope your backlight issues have been fixed by now. In addition to what my previous post says try out the fix I just figured out.  It does not address the hotkeys, I am still working on that.

-Navigate to /sys/class/backlight/acpi_video0
-There should be 3 text files: "actual_brightness", "brightness" &  "max_brightness"
-Open "actual_brightness with gedit, enter your password when prompted
[SIZE=2]*Chances are the numbers are: 0 if too dim or 15 if too bright*[/SIZE]
-Set the number to 10
-Save. Your brightness should immediately change.

I have started another thread and as I discover some fixes I will update that thread, hop on over to it if your issues continue or if you are just interested.
[http://ubuntuforums.org/showthread.php?t=1438809](http://ubuntuforums.org/showthread.php?t=1438809)

---

### Post by hyperion285 on 2010-04-08
Okay all fixed, adding acpi_backlight=vendor to the kernel options fixed it, now it works just liked in 9.10.

Hope this helps.

---

### Post by TheCowGod on 2010-04-18
This is happening on my Asus P50IJ too. None of the fixes here seemed to do anything.

When I boot the function keys for volume, etc work. However as soon as I press one of the keys to lower/raise the brightness the notification shows once, then none of my function keys work anymore. If I wait for a while it will show the notification again for the next key press, but with a very long (30 seconds?) lag. Nothing seems to happen with the volume or screen brightness.
This is caused by the brightness hotkeys since it only happens after I try to change the brightness. The brightness control applet does nothing either. It will start but when I try to click on the slider it just disappears. If I watch /sys/class/backlight/acpi_video0/actual_brightness the number in there goes down each time the lagged notification pops up but the brightness still doesnt change.

Also if I use xrandr --set BACKLIGHT it doesn't give me an error, but nothing changes.

---

