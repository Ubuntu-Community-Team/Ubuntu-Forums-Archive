---
title: "Ubuntu Server 6.06 not booting"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by Lord Chavo on 2006-06-20
1) System Specifications:
Laptop HP dv1125la
Monitor: LCD
Ram Amount: 1 GB (64 Shared with Video)
HD: Momentus 4200.2 	
     Model Number:ST960821A
     Capacity:60 GB
     Speed:4200 rpm
     Seek time:12.5 ms avg
     Interface:Ultra ATA/100
Onboard or Discreet Graphics Card: Intel 82852/82855 GM/GME
CPU: Pentium M 1.6 Ghz
MainBoard: HP i guess
Modem / Eth / Wifi brand: Intel PRO/Wireless 2200 BG
Adapter cards you have installed:
2) Version of Ubuntu your using: 6.06 server
3) Any error or output codes you receive durring the install or after: NONE

UBUNTU installs well, and everything is fine. When istallation is finished, nethier recovery or normal mode boot. it freezes in this screen:

[[IMG]http://img98.imageshack.us/img98/4884/image5585vm.th.jpg[/IMG]](http://img98.imageshack.us/my.php?image=image5585vm.jpg)

I've downloaded and burned the iso 3 times and everything is the same...

Desktop version runs perfect installed and in live cd mode, i dont understand why the server version dont.

---

### Post by jvl on 2006-06-21
try passing the acpi=off option to kernel

---

### Post by Lord Chavo on 2006-06-22
how i do that ?

---

### Post by jvl on 2006-06-22
in the grub menu, press 'e' on the line with current linux kernel. You'll get to prompt, where you'd see the lines from grub's menu.lst

scroll down to the line that says kernel /boot/vmlinux ... and press enter on it. You then should be able to edit the line like it's standard command line. add the acpi=off at the end of the line and press enter again. You should be back one prompt. Then press 'b' to boot with these commands. 

If it works, add this command to /boot/grub/menu.lst on the correct line. 

hope this helps

---

### Post by nick1 on 2006-06-22
Greetings,

If you've tried all of the previous suggestions and still have no success booting into Ubuntu, then I highly recommend you read this thread:

[http://www.ubuntuforums.org/showthread.php?t=198879](http://www.ubuntuforums.org/showthread.php?t=198879)

I too experienced the same situation you're in and I found my solution by installing the 686 kernel (it's really not that hard to do).  I've included instructions on how to do this in the thread.

Hang in there,

*Nick*

---

### Post by Lord Chavo on 2006-06-22
oh thanks, i'll try it :)

---

