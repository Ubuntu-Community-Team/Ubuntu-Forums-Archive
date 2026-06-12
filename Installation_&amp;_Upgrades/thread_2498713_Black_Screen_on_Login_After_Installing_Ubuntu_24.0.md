---
title: "Black Screen on Login After Installing Ubuntu 24.04 - nvidia"
date: 2024-06-25
forum: Installation &amp; Upgrades
---

### Post by alessio-pointnet on 2024-06-25
[COLOR=#0C0D0E][FONT=-apple-system]I recently installed Ubuntu 24.04 on my system and performed all the available updates. However, I’m encountering a frustrating issue every time I reboot. When I reach the login screen, my primary monitor goes black, and I have to log in blindly by entering my password without seeing anything, I can only see the cursor of my mouse.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I have a projector connected to my system, and I've discovered that if I turn on the projector, the login screen appears on it. This means the login screen is not showing on my main monitor but only on the projector if it’s powered on.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Here’s what I’ve tried so far:[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Logging in blindly (entering my password without seeing the login screen), after which my main monitor starts working normally. Turning on the projector, logging in using the login screen displayed on the projector, and then turning the projector off. I have also gone into the display settings and set my main monitor as the primary display while disabling the projector, but the issue persists.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Any help or suggestions on how to resolve this would be greatly appreciated![/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I have a 3070 TI card, if may help.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Thanks in advance.[/FONT][/COLOR]

---

### Post by makem2 on 2024-07-03
> **alessio-pointnet said:**
> [COLOR=#0C0D0E][FONT=-apple-system]I recently installed Ubuntu 24.04 on my system and performed all the available updates. However, I&#8217;m encountering a frustrating issue every time I reboot. When I reach the login screen, my primary monitor goes black, and I have to log in blindly by entering my password without seeing anything, I can only see the cursor of my mouse.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I have a projector connected to my system, and I've discovered that if I turn on the projector, the login screen appears on it. This means the login screen is not showing on my main monitor but only on the projector if it&#8217;s powered on.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Here&#8217;s what I&#8217;ve tried so far:[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Logging in blindly (entering my password without seeing the login screen), after which my main monitor starts working normally. Turning on the projector, logging in using the login screen displayed on the projector, and then turning the projector off. I have also gone into the display settings and set my main monitor as the primary display while disabling the projector, but the issue persists.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Any help or suggestions on how to resolve this would be greatly appreciated![/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I have a 3070 TI card, if may help.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Thanks in advance.[/FONT][/COLOR]

have you tried:

```

sudo nvidia-settings

```

You can swap the screen positions there.

I used to have a problem with my dual screen desktop always being on the left and Ubuntu didn't want to keep it on the right after a reboot. I saved the X configuration to /etc/X11/xorg.conf. To do this I had the change the permissions to that file to give me access. That worked for a long while.

When I upgraded to 24.04 the file permissions went back to root but I can still save. The only time I get a problem now is if I turn off the monitors to save the screens while the computer is doing something I started and can return to later. When I go back the screens are being mirrored and I have to use 'Display' setting to restore the correct settings. 

I remember some while ago I had to update Nvidia drivers, are your the correct ones and up to date? I use:

[https://www.nvidia.com/en-gb/drivers/](https://www.nvidia.com/en-gb/drivers/)

Your GFX card is there.

Current card:

```

nvidia-smi

```

---

