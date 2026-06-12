---
title: "3G Mobile Broadband - HAUWEI E220 - Kernel 2.6.31-3-generic"
date: 2009-07-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kylea on 2009-07-31
I have been testing my Mobile Broadband with a HAUWEI E220 -using Kernel 2.6.31-3-generic #19-Ubuntu SMP Tue Jul 14 16:07:02 UTC 2009 x86_64 GNU/Linux

and 2.6.31-4-generic

It seems 2.6.31-4-generic is causing quite a few stack traces.

The modem works with 2.6.31-3-generic but not 2.6.31-4-generic.

I'll do some more tests

---

### Post by kylea on 2009-07-31
Ok can confirm that 2.6.31-4-generic is a problem for Mobile Broadband E220 modem

---

### Post by Buffalo Soldier on 2009-07-31
I think Huawei E220 is quite a widespread modem, you bug report in this matter would be very valuable. Have you done it?

---

### Post by GeorgeVita on 2009-07-31
Hi **kylea**,
I had a similar problem with my Huawei E169 described at:
[http://ubuntuforums.org/showthread.php?t=1224361](http://ubuntuforums.org/showthread.php?t=1224361)

that seems to be solved with later kernel builds:
> **GeorgeVita said:**
> UPDATE: Solved
I download kernel 2.6.31-999-generic #1248771614 (daily 28/July/09) and now CONNECTED with the Huawei E169. Double checked that the problem exists by booting on 2.6.31-4.22 and -4.23

Kernel daily builds at: [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/)

Regards,
George

---

### Post by kylea on 2009-08-03
Hi George - thank you - did not realise I posted twice - am doing downloading a new kernel as suggested and will advise

---

### Post by kingfisher on 2009-08-03
Loading the kernel modules for the HUAWEI E220 modem works now with the new kernel version 2.6.31-5.24.
What still does not work is unplugging the device - something crashes and the usbserial module stays loaded and is marked as being in use, so it cannot be unloaded.

---

### Post by kylea on 2009-08-04
Ok kernel 2.6.31-020631rc5-generic is working

---

### Post by kylea on 2009-08-04
> **kingfisher said:**
> What still does not work is unplugging the device - something crashes and the usbserial module stays loaded and is marked as being in use, so it cannot be unloaded.

Can confirm the unload does not work

---

### Post by kingfisher on 2009-08-04
The related bug report on launchpad: [https://bugs.edge.launchpad.net/ubuntu/+source/linux-meta/+bug/406312](https://bugs.edge.launchpad.net/ubuntu/+source/linux-meta/+bug/406312)

Please provide further information there and select "This bug affects me too" if you experience this problem too.

As someone said before the Huawei E220 is quite a common usb modem and this device worked perfectly with 9.04.

---

### Post by kylea on 2009-08-04
Have selected "This bug affects me too".

Will try and get some more info

---

