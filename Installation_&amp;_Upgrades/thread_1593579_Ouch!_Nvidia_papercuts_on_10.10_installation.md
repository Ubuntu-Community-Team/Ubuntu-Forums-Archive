---
title: "Ouch! Nvidia papercuts on 10.10 installation"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2010-10-11
After installing 10.10, I was notified of the availability of nvidia proprietary drivers (good). I activated the driver and rebooted. My 2nd screen wasn't immediately activated, so I did this:

```
gksudo nvidia-settings
```

I applied my settings and my second monitor was working the way I wanted it to.

At this point I wondered if the "save to xorg.conf" option was still necessary (and if so, would it work). I rebooted without saving to xorg.conf and my options weren't saved, so it was necessary after all. Again...
```
gksudo nvidia-settings
```

This time save settings to xorg.conf, but there's an error - failed to parse file. (Second papercut so far.)

I back up the original xorg.conf and manually create a new one using nvidia's suggestions. I reboot and I get a command prompt. Not good.

Again, edit xorg.conf and reboot.

This time I get into the desktop, but my second monitor is not working.

Again...
```
gksudo nvidia-settings
```
Repeat the whole process. Interesting, this time nvidia suggests DIFFERENT values for xorg.conf even though my selected settings are the same. (I've been saving nvidia's suggested values into backup files each time, so it's not my imagination.)

I overwrite xorg.conf with the new nvidia suggestions and reboot again.

Bottom line: I had to do this at least once more before everything was working. And I'm not even sure if the result is optimal. The suggested nvidia xorg.conf include input sections and other information that shouldn't be needed in xorg.conf. When I attempted to remove that, my 2nd monitor didn't work (probably for other reasons), but I don't have time for this long cycle of editing-rebooting-testing. Too many papercuts.

Just reporting my experience...

But I would like to know how my xorg.conf should look now (in general). Which sections are absolutely required and which ones can I get rid of? Why, if xorg.conf isn't really used in ubuntu now, do we have to do this to get the proprietary driver working?

---

### Post by DarkLilith on 2010-10-12
My b/f was having a similar problem I'm pretty sure, or at least it was definitely an issue with the Nvidia driver, because everything was working fine and then when he reset after installing the driver his resolution was all messed and we couldn't even get him logged in. We just ended up re-installing 10.10 and not touching the drivers until I could find a stable solution, as it seems to be working fine for him at the moment.

If anyone finds a solid solution for this, that would be awesome!

---

### Post by MountainX on 2010-10-12
> **DarkLilith said:**
> 
If anyone finds a solid solution for this, that would be awesome!

Mine is solid. I'm not having any problems. It was just a matter of enduring the papercuts. I was hoping for an "automagical" solution where I didn't have to do anything. So I was just complaining about the need to manually save xorg.conf and the hassle of having to do it more than once. 

But the fact is that the steps I went through (explained above) resulted in a very nicely working solution. I am not having any problems with stability or anything else.

---

### Post by DarkLilith on 2010-10-13
Awesome! I will have to try that and see how it works out for me.

---

