---
title: "microsoft vx1000 support"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by deadite66 on 2008-10-10
reading [http://lwn.net/Articles/291036/](http://lwn.net/Articles/291036/) the cam should have support with 2.6.27.

and yet

```
[  227.725016] usb 1-1: new full speed USB device using uhci_hcd and address 4
[  227.887359] usb 1-1: configuration #1 chosen from 1 choice
[  227.900522] usb 1-1: SN9C105 PC Camera Controller detected (vid:pid 0x045E:0x00F7)
[  228.032042] usb 1-1: No supported image sensor detected for this bridge

moon@desktop:~$ lsusb 
Bus 001 Device 004: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000

```

no /dev/video0

which is worse than it was under hardy, with hardy i had an image although the colours were all wrong but with intrepid not even that.


any ideas what up?

---

### Post by sjhstorm on 2008-10-10
This seems to be a regression in the kernel, I have placed a bug report here: [https://bugs.launchpad.net/ubuntu/+bug/280657]("https://bugs.launchpad.net/ubuntu/+bug/280657")

---

### Post by deadite66 on 2008-10-10
great, thank you.

---

