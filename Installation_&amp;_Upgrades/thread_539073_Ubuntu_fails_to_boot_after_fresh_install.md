---
title: "Ubuntu fails to boot after fresh install"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by PrimoTurbo on 2007-08-30
I have encountered this problem various times, I have no idea what causes it. Basically after a fresh install of Ubuntu 7.04 using both shipped CDs of either Ubuntu or Kubuntu or burned CDs, I remove the CD and restart like the setup instructs.

I get past Grub and than Ubuntu starts loading, then after only about 2-3% of the orange bar has loaded it stops.

When I boot through recovery console I notice it stops loading after:
[B]
drivers/usb/input/hid-core.c: v2.6:USB HID core driver[/B]

I have installed Ubuntu dozens of times on the same computer, I have run into this problem many times. Often I just keep reinstalling Ubuntu like 2-3 times and it goes away by itself. However I have tried 7 times today and I keep getting the exact same error. I need to find a fix!

Any ideas?

---

### Post by rsambuca on 2007-08-30
Sorry, I have no idea what is happening.  I just wanted to say how amused I am at your comment "I have installed ubuntu dozens of times on the same computer"!

---

### Post by Pumalite on 2007-08-30
Do you have an USB device plugged in?
Do you have some Linux installed? If so, then post 'lspci'

---

### Post by PrimoTurbo on 2007-08-30
I made a thread about this problem already, no one helped me :(

[http://ubuntuforums.org/showthread.php?t=428954](http://ubuntuforums.org/showthread.php?t=428954)

---

### Post by PrimoTurbo on 2007-08-30
> **Pumalite said:**
> Do you have an USB device plugged in?
Do you have some Linux installed? If so, then post 'lspci'

I have a USB mouse plugged in and a printer, I will unplug both and try to boot up see if I get a different error.

I have no other Linux installed.

---

### Post by banditti on 2007-08-30
For testing purposes, go into your bios and disable USB.  Try the install and see if it works.  My guess is it will.  Work backwards from there.

---

### Post by banditti on 2007-08-30
Maybe first you can remove anything plugged into usb. printers, thumb drives, etc.  You may not have anything plugged in, then try the above post.

---

### Post by PrimoTurbo on 2007-08-30
I remove all usb devices now it stop loading at this point.

udevd-event[1926] : run_program: '/sbin/modprobe' abnormal exit

---

### Post by Pumalite on 2007-08-30
Post your specs.

---

### Post by PrimoTurbo on 2007-08-30
Pentium 4 1.6Ghz
768 DDR RAM
ATI 9700 Pro 128Mb
Western Digital 250 GB

---

### Post by Pumalite on 2007-08-30
Use the Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below 'Start Download'

---

### Post by PrimoTurbo on 2007-08-31
I get the same error after install and reboot. :(

---

### Post by Pumalite on 2007-08-31
You have to do some serious checking of your hardware, connections, etc.

---

