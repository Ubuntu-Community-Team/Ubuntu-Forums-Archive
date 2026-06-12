---
title: "driver pl2303 installation"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by Misbah Naveed on 2008-05-23
Hi
I have RHEL4 with kernel-2.6. I have a USB to serial convertor FT232R.this cable is sending data to a device used for temperature sensing.it is working well in windows.i have to make its interface and working in linux with kernel-2.6.RHEL4 already have pl2303.c and pl2303.h files in /usr/src..../drivers/usb/serial/pl2303.c so i did the step
1...modprobe pl2303
2...lsmod  shows the loaded module and dmesg also confirms it.now i have to make an interface from where i give value that passed to usb port and then shows the output on screen.in RHEL there is a software "QT Designer" but i donot know how to use it and the display. Can some one tell me 
**i installed the module in correct way..is there a need to apply commands make, make install...etc.
waiting 4 reply...
thanks in advance

---

