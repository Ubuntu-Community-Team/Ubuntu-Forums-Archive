---
title: "USB error -32"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by ricardobentes on 2008-05-04
Hi!
I'm using Ubuntu 8.04 and getting error -32 when I connect any USB drive.

```
[ 9739.853608] usb 3-5: device not accepting address 73, error -32 
```

I've searched the web and found this workaround that seems to "turn off" USB 2.0 and makes the ports work at USB1 speed. 

```
sudo modprobe -r ehci_hcd
```

This way it detects and mounts the drive without problems. The problem is just the speed. Anyone knows what the problem might be and how can I fix it?

It sucks wanting to copy 4 GB of information and having to wait 1h for it... :(

I posted the problem [here]("http://ubuntuforums.org/showthread.php?t=779064") they helped me locate the problem but still no fix...

Thanks everyone!

---

### Post by ricardobentes on 2008-05-05
doesn't anyone have any idea?

Man... Guess it will be windows xp to me again... :(

---

### Post by ricardobentes on 2008-05-06
keeping this one alive....

---

### Post by waster on 2009-02-17
yep, I get this in hardy and jaunty with a crappy ralink (don't buy) wifi usb dongle.

I've read other pages which suggest that it works with different kernels (and this device has worked in the past), but yet to try it on older kernel or, heaven help me, windows.

---

