---
title: "upgrade from dapper to edgy = broken 3d acceleration"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by overdose on 2006-10-28
OK, so I'm using an ATI Radeon 9800 Pro for which the proprietary drivers were working great under dapper, but since the upgrade to edgy, no dice! Direct rendering appears to have gone kaput.

When I run glxgears I get under 300 (It used to average about 1500 before) fps proceeded by the message:

[COLOR="Red"]Xlib:  extension "XFree86-DRI" missing on display ":0.0".[/COLOR]

The only things that have changed since the upgrade that might affect this that I could see was that the kernel version had changed and maybe the linux-restricted-modules that i had installed previously were broken.  So i installed the restricted modules matching the current kernel, blah blah.. still nothing.  Checked my xorg.conf, everything looks good.  /etc/modules is right.. I'm completely stumped..](*,)  Anybody have a similar problem?  

Any help would be greatly appreciated! Thanks.

---

### Post by Deus42 on 2006-10-28
I had this problem on my laptop as well. I had to add this at the end of my xorg.conf file:

Section "Extensions"
        Option           "Composite" "Disable"
EndSection


check your /var/log/Xorg.0.log file to see if the composite extension was disabling dri, but I think this is a common problem, so try adding that to your xorg.conf file. Just be sure to back the old one up first.

---

### Post by cptnapalm on 2006-10-28
If that doesn't work change the Disable to 0 (the number).

---

### Post by overdose on 2006-10-28
Awesome! Adding the: 

[COLOR="Red"]Section "Extensions"
Option "Composite" "Disable"
EndSection[/COLOR]

to the bottom of my xorg.conf did the trick.  although glxgears still reports under 300 fps.. but all my opengl rendered games and such seem to be  running at full capacity and at expected framerates..

Thanks for the info! :D

---

### Post by strawman on 2006-10-28
thanks for the info.  3d accel is working again:)

---

### Post by MrSiegal on 2006-10-28
This fixed opengl Direct Rendering for me, but 3d acceleration still won't be enabled.

---

