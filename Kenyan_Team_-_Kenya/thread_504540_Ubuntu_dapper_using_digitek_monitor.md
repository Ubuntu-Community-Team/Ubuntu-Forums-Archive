---
title: "Ubuntu dapper using digitek monitor"
date: 2007-07-19
forum: Kenyan Team - Kenya
---

### Post by mwero001 on 2007-07-19
I recently installed ubuntu dapper on a friends computer and it brought up some issues with his monitor (it has a frequency of 50/60Hz). It couldn't display anything but the monitor's frequency range (I was baffled to). I've googled with no success. Any assistance guys?

---

### Post by ronaldotis on 2007-08-30
Try typing:
sudo vi /etc/x11/xorg.conf on the command line depending on your favourite text editor. Do not attempt this when logged in as root. Follow the instructions which will require an indepth knowledge of your hardware.
Reboot the computer.
Hope it works, good luck.

---

