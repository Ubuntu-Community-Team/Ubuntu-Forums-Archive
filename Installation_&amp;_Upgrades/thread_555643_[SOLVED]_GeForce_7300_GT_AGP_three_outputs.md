---
title: "[SOLVED] GeForce 7300 GT AGP three outputs?"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by dwf_starband on 2007-09-20
I just installed a new video card.  (I specifically wanted video out for mythtv)
Its a GeForce 7300 GT AGP with three outputs on the back, CRT, S-video and DVI.

I spent a while last night trying to configure it for my computer using nvidia-settings.

I used the command,

sudo nvidia-settings

to start nvidia's settings program and then arranged the monitors saved and rebooted.

I different variations of twinview and separate x screens, but just managed to get different combinations of 2 monitors at a time.

Is it possible to have two monitors plus a tv connected at the same time and be able to use all three?

thanks for your help,

dennis

---

### Post by MrHippocampus on 2007-09-20
As far as I know it isn't, a normal card only has two RAMDAC's onboard, these convert the display in the graphics card RAM to something a monitor can understand. These RAMDAC's can be used by any of the three outputs, but only two of the outputs can operate at the same time because there are only two RAMDAC's :(

---

### Post by dwf_starband on 2007-09-20
I was afraid of that. thanks for your help.

dennis

---

