---
title: "Turning off DVD to save battery?"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-09-24
Is there an easy way to turn off/on the DVD drive to save battery? I am not sure if it's worth doing but I remember doing that in Windows and it would give a few extra minutes of battery life.

---

### Post by ode on 2009-09-24
When I have used [Powertop]("http://www.lesswatts.org/projects/powertop/") in the past it has used the command ```
hal-disable-polling --device /dev/cdrom
```to turn off the DVD.

I'm not sure how to turn it back on. Maybe restart the hal service.

---

### Post by executorvs on 2009-09-25
in windows doing this on my acer timeline buys me a little over 1.5 hours of extra life. in ubuntu I get about 4-4.5 hours compared to my nearly 8 in windows. This should be a good thing to work into power management as well.

If I could do this and adjust my screen brightness(requires terminal currently) I'm sure I would get at least 6 hours of up time on my machine.

---

### Post by ode on 2009-09-25
You don't need to use the terminal to adjust screen brightness.
Right click on the panel, click 'Add to Panel' and choose the 'Brightness Applet' from the menu.

System-->Preferences-->Power Management
You can set options in here to dim brightness when on battery power.

---

### Post by executorvs on 2009-09-25
> **ode said:**
> You don't need to use the terminal to adjust screen brightness.

Actually I do. Unless I reset some of the xrandr settings manually, the applet of which you speak (which shouldn't be needed anyway as jaunty recognises my brightness Fn keys and associates them correctly) won't do anything. This wouldn't be an issue if after making these changes persistent they would in fact be persistent. 

it's a bug you see. not a lack of knowledge of how the various screen brightness functions work.

I'm really not awake enough to be on the internet.

---

