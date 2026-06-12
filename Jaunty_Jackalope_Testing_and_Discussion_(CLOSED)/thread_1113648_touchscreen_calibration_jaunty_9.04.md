---
title: "touchscreen calibration jaunty 9.04"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jon_herr on 2009-04-01
I'm having a problem with a Xenarc touchscreen...  it's never worked but thought I'd try the touchscreen calibration tool since it is there.

What happens is - anywhere I touch the screen causes the 'trash' bin to open.  So every touch must cause a mouse click on the lowest part of the right side of the screen?

There are ways of making this touch screen work, but it's really difficult and dies on every kernel update.

Can you put me in touch with the developer of the touch screen calibration utility?  Thanks, Jon



lsusb produces:

lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 045e:0053 Microsoft Corp. Optical Mouse
Bus 003 Device 004: ID 0b38:0003
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen

---

### Post by Favux on 2009-04-02
Hi jon_herr,

Does your Xenarc touchscreen use the evtouch driver?  If so Tom Jaeger has updated it to work with the Xserver 1.6 in Jaunty.  It's here:

[http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/x/xf86-input-evtouch/]("http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/x/xf86-input-evtouch/")

I hope this is helpful.

---

### Post by vishalrao on 2009-04-02
Also read the comments in bug [lpbug]317127[/lpbug] as its not perfect and no idea at the moment if it will end up in Jaunty final release...

---

### Post by Favux on 2009-04-03
Good point vishalrao.  Tom does say he left out patches and stuff so it's not the final solution.  But it should keep you going, right?

---

### Post by vishalrao on 2009-04-03
The updated package is now in the repos :) Although testers are reporting you can tap but you cant drag (hence no scrolling/writing etc)... Tom Jaeger has already asked testers to get in touch with the upstream author/maintainer but doesn't look like there's any hope...

---

### Post by Alejandro Nova on 2009-04-16
AFAIK upstream NEVER implemented dragging for eGalax touchscreens. Dragging in 8.10 relied in a patch made by Debian X Task Force, and for 9.04 you have to port the Debian patch to the newer evtouch. Sad, but true.

---

