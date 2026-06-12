---
title: "Using NOMODESET for installation - no video on restart"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by Pappy-D on 2010-12-22
In order to get video on installation of 10.04 I had to use setting NOMODESET and everything went fine. However on restarting after installation I have no video. I can't find anything in the bios that controls auto reset of the monitor settings but that is what is happening. I can get a terminal with <ctrl><alt>f1 and feel my way through a shutdown. How do shut off the auto reset for the monitor?
BTW I tried a digital and analog monitor.

---

### Post by sikander3786 on 2010-12-22
Press and hold down Shift key from your Bios screen until you see the Grub menu. Highlighting the first entry there, press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot. Hopefully, you'll see the desktop this time.

Then, System > Administration > Hardware Drivers and install the Current drivers there and the problem might disappear for ever.

---

### Post by Quackers on 2010-12-22
On booting hold dow the shift key and the grub menu will appear. The Ubuntu system should be highlighted on the menu. You should press the "e" key and on the new screen navigate to the end of the line that says "quiet splash" and remove those words and replace them with "nomodeset - without the quotes - then press ctrl + X to reboot. If the desktop then loads you should install any available graphics drivers by running System > Admin > Hardware drivers.

---

### Post by Pappy-D on 2010-12-22
Okay, thank you.
I figured that out after trying modeset=1 from another list
duh i want no mode set.
Pappy-D

---

### Post by Pappy-D on 2010-12-22
Marking as solved.
BTW I added nomodeset after quietsplash and it worked.
PD

---

### Post by Quackers on 2010-12-22
Yes it would do. But if you had replaced quiet splash with nomodeset and booting failed we would have had a message on the screen to tell us where to look next.
You should now install any video drivers using System > Admin > Hardware drivers if any are available. Then after a reboot, hopefully, you will not need nomodeset again.

---

