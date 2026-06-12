---
title: "Help needed for installing Ubuntu 7.10 on HP laptop"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by hakrya08 on 2008-03-09
I am a complete newbie to linux. I have a HP Pavillion dv6000 laptop. The following are it's specifications.

Processor: AMD Turion 64 X2 Mobile Technology TL-60 2.00 GHZ
Memory(RAM): 1982 MB
System Type: 32-bit OS
Graphics: 
  Display adapter type NVIDIA GeForce Go 6150 
  Total available graphics memory 799 MB 
        Dedicated graphics memory 64 MB 
        Dedicated system memory 0 MB 
        Shared system memory 735 MB 
  Display adapter driver version 7.15.11.6743 
  Primary monitor resolution 1280x800 
  DirectX version DirectX 9.0 or better 
 
I try to install from an Ubuntu 7.10 Live CD, but once I click on the Start or Install Ubuntu. It starts loading but than it checks through stuff. But than it comes to a line where it says the Bios Version not found and other such things than it goes to a black screen. Can someone please help with this problem.

---

### Post by uberlube on 2008-03-09
Hopefully it doesnt have anything to do with your BIOS. Try adding vga=791 to the boot procedure by pressing F6 while 'start or install ubuntu' is highlighted . Then delete 'quiet splash' and add the 'vga=791'

---

### Post by Pumalite on 2008-03-09
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)
Update your BIOS, just in case.

---

