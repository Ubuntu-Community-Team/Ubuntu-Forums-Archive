---
title: "Ubuntu purple screen (freeze)"
date: 2013-02-05
forum: Installation &amp; Upgrades
---

### Post by Risquel on 2013-02-05
Hi, I installed Ubuntu 12.10 alongside windows 7 with a dual boot, windows 7 works fine but when i select to boot Ubuntu it takes me to the Grub... i continue and it just hangs on a purple screen until i reboot, i have tried recovery mode but it just hangs on "initializing ram disk" and i have tried pressing E and changing things to "nomodeset" but NOTHING is working. I have an AMD gpu which i know is finicky with it but i cant get into the options to download the package "the sudo apt get thingy"

ANY HELP IS APPRECIATED, I really want to use Ubuntu and i'll do anything to make it work

Thanks, Risquel

---

### Post by dino99 on 2013-02-05
to get the verbose mode (and see whats going on while booting), edit (E) the boot line, and:
- remove "quiet splash"
- add "drm.debug=0xe plymouth:debug"

After the system is loaded, open a terminal to make the changes permanent:

[HTML]sudo gedit /etc/default/grub[/HTML]

change the line to get:
```
GRUB_CMDLINE_LINUX_DEFAULT="drm.debug=0xe plymouth:debug"
```

and finally, update grub:
[HTML]sudo update-grub[/HTML]

note:  that kind of trouble can depend of how the display is plugged (hdmi, ...) and the card used. With very recent hardware, the latest packages are also needed most of the time (kernel, video driver)
So, how is yours ?

---

### Post by Risquel on 2013-02-05
Thanks for the reply, I tried "- remove "quiet splash"
- add "drm.debug=0xe plymouth:debug" and it still hangs on purple screen

I have two displays connected to my HD5850 using a VGA and an HDMI

Thanks, Ris

---

### Post by dino99 on 2013-02-05
for testing, use only your vga device; if that works, then you will know to dig about your graphic card model +hdmi (googling around, if a problem exist, you might not be the only one with)

maybe you can also try some boot option too : google around "ubuntu boot option"

---

