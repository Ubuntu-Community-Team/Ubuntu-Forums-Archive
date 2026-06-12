---
title: "Lost gfx mode on upgrade to Lucid"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Elwro on 2010-05-10
I upgraded to Lucid and the gfx mode 1280x1024 disappeared. The computer starts in 1024x768. xrandr displays a list of modes which even includes 1360x768, which is clearly wrong for my monitor, but does not display the useful mode 1280x1024. 

To use the computer, basing on the output of "gtf 1280 1024 60" I wrote this script, which I always run on startup:

```

#!/bin/bash
xrandr --newmode 1280x1024 108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
xrandr --addmode VGA1 1280x1024
xrandr --output VGA1 --mode 1280x1024

```

I have no idea regarding the cause of this error. But more importantly, I'd like to make the changes persistent! How do I do that? I found some advice regarding editing xorg.conf but I won't do that, since my xorg.conf is clearly a dummy file (with lines such as "Monitor: Configured monitor" and so on) and the computer worked perfectly with it on karmic.

---

### Post by Elwro on 2010-05-25
I'm very sorry for bumping this, but I'm quite upset about having to run this all the time, too... ;-)

---

### Post by kansasnoob on 2010-05-25
I prefer this method:

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

If you also need to change the login screen this works:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

In fact the latter of the two links will change both the login screen and the display, but it won't work with auto-login.

You can do both without problems.

---

### Post by Elwro on 2010-05-25
Thank you very much, this worked. I did both those things, and I still had to set the resolution manually after restart, but the setting got saved and seems to be "permanent", if that's ever a good word in such contexts :-) Thanks again!

---

