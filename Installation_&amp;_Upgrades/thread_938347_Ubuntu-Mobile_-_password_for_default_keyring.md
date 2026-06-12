---
title: "Ubuntu-Mobile - password for default keyring?"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by Badcam on 2008-10-04
Whenever I restart Ubuntu-Mobile I keep getting asked to "Enter password for defualt keyring to unlock" "The application 'Network Manager applet' (usr/bin/nm-applet) wants access to the default keyring but it is locked"

Please how do I stop this password request? :confused:

---

### Post by p110011 on 2008-10-04
I never could get it to stop, so I ditched NM and now I use WICD.
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
It's much better.:D

---

### Post by Badcam on 2008-10-05
Thanks.

I'll follow those install instructions. I assume that WICD will recognise the existing drivers. Would that be correct?

Also, how do I uninstall Network Manager? Do I just go into Synaptics Manager and deselect Network Manager under Networking?

---

### Post by p110011 on 2008-10-05
Yeah the drivers stay and NM will uninstall by itself. You will loose connection till you set up WICD.

---

### Post by Badcam on 2008-10-05
Amazing. I got it working. Working nicely. Thank you.

Could you please advise how I can get it to minimise into a small tray icon?

---

### Post by p110011 on 2008-10-05
Here's a copy/paste of how to do that.
*In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the “Startup Programs” tab, click the “New” button. Give it a name (”Wicd” works fine). For the command, enter “/opt/wicd/tray.py”*.”

---

### Post by Badcam on 2008-10-05
And who says noobs can't use Linux? I'm enjoying this. This distro is exactly what I've been looking for, for my Kohjinsha SH8 Laptop. I'm loving it. If this keeps up, I just may well remove Vista completely.

I note from that Sessions list, that the Network Manager applet is listing there. I thought I had removed Network Manager when I installed Wicd. I have been getting instances when  using Synaptics, where Synaptics is still trying to use Network Manager. Could this be the reason? Should I remove it from the Session list?

Also, what about all the other things listed? Are they all starting whenever I run Linux? If so, can I remove any of these? For instance I probably won't be using Bluetooth, nor the remote desktop, and perhaps Visual Assistance. Are these necessary?

Thanks for all your help. It's been great.

---

### Post by p110011 on 2008-10-05
Yeah, uncheck the Network Manager. I've unchecked other programs with no bad effects.
Enjoy your new OS, I think the Developers have really done a good job:)

---

### Post by Badcam on 2008-10-05
Awesome. I don't suppose your any good with Touchscreens by an chance? Hint, hint, nudge, nudge, wink, wink!

Do you have any other tips, or links, that would help me improve my ubuntu-mobile experience?

---

