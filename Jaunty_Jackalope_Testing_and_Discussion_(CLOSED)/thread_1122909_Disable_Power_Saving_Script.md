---
title: "Disable Power Saving Script"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by turniphead on 2009-04-11
I'm having issues with xbmc not disabling the screensaver and powersaving options. I have a script to turn off the screensaver

```

#!/bin/sh

#Disable Screensaver
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool FALSE

# Start XBMC
xbmc

# Enable ScreenSaver when XBMC closes
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool TRUE

```

Could someone show me what to add to disable power saving before xbmc is launched and re-enable it afterwards please.

Many thanks in advance.

---

### Post by FuturePilot on 2009-04-11
I've run into this problem with some games, and I've found a reliable way to deal with this. There's a command called 'gnome-screensaver-command'. One of the options to this command is
> -i, --inhibit
              Inhibit  the  screensaver  from activating. Command blocks while
              inhibit is active.


Not only will this disable the screensaver, it will also disable powersaving such as hibernate/suspend.

Here's a way to make a script with this.
```
#!/bin/bash
gnome-screensaver-command -i &
program-command-goes-here && killall -15 gnome-screensaver-command ;
exit

```

What this does is run the command gnome-screensaver-command -i to disable the screensaver and powersaving, then runs your program. After your program exits, it terminates the gnome-screensaver-command command so that your screensaver and powersaving will function again.

---

### Post by turniphead on 2009-04-12
Thanks very much, I'll give it a try.

---

