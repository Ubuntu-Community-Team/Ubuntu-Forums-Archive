---
title: "HP Compaq 621 Laptop cannot boot Ubuntu"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by gang.huang on 2011-02-17
I have been using Ubuntu for years.  I just bought a new laptop - HP Compaq 621.  Hardware settings:
Processor: Intel(R) Core(TM)2 Duo CPU T6570 2.10GHz
Memory: 1GB
ROM Date & revision: 01/07/2011, 68PVI Ver. F.09
Video BIOS Revision: ATI 01/05/2011

I followed exactly what is described on Ubuntu [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Believe me, I burned image (not .iso data) to CD, but BIOS won't boot from the Ubuntu bootable CD.  I also created a USB stick, again BIOS won't boot from the Ubuntu bootable USB (I selected to boot from USB first) stick.  I tried with Desktop 10.10 32bit, 10.10 64bit, 10.04 32bit, and 10.04 64bit.

I also tried with my old Ubuntu Desktop 8.04 64bit bootable CD, which my very old Compaq Laptop installed. It allows me to see the menu. I selected "Safe mode" to install Ubuntu. But it gives me the error message: 
"udevd-event [1412] run_program /sbin/modprobe" 

Does anyone know how I can install Ubuntu on my HP Compaq 621 Laptop?

Thanks!

---

### Post by sikander3786 on 2011-02-17
Welcome to the forums :-)

First of all, check your downloaded image's integrity by running an MD5SUM check.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the sums match, burn a USB and use UNetbootin this time.

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html)

You have got a modern PC and it should boot Ubuntu successfully from both CD and a USB. I don't think that you need a Bios upgrade at the moment.

There should be a quick boot key at your Bios screen (mostly F10), press that and select your USB device.

Keep us posted ;-)

---

### Post by gang.huang on 2011-02-17
Thanks for reply. 

Please believe me that I did create the bootable USB stick and CD following the instruction on Ubuntu site.  And I did select to boot from USB or CD. But my laptop doesn't recognize the USB and CD as bootable.  I installed several versions of Ubuntu on my desktops by following the instructions on Ubuntu site, and never had such problem. Do you think that it may be a problem with the modern Laptop?

---

### Post by gang.huang on 2011-02-20
I finally installed Ubuntu 10.10 Desktop 32 bit on my Compaq 621 laptop. 

I think the most important thing to get the CD bootable is using the lowest CD writing speed.  I used 4X 600kB/s

I used UltraISO
1) Insert blank CD (at least 700 MB)
2) Open UltraISO
3) Open Ubuntu installation ISO file
4) Burn Image or F7
  a) Choose lowest CD writing speed.  I used 4X 600KB/s
  b) Choose DAO mode
5) Burn the CD

Now you can boot your Desktop/Laptop from the CD

---

