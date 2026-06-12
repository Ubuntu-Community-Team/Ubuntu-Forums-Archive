---
title: "Checking Battery State"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by mdhollis on 2011-11-11
I just installed 11.10 on a second computer that I have and I get this error when the computer is booting.  I updated the computer, installed and reinstalled the nvidia drivers(current) with no success.  I saw this error during the developmental stages and usually solved it by reinstalling the video drivers.  I also tried:
```
sudo service lightdm start
```
but lightdm will not start it just goes back to checking battery state:confused:

---

### Post by mdhollis on 2011-11-12
Also sudo nvidia-xconfig returned this output:

using x configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: data incomplete in file /etc/X11/xorg.conf.

Device section "default device" must have driver line.

Backed up file '/etc/X11/xorg.conf' as /etc/X11/xorg.conf.backup

New X configuration file written to ' /etc/X11/xorg.conf'


Now it stalls at checking for unattended updates or something like that

---

### Post by mdhollis on 2011-11-14
After days of trying to re-install 11.10 and messing around in tty1, I used a beta 1 image I had of 11.10 from the developmental stages.  I updated the system and installed nvidia-current and I'm up and running.  I can't explain it but if anyone cares that's what I did....lol.

---

