---
title: "Strange problems with 7.04 to 7.10 upgrade"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by MattinTucson on 2008-07-23
I recently upgraded from 7.04 to 7.10.  I have experienced a variety of strange troubles.  I recommend people re-installing.  Here are a few problems I have had, and I wonder whether anyone can help.

1. The Logout button has removed the options for "reboot" and "shutdown," and the only suggestion I could find on the internet suggested the "login screen" option in the "Administration" menu, but I couldn't find "login screen" on either menu in the "system" tab.  I have to go to the command line to shut down.  

2.  I keep getting the tan/orange blinking screen when the system starts up.  I have to go into a terminal, and do the " /etc/init.d/gdm stop, dpkg-reconfigure xserver-xorg" routine.  However, I can only get back to a window interface by using "startx" as "/etc/init.d/gdm start" takes me back to the blinking log-in screen.  I've used envy, and 3D works now, but it still will not start up correctly.

3. Evolution eats up all the processor, and I can't kill it using "kill" or "top."

If anyone has any suggestions for these odd and persistent problems, let me know.

Thanks.

System:  Dell Inspiron E1505 laptop, GeForce Go 7300 video card, 2.6.22-15 Generic kernel, no desktop effects

---

### Post by Partyboi2 on 2008-07-23
> 1. The Logout button has removed the options for "reboot" and "shutdown," and the only suggestion I could find on the internet suggested the "login screen" option in the "Administration" menu, but I couldn't find "login screen" on either menu in the "system" tab. I have to go to the command line to shut down.Have a look at System>Admin>Login Window on the first tab click on "Edit commands"

Edit: Fixed up

---

### Post by MattinTucson on 2008-07-31
The "system" button on my main toolbar (with "applications" and "places") only has options for "Administration" and "Preferences," and neither of them have options for "login screen."  I wonder if there is some problem when I first set it up with 7.04 that is now manifesting itself.  

Also, trying to solve the "blinking login-in screen" I did a ctl-alt-f1, and brought up "top" as root, and found the application was "gdmgreeter."  After doing some searching on the problem, I re-installed gdm using synaptic.  But, it is still doing the same thing.  

I am having a hard time understanding what is happening.  I have never had such a difficult time with a Linux distribution as I have had after this upgrade.  But, I don't want to nuke my system until I graduate.

Also, I am not running the "desktop effects."  I tried to keep things simple, and figured they would just cause more problems.

---

### Post by zvacet on 2008-07-31
Look under **system>admin>login window** and do as **Partyboi2** suggested.

---

