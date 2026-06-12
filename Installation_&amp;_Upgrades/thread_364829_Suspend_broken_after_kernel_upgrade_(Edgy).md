---
title: "Suspend broken after kernel upgrade (Edgy)"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by djails on 2007-02-18
Hi everyone,
I upgraded to the latest version of the kernel 2.6.17-11 this week end and recompiled the ATI driver (downloaded from the ATI website not the ubuntu repository one). I tried using the latest version of the ATI driver (8.33.6). The laptop can be suspended/hibernated but the screen remains pitch black (no LCD backlight, no blinking cursor, no nothing) when waking up. The keyboard is useless and restarting / turning off and on doesnt do anything, screen remains black, and nothing loads (no HDD activity) weird ... .The ONLY way to get the laptop to start again is to unplug the power cord, remove the battery for a couple of seconds and try again. And only then will it start. So I tried changing a couple of settings in /etc/default/acpi-support (including changing POST_VIDEO to true and then false) but no success. 

I downloaded the ATI driver that I used before the kernel upgrade (8.29.6). This time, the laptop wakes up from suspend/hibernate. This time, the backlight turns on, I can see a blinking cursor for a couple of seconds, and then I assume X-windows comes back, but that s it, the screen remains black just like when you use a blank screen saver. I can see some HDD activity and the keyboard is functional. I am sure that X-windows is running because I can run commands (like xterm) by pressing Alt-F2. I can also switch to text terminals and see the commands I ve ran with Alt-F2. I can also restart the Xwindows server with Ctrl-Alt-Backspace which fixes the black screen problem. I checked /var/log/X.log but there is no hint as to why the screen remains black when waking up.

All in all, when the laptop resumes from suspend/hibernate, everything goes back to normal (LCD backlight on, X-windows is there, keyboard is functional) except that the screen remains black.

Has anyone experienced this ? Any fixes ?

Thanks

---

### Post by djails on 2007-02-19
Update
The ugly hack I found:
I found that running ```
aticonfig --enable-monitor=lvds
``` enables the LCD screen again after a resume. So I created the file "/etc/acpi/resume.d/99-fglrx-fix" with 
```

#!/bin/sh
/usr/bin/aticonfig --enable-monitor=lvds

```

and resuming from hibernate/suspend now works !!:guitar:

---

