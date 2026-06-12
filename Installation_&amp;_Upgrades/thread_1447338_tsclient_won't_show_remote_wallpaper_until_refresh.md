---
title: "tsclient won't show remote wallpaper until refresh"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by LINUX-JJ on 2010-04-05
Hi, again very new to Linux I am connecting to a Windows 7 PC and all is fine except that when I connect the remote wallpaper is not shown, but if I refresh the remote screen the wallpaper is shown.

I suspect it is a optimisation issue on the tsclient in ubuntu but can't find it - it's v1.5

---

### Post by rfreedman on 2010-04-05
Use rdesktop instead of tsclient - tsclient is just a gui front-end for rdesktop, and rdesktop exposes more options.

Pass the -xl option, which increases the bandwidth usage.

From the documentation:

-x <experience>
    Changes default bandwidth performance behaviour for RDP5. By default 
only theming is enabled, and all other options are disabled (corresponding to modem (56 Kbps)). Setting experience to b[roadband] enables menu 
animations and full window dragging. Setting experience to l[an] will also 
enable the desktop wallpaper. Setting experience to m[odem] disables all 
(including themes). Experience can also be a hexidecimal number containing the flags.

---

### Post by LINUX-JJ on 2010-04-06
thanks for the rdesktop heads up - that's the wallpaper sorted but I can not get the sound re-directed back to the remote back.  If I used the tsclient it works but using rdesktop it does not this is what I am trying ....

rdesktop -f -xl -u (user) -p (password) -r sound:local server

and

rdesktop -f -xl -u (user) -p (password) -r sound:local driver:OOS: device:$AUDIODEV  server

I got this info from the help but I get no sound back.

Please help!!!

---

