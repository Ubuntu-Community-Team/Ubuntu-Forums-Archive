---
title: "system won't boot after crashed upgrade, can't even get a terminal"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Ba66e77 on 2007-10-21
The upgrade tool crashed while I was trying to upgrade to Gutsy.  After a reboot, the system displays the window with a progress bar indicating that its loading up, like you get before the login screen,:confused: then just goes black.  I've seen other posts recommending booting to recovery mode to try to get a prompt, but GRUB is ignoring my hitting ESC to try that.

Help, please?

---

### Post by pbcartwright on 2007-10-21
If you hit CTRL-ALT-F1 in the black screen does it take you to a text-based login prompt??
if so, log in. If you can do this it is a video problem, you running an ATI or NVIDIA video card?  if so, then you need to reinstall the video driver.. check the ATI page for info on that car, and NVIDIA.com for the latest driver to download & install.
if you have the nvidia card, to get X running now, you need ti edit your:
/etc/X11/xorg.conf file and change the video driver from nvidia to nv. then reboot.
If you have NVIDIA card, I would suggest installing envy, it installs what you need for nvidia to work..

---

### Post by Ba66e77 on 2007-10-21
CTRL+ALT+F1 and changing the xorg.conf worked.  Thanks loads.

---

