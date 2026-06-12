---
title: "USBMidi Installation Help!"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by corevette on 2007-02-16
I have a Midisport 1x1 hooked up to my keyboard/piano.  I followed the steps here: [http://ubuntuforums.org/showthread.php?t=96506](http://ubuntuforums.org/showthread.php?t=96506) , but I cannot get the piano to make/record a single sound.  I heard i need to install this: [http://homepage3.nifty.com/StudioBreeze/software/usbmidi-e.html](http://homepage3.nifty.com/StudioBreeze/software/usbmidi-e.html) .

i tried doing a 'make' and i got this error: 
> corevette@corevette:~/Desktop/usbmidi-20040829$ make
Makefile:18: /usr/src/linux/.config: No such file or directory
make: *** No rule to make target `/usr/src/linux/.config'.  Stop.
corevette@corevette:~/Desktop/usbmidi-20040829$ 


here's an 'ls' of the directory:
> corevette@corevette:~/Desktop/usbmidi-20040829$ ls
ChangeLog  Makefile.RedHat  README   usb-midi.c
Makefile   Makefile.zaurus  testing  usb-midi.h


what do i do?

---

### Post by dando80 on 2007-03-22
Do u have your kernel source installed and the link /usr/src/linux pointing to the appropriate /usr/src/linux-source-2.6.x directory?

---

