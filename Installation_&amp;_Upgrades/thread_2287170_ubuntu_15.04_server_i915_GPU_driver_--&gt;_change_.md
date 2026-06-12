---
title: "ubuntu 15.04 server i915 GPU driver --&gt; change resolution"
date: 2015-07-17
forum: Installation &amp; Upgrades
---

### Post by alex351 on 2015-07-17
hi there,

i am running an ubuntu server with an intel gpu. The server is connected via HDMI and the resolution automatically jumps to 1920x1200 based on the display. the i915 driver is used and I would like to lower the resolution to 1024x768 (or something similar as connect to it via VNC on significantly smaller displays). However I was unable to achieve this. Setting GRUB_GFXMODE=1024x768 in /etc/default/grub seems to only work until the i915 driver is loaded - then resolution switches to 1920x1200 again...

any help would be greatly appreciated - however swichting to bootoption nomodeset in not an option due to powersavings...

cheers
alex

---

### Post by oldfred on 2015-07-19
Can you try this as boot parameter like nomodeset?
 Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

If that works then you can make it permanent in grub.

 gksudo gedit /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
        o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

---

### Post by alex351 on 2015-07-20
thanks - works like charm!

---

### Post by oldfred on 2015-07-20
Glad that worked. 
You can change thread to solved.

---

