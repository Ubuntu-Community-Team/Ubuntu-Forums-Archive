---
title: "Loose  Moinitor Signal @ Boot"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by Frogs Hair on 2010-02-25
Hello, 
 
I have had Ubuntu 9.10 for less than 48 hours and I like it so-far, but sometimes during boot I loose the signal to the monitor. I can hear the audio promt
indicating the program is running but the no signal window pops up on my sony monitor. If I reset all is well . I'm a new-bean so any suggestions would be great. 
I have tried both Kernals  and Ubuntu seems to start most of the time with both.

---

### Post by Kakers on 2010-02-25
Might be your display settings or drivers...

Try going to System -> Administration -> Hardware drivers and make sure that any listed are installed.

If that doesn't work...

What graphics card do you have?

Could you also include your config? - open a terminal window and type 'cat /etc/X11/xorg.conf then copy & paste to here.

---

### Post by Frogs Hair on 2010-02-25
Hello, 
Thank you  for the reply . Hardware/ Drivers shows my 3D drivers as being uninstalled .
This is correct because I don't have a 3D monitor or 3D vision hardware.

My graphics include Nvidia 8300 on board chip set and Galaxy Ge force 8400GS 512 mb
display adapter with up to date drivers.

---

### Post by Frogs Hair on 2010-02-26
Solved !!

Installed Nvidia 185 driver and now Ubuntu  boots normally .:P

---

