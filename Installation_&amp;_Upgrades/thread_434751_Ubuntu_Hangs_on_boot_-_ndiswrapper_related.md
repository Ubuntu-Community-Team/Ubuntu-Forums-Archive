---
title: "Ubuntu Hangs on boot - ndiswrapper related?"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by jeanoisette on 2007-05-06
Hello, I'm a bit of a newby and definitely NOT techy. Yesterday I decided to install Ubuntu on an previous XP machine and everything went perfectly until I tried to get my wifi connection going. It used to work on the XP OS but I had recently changed by WEP access keys to the wifi router and had not updated them to this machine. My wifi adapter is a Broadcom 4306 and seems to have quite a history of problems on Ubuntu so I tried following the instructions provided on this forum. I was able to get to the part that said "sudo apt-get install ndiswrapper-utils-1.9" and it came back with the reply that it could not get the ndiswrapper utils. So I got the latest ndiswrapper from the sourceforge site and tried installing it but when I followed the installation instructions it could not remove the ndiswrapper.ko file. I tried to delete it direclty and could not. In any case, after going through this process, I rebooted just in case that was what I needed and the machine hanged on reboot - the little red line just didn't move and after a while I got the following: /bin/sh: can't access tty; job control turned off (initramfs). After this I tried reinstalling ubuntu from the CD but still have the same problem.

Sorry for the length of the description but I've tried to be as brief as I could, given the hours spent on this! 

Thanks for any help. Cheers.

---

### Post by derrekito on 2007-05-06
I've never had much luck using ndiswrapper.  are you positive there are no linux alternative drivers for this device? If not, is ndiswrapper fuily updated?  I've had too many issues with wrapper, and I usually just turn to purchasing a device that is better supported under Linux.

---

