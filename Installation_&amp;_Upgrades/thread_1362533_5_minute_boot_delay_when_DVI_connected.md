---
title: "5 minute boot delay when DVI connected"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by mahlty on 2009-12-23
Hey people,

I have a bizzare issue with Mythbuntu 9.10. There is a 5 minute delay during the boot sequence (completely black screen).

The delay only occurs when using this hardware combination:
- Using DVI to HDMI cable connected to Sony Bravia LCD
- Using Western Digital 1TB SATA harddisk

I originally installed on an 80GB SATA drive which worked fine, then decided to upgrade the drive. The install process went fine on the 1TB drive but then problem appeared after first reboot.

If I use a VGA cable, it boots fine. If I leave the DVI/HDMI cable in place but put the 80GB drive back in then it boots fine. Something about the combination of DVI + 1TB HD causes this delay. 

Here is the dmesg log showing the delay: 
[http://mahlty.com/temp/dmesg%20-%20delay.txt](http://mahlty.com/temp/dmesg%20-%20delay.txt)

As you can see there is a 300 second delay just after the lines referring to keyboard/mouse usb device. I have tried connecting an entirely different keyboard but the problem remained. 

Here is the dmesg log with no delay (VGA cable):
[http://mahlty.com/temp/dmesg%20-%20no%20delay.txt](http://mahlty.com/temp/dmesg%20-%20no%20delay.txt)

I used a difference viewer on these two files and found only one difference prior to the delay. The log with no delay had two extra lines: "APIC calibration not consistent with PM-Timer"... and "APIC delta adjusted to PM-Timer...". Is this significant? Are there any other logs I should be checking for clues?

This is driving me nuts and doesn't make any sense to me. I've installed all available updates. Apologies if it's something obvious, i'm very new to linux. Any ideas very much appreciated! 

Thanks
Matt

---

### Post by mahlty on 2009-12-25
Sorted.

I stumbled upon this:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/465350](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/465350)

I edited /etc/default/grub and removed the "quiet splash" options and problem solved. Still a mystery why it worked with the VGA cable, or why it had worked when installed on the 80GB drive...

---

