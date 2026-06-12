---
title: "Lucid - iphone with ifuse does not mount"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by genux05 on 2010-03-24
when I plug in my iphone I am unable to mount it - and it does not come up in the devices plugged in widget.

Here is my dmesg ouput
```
usb 1-2: new high speed USB device using ehci_hcd and address 5
usb 1-2: configuration #1 chosen from 4 choices
usb 1-2: can't set config #1, error -71

```

trying to mount the iphone with ifuse
```

ifuse /media/iphone/

No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.

```

here is my lsusb output
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 062a:0252 Creative Labs 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05ac:1294 Apple, Inc. iPhone 3GS
Bus 001 Device 003: ID 046d:0896 Logitech, Inc. OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

any advice would be grateful..

also I am using a iphone 3GS 16GB.

---

### Post by pickarooney on 2010-03-24
Sounds like a problem with the USB port(s) or a hardware interrupt conflict. 

Have you tried plugging it into all avaialble USB ports?
Does **lsusb **take up tp a couple of minutes to output the results?

---

### Post by genux05 on 2010-03-24
I have no other problem with other devices that plug into any of the USB ports.. and it does not take that long for the usb hardware to be detected, about 1 second max.

---

### Post by genux05 on 2010-03-25
Yeppy with the latest of updates to the 10.4 lucid system, my iphone 3GS 16GB is working :)

I had to turn of the password keyword protection to make it work, the GUI did not say but after doing

ifuse /media/iphone

it said that I needed to turn it off :).

but it is now working.. yeppy :) :) :).

ubuntu/kubuntu / linux on the whole is just great.

---

### Post by arkanovios on 2010-04-25
Sorry to bring this up again but i have the same problem.

Recently updated to Lucid RC and was looking forward to having my Iphone 3G work correctly.
I can see it in the output of lsusb but it doesn't automount. When i try it with ifuse /media/iphone (i had to manually create the iphone dir) i get the
```
ifuse /media/iphone/

No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.
```

Anyone here knows what do i have to do?
The password keyword protection removal should be done in the Iphone? It's the root password of my device?

Thanks in advance.

---

### Post by G@B0 on 2010-04-28
I have the same problem, only that I upgraded from Karmic having iPhone support with ifuse, now that I upgraded I lost the support and I can't even mount it.
I guess that I need to make a clean install, but it's weird because I have all the packages installed and nothing works.

---

### Post by arkanovios on 2010-04-28
Ok, i just installed the new updates and my iPhone is recognized.
All ok now :)

---

