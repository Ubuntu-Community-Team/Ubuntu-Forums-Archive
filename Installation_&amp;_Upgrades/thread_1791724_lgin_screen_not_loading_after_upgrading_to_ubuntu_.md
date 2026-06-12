---
title: "lgin screen not loading after upgrading to ubuntu 11"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by cbungau on 2011-06-27
Hi,

I have upgraded from Ubuntu 10 to Ubuntu 11 and the login screen fails to load after the reboot. A (dark) pink monitor is displayed and I can see the mouse cursor, which I can move just fine, but no log in options appear. It stays like this ((dark) pink display + mouse cursor) forever. Ubuntu is installed alongside Windows 7, so during the reboot there is the option to boot into the Ubuntu recovery mode directly.

If I select the recovery mode, then the screen becomes black and nothing happens. However, following the attempt to boot into the recovery mode, after a new forced shutdown and restart, selecting the Ubuntu partition works perfectly.

It looks like each time I have to attempt to go into the recovery mode (resulting in the completely black screen, not allowing me to do anything), then force the computer to restart, and go into the standard Ubuntu partition just fine. However I would be very grateful if you could please suggest a way of avoiding doing this each time I reboot the PC.

Thank you very much,

Cristian

---

### Post by MAFoElffen on 2011-06-27
> **cbungau said:**
> Hi,

I have upgraded from Ubuntu 10 to Ubuntu 11 and the login screen fails to load after the reboot. A (dark) pink monitor is displayed and I can see the mouse cursor, which I can move just fine, but no log in options appear. It stays like this ((dark) pink display + mouse cursor) forever. Ubuntu is installed alongside Windows 7, so during the reboot there is the option to boot into the Ubuntu recovery mode directly.

If I select the recovery mode, then the screen becomes black and nothing happens. However, following the attempt to boot into the recovery mode, after a new forced shutdown and restart, selecting the Ubuntu partition works perfectly.

It looks like each time I have to attempt to go into the recovery mode (resulting in the completely black screen, not allowing me to do anything), then force the computer to restart, and go into the standard Ubuntu partition just fine. However I would be very grateful if you could please suggest a way of avoiding doing this each time I reboot the PC.

Thank you very much,

Cristian
Welcome to Ubuntu Forums!

Please read the first 3 posts of this Sticky and go through the Troubleshooting flow chart in Post 1:
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

---

### Post by cbungau on 2011-06-27
Hello,

Thank you very much for your reply. I have attached the .xsession-errors file which I got in my home directory, maybe it shows some meaningful hints to solving this.

Meanwhile I also used the startup manager application and I noticed the resolution was set to a much lower value than it really is. So I set the display resolution to 1600x1200, although it is 1600x900 in reality (but this option was not available from the selection list).

Then rebooted the PC and it appears to be working fine, at least until now I have made 3 consecutive (successful) reboots.

So setting a resolution closer to the real one seemed to have solved the issue :p.

Thank you again and please let me know if the messages in the attached file suggest I should take any other course of action.

Best regards,

Cristian

---

