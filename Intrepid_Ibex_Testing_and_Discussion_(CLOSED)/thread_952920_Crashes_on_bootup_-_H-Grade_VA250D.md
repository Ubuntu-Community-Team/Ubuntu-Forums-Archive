---
title: "Crashes on bootup - H-Grade VA250D"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2008-10-19
I've finally decided to go whole hog and upgrade my second laptop. The upgrade went smoothly and I rebooted to find a plain white screen with the username/password box in the middle. The mouse cursor appeared as an X then changed to a scrambled square of static. After a few seconds the pc crashed completely.

Any ideas?

---

### Post by macroshaft on 2008-10-20
Upon closer investigation I've discovered a line in the syslog right at the point of the crash

> Oct 19 22:03:07 gareth-laptop gdmgreeter[6544]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 


I discovered that the module gtk2-engine-ubuntulooks isn't even installed and cannot install due to conflicts, although I have no idea what they are.

I forced the module to install and no change.

To clarify the system boots into the login screen which is the correct colour but before any details are filled in the screen changes to plain white and only the username/password box is unchanged and at this point the system completely hangs.

I'm a little dissapointed at the lack of response, I'd hoped everyone would be pushing for any remaining bugs to be identified. Come on guys!

---

### Post by jerrylamos on 2008-10-20
There's so much hardware & drivers out there that the developers haven't been able, from my viewpoint, to get everything to run on every combination especially when they do fancy tricks with graphics.

The error message in your post looks like something from System Preferences Appearance.  The "eye candy" code compiz is used heavily by Ubuntu Gnome in appearance effects and is on by default?!

Itrepid Ibex 8.10 Beta will install on my laptop but does not complete booting up.  After X windows comes up it hangs.

My workaround is to remove the fancy eye candy compiz code:
Boot in rescue mode
At the options window, choose root prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot.
 
Thereafter the laptop boots O.K. of course I don't get fancy desktop splashes & other display tricks.  I could care less since I do full screen internet, full screen Open Office write, full screen Picassa pictures, etc.

Jerry

---

### Post by macroshaft on 2008-10-20
I've never had compiz working on this laptop but would like to identify the cause for two reasons. Firstly to let the developers know to see if they can use that and secondly for my own education.

I'll give this a try & report back. Thanks.

---

### Post by macroshaft on 2008-10-20
Removing compiz had no effect. If nobody has any ideas I'll have to perform a re-install.

---

