---
title: "USB device automounting..."
date: 2005-03-02
forum: Installation &amp; Upgrades
---

### Post by snitgaard on 2005-03-02
[size=2]I have had a number of problems with my USB ports on my machine. My main concern is that I can not use USB memory dongles and USB hard disks to transfer data - really annoying as it does work perfectly on my Windows installation on the same machine. At some point I also had problems simply booting with a storage device in one of the USB ports, but disabling USB boot in the BIOS has resolved this for now.
 
In Windows the LED in the USB memory turns on or the USB hard disk starts spinning and the drive is accessible when plugged in, but running Ubuntu the LED remains off. Only if the USB memory dongle is plugged in during booting, the LED will be turned on.
 
I did have the impression that the Ubuntu distribution supported automounting of USB memory dongles, but I guess I will need to do some tinkering to make it work. I have a fair idea on what is needed:
[list]
[*]A proper mounting point: /media/usb
[*]Editing of /etc/fstab to include the USB device with proper parameters
[/list]I have seen the device detected as /dev/sda . I guess that should be used for /etc/fstab. Will this always be the name? What happens if multiple devices are connected at the same time, like USB memory dongle, my camera and maybe a Palm device? :???: 
 
This post may not be that informative, but give me a hint and I will dig up what is needed. I guess I badly need the HOW-TO on fixing USB automounting...
 
[/size]

---

