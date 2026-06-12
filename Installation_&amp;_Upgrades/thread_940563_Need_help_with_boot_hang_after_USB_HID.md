---
title: "Need help with boot hang after USB HID"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by mike.headon on 2008-10-07
Hello folks.....
On all kernels later than 2.6.22-14, I get the hang after
/build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c:
System is home-built Athlon XP 2000+ on Asrock K7NF2 mobd.
I have tried the fix described in 
[http://ubuntuforums.org/showthread.php?t=938173](http://ubuntuforums.org/showthread.php?t=938173)
but with no improvement (of course, I am not 64-bit).
I have tried various workarounds such as removing surplus drives, disabling SATA but all to no effect.
So, I will be very grateful if anybody can suggest anything else to try.
Thanks - Mike

---

### Post by Pumalite on 2008-10-07
Memory?

---

### Post by mike.headon on 2008-10-07
512 Mb. Runs XP Pro and other distros with no problem.

---

### Post by iamah on 2008-10-31
I got similar problem, I'm able to run the live cd and install by pressing F6 and adding options "all_generic floppy=off irqpoll pci=nomsi" at boot.

However, after installed I'm not able to boot, for it hangs at USB HID, then drops to busybox with this message:

"Gave up waiting for root device (...) Alert! /dev/disk/by_uuid/[disk id] does not exist. Dropping to shell"

I'm guessing its something with my sata HDD, hes getiing a huge disk id, dunno if thats normal... this sata hdd is connected to sata 4 port, not sata 1 port, but I can't try it at port 1 because my vga card is too big...

I'll subscribe this thread.

---

