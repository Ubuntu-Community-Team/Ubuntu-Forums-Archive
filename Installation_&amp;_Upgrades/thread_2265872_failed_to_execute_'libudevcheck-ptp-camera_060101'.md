---
title: "failed to execute '/lib/udev/check-ptp-camera 06/01/01': No such file or directory"
date: 2015-02-18
forum: Installation &amp; Upgrades
---

### Post by UbuRegmi on 2015-02-18
Ubuntu 12.04.1 kernel 3.2.0-29

Latest automated update on February 13 is causing boot problem. The automated update asked to restart the computer.
But upon restart it is hanging and hasn't been able to boot up. It hangs with error message:


udevd[xxxxx]: failed to execute '/lib/udev/check-ptp-camera 06/01/01': No such file or directory




[IMG]http://i62.tinypic.com/a42x54.jpg[/IMG]


I'm not very familiar with bootup routine or what udevd does. check-ptp-camera seems to do with webcam, but my desktop doesn't
have webcam.
In the screen shot you will notice mount failures for c, d and e drives of a windows machine as well. May be its not specific issue with mount failure or check-ptp-camera, but something else is corrupted ?


There is no other OS in this machine.


I have tried shutting down the machine and start again, but it can't get past this error message.


What should I do to diagnose/fix this problem? Step by step instruction (for a noob) will be very much appreciated.


Thank you kindly

---

### Post by UbuRegmi on 2015-02-18
I inserted a 12.4 installation cd, but for some reason BIOS is not able boot from the DVD drive. Booting from cd in this machine had been working fine before. Also tried 14.4 installation cd, got same problem of BIOS not booting from the disk. These cds are ok, because I tested them in another computer where they work.

Another thing I tried is to go into grub menu and get a grub command line. I am not very familiar with grub, so wasn't sure if it can help. In grub command line I could view files like /etc/fstab but could not edit them even with su.

Please help I'm completely stuck !

---

