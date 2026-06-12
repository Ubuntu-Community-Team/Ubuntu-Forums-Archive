---
title: "need ATI xorg.conf file from edgy (clean install file perferred)"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by hardyn on 2007-02-05
my buddie tried to install the ATI proprietory driver before checking board support, oops ;)

he is green but learing fast, and i am in no position (geograhically) to help him out right now, he did not back up the original file and is having trouble reassembling a xorg.conf file for the "ati" driver...

does anybody have a originalish xorg.conf file for "ati"
could you email it to me?

thanks for the help.

---

### Post by pay on 2007-02-06
Can't he just change ```
Section "Device"
    Driver "fglrx" 
``` to "ati"?

---

### Post by aberry5555 on 2007-02-06
it is fairly easy to do as the ati driver comes with a configuration tool, I think if he types in something like "sudo aticonfig --initial" it should re-write the xorg.conf file properly.

And also make sure he uses the "fglrx" driver not the "ATI" driver as this driver definately does NOT work well in Ubuntu! try the first option as this should replace the ATI with fglrx (accelerated graphics) and, once he's restarted the X server, it should be OK.

---

