---
title: "Problems with radeon driver and upgrade."
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by digitaljeff on 2010-04-30
First off im a pretty big linux noob, so i may be missing something.

I recently installed 9.10 and had to install under safe graphics, as i would get no video with regular install.

im running a 9800 pro , with an lcd attached to DVI on the card (with a vga to dvi adapter).

everything installed fine. i noticed i had horrible video acceleration, so i checked out my xorg.conf and found out i was running the vesa driver. i tried first to install ATI's 9.3 drivers but those didnt work, went back to vesa and tried to configure to use the open source radeon driver. this again would not work, after reboot i would get black screen. i searched a little and found this bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413)

i tried all work arounds on that link and none worked for me, either i was still using vesa, or i would have no video.

weird thing is that i was not able to switch to a terminal by ctrl alt f1 either after a boot to black screen.

decided to stay on vesa driver and worry about the problem another day when 10.04 came out yesterday. Figured hey, might as well upgrade and see if that fixes my problems. So i upgraded and after reboot im now staring at a nice black screen. im figuring its again a driver problem, but im not sure. I cant switch to a terminal, and i cant seem to halt at grub via esc. 

want to see how i can fix this as i dont really want to re-install again. 

another thing, was the safe graphics option removed from the 10.04 image? i tried booting it last night and couldnt seem to find the option?

any help would be greatly appreciated. and please be easy on me, im a big linux noob.

---

### Post by spydeyrch on 2010-04-30
Did you try to install the proprietary drivers via the hardware updater in ubuntu? If you go to System --> Admin --> Hardware, it will search your hardware for any needed drivers. I have 2 ATI HD 3870 in crossfire and that is how I got my video drivers to work.

Just and idea.

-Spydey :lolflag:

---

### Post by digitaljeff on 2010-04-30
comes back and says "no proprietary drivers are in use on this system"

and nothing is listed.

---

