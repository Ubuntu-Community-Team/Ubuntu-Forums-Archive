---
title: "update of nvidia-driver breaks poweroff/shutdown again"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by alterpinguin on 2010-06-25
update of nvidia-driver breaks poweroff/shutdown again
-
like solved here:
> [http://ubuntuforums.org/showthread.php?t=1489432](http://ubuntuforums.org/showthread.php?t=1489432)

after the update of nvidia-driver last week, poweroff is not working any more. I tried different things, like nomodeset .. but it is the same like before, the computer shuts down and the last message on screen is "poweroff", there is the bad sound of harddisks spinning down but everything is still running. And after a Reset(-button-press) the harddisks dont spin up again. I need a coldboot with total poweroff.

Besides a few other packages, i suspect the sudden change of the nvidia-driver breaks it again. It was the update to
 nvidia-current-modaliases             195.36.24-0ubuntu1~10.04 
 nvidia-current                        195.36.24-0ubuntu1~10.04
-
there was no change of x11-server or kernel, only these packages. A few other were about pulseaudio, gstreamer...

Does anyone know how to easy select another graphics-driver at startup, like the noveau-driver or to select another nvidia-properiatry one like the nvidia-173..

---

### Post by dino99 on 2010-06-25
try with this ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by alterpinguin on 2010-06-25
i go for do a REBOOT instead of shutdown the computer.

This works with a default menu-entry in grub, that does the "halt" after the short timeout (of 10 seconds).

For this i put a 09_custom file into
/etc/grub.d

```

 cat /etc/grub.d/09_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry 'poweroff .. halt command ..' {
        halt
}

```

after a update-grub
now this is the first menu-entry and for the default of menu no.0
this will be executed and "halt" (=poweroff) the computer.

I need this, because sometimes i have some progs. running and want the computer shutdown after all is done, - now i do a reboot and the grub-menu will do the poweroff.

@dino99: thanks for Your suggestion, but i suspect there will still more changes and may brake this acpi-thing again. There are errors in parsing the acpi of my mainboard - errors, a lot more than with old ubuntu 9.04. I dont know if a possible bios-update may fix some things .... for the next time i will go with this grub-poweroff-workaround.

---

