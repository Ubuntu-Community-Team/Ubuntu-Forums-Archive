---
title: "touchpad not working properly Panasonic toughbook cf-30"
date: 2016-10-20
forum: Installation &amp; Upgrades
---

### Post by offset442 on 2016-10-20
Hello,

looking for a little help with an old Milspec CF-30 for field work, i seem to have gotten everything setup the way i want except that the touch pad is not working as a touch pad, it seems to be identified as a generic ps/2 mouse which means pointing works and tap to click works, but side scrolling and multi finger scrolling does not work........this unit has a low res 13 inch screen scrolling is required and a external mouse is not an option since there will almost never be a good surface to use it on...in field work

I have been researching this issue for almost a whole day and have found that in the past there where several fixes for this issue but none of them seem to apply anymore, since these laptops are still highly usefully for workmen like me that need to use a laptop in hazardous places like roofs and hanging off the side of antenna towers it would be kinda of nice if it worked.

so this old thread right here defines the issue with the hardware.......

[https://ubuntuforums.org/showthread.php?t=844968](https://ubuntuforums.org/showthread.php?t=844968)

apparently, the touch-pad defaults as a dumb ps2 mouse unless its told otherwise, the fix was to add some startup kernel options to grub to get it kick started

fast forward almost a decade we are at grub2 and kernel 4 plus, so this fix needs a little updating....... im running Ubuntu 16.04 

also open to any better ideas as well of-course....

---

### Post by offset442 on 2016-10-20
OK tried this stuff:

1. Use sudo + your favourite editor to open /etc/default/grub

$ sudo nano /etc/default/grub

2. Add &#8220;i8042.notimeout i8042.nomux&#8221; to the line which says GRUB_CMDLINE_LINUX=&#8221;&#8230;&#8221;.

(For example, mine looks like this after the edit: GRUB_CMDLINE_LINUX=&#8221;i8042.notimeout i8042.nomux i8042.noloop&#8221;)

3. Update grub.

$ sudo update-grub

restarted and nothing changed with the touch pad so i guess this is not the issue

_________

- Xinput -list still shows its as "ps/2 Generic mouse" while is should show as something to the effect of "touchpad"

xinputs shows these devices,

Virtual core pointer
-virtual core xtest pointer (no idea what this is)
-fujitsu componet usb touch panel (touch screen, is working fine)
-PS/2 Generic mouse (touch pad)

- modprobe and  removing psmouse and re-adding it only disables the touchpad completely and restores it as a PS/2 Generic Mouse again

---

### Post by offset442 on 2016-10-21
tried 

#synclient -l
#Couldn't find synaptics properties. No synaptics driver loaded?

since its registering as a ps/2 mouse no touchpad drive had been loaded, anyway i can force a touch pad driver to load?

---

### Post by offset442 on 2016-11-05
bloop...

---

