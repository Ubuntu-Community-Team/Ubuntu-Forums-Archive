---
title: "[SOLVED] nvidia-settings do not save to X Config File"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Occam on 2008-10-28
Using the latest nvidia drivers (177.80) in Intrepid, and typing

```
gksudo nvidia-settings
```

then saving my settings, and clicking on Save to X Configuration File, the whole window simply closes without any sort of error dialog whatsoever. Upon reboot, my settings have been reverted (running dual monitor, so it goes back to a single monitor, with my second monitor being disabled).

Anyone else experiencing this issue? Thanks!

Occam

---

### Post by lunarcloud on 2008-10-28
have you hit apply settings first?

did you try the built-in monitor config tool (i know the nvidia one is nice, i use it on kubuntu here)?

---

### Post by dabl on 2008-10-28
After backing up the xorg.conf file that you have, you might want to run

```
sudo nvidia-xconfig
``` 

first, to write a new xorg.conf in nvidia style.  Then run your ```
gksudo nvidia-settings
``` and see if it is any happier to adjust the settings.

---

### Post by kaibob on 2008-10-28
I had the same problem with the older (~173) drivers. I tried both sudo nvidia-settings and gksudo nvidia-settings but neither worked. I also tried resetting the xorg configuration file and then reenabling the proprietary drivers and then ran nvidia-settings but no luck. I finally went back to 8.04. I hope someone has a fix for this as I'd like to upgrade.

BTW, I can't recall if I clicked apply settings first. This isn't necessary in 8.04.

---

### Post by Occam on 2008-10-28
> **zarquad said:**
> have you hit apply settings first?

did you try the built-in monitor config tool (i know the nvidia one is nice, i use it on kubuntu here)?

I did hit Apply Settings first.

I have heard about the built-in monitor config tool but haven't figured out where it is. Can you point me in the right direction? I'd love to give it a shot.

@dabl: I'll try your suggestion once I try the built-in monitor config tool. :) Thanks for your responses!

Occam

---

### Post by Occam on 2008-10-28
Good news!

I found the monitor screen resolution tool, but it only found one giant monitor, not two. And it was seen as "Unknown." So I decided to try out dabl's advice, and that did the trick! I can now logout and log back in with my nvidia settings.

Thanks so much!

Occam

---

### Post by dabl on 2008-10-28
> **Occam said:**
> Good news!

I found the monitor screen resolution tool, but it only found one giant monitor, not two. And it was seen as "Unknown." So I decided to try out dabl's advice, and that did the trick! I can now logout and log back in with my nvidia settings.

Thanks so much!

Occam

:cool:

OK, now please put a "SOLVED" in front of your original title, so other folks can get the benefit.   Thanks!   :)

---

### Post by finalkut on 2008-10-29
This technique solves the problem of not being able to save my xorg.conf file but x won't properly restart for me once I do get it to save.

Does anyone know if there are specific settings I just can't use (dual x for instance?)

---

### Post by finalkut on 2008-10-30
I did a system update last night and today it worked out.  thanks again dabl.

---

