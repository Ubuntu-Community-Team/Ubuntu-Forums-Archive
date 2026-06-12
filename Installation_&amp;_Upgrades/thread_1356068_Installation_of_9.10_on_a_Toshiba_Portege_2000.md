---
title: "Installation of 9.10 on a Toshiba Portege 2000"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by thomas_web on 2009-12-15
Hey guys.

I'm trying to install Ubuntu 9.10 on my Toshiba Portege 2000 over a cd rom drive which is connected to the laptop by a pcmcia card.

The CD-Rom Drive is called Slimline CD-ROM Light 24x (PX1052E-1NMD for PCMCIA).

The laptop is some years old now:
Mobile Intel Pentium III-S, 750 MHz, 
ULi/ALi M1644 CyberALADDIN motherboard, 
240 mb SDRAM, 
Trident video accelerator CyberBlade XP Ai1 v5.9030-008O.22ICD


I went to the bios and changed the boot order so it would boot from the cd.

Then it shows that screen where you can choose what to do next (install, try out, etc.).
I chose install and after some computing it started to show the little ubuntu icon in the middle of the screen. after that, the screen went all black with just a little white underline blinking character in the top left. 

At the end, regrettably, there are some 15 lines with the following:

stdin: error 0

... and ...

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system



I really don't know how to procede from there and I'm sorry if this a rather simple problem but any help would be greatly appreciated.
I would like it very much to us ubuntu on this device. So, I'm counting on you guys to give me some advice. :neutral:

---

### Post by kerry_s on 2009-12-15
there should be a check disk option, you should see if you got a bad burn.

---

### Post by thomas_web on 2009-12-16
i redownloaded the .iso and burned it again, but i still get the same error. when i check both cds for errors the same error occurs as described in my first post.

is it possible that my cd drive stops and it doesnt work because of that? i listened to the cd spinning around in the drive but  after i select something in the installation screen it seems to stop.

edit1:
i checked both cds on another machine. first one really had an error. second one should be fine.

however, i just tried to install 9.04 from a cd which i already used on another device, so this should work anyway and i got the following:

[5.527640] IO APIC resources could be not be allocated.
Loading, please wait ...

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

edit2:
is it maybe possible to install ubuntu from a usb stick to see if my cd drive is the problem?

---

### Post by thomas_web on 2009-12-19
i tried the usb stick variant, but i can't boot from usb devices. there is no such option in the bios.

besides that has anyone any ideas how to solve this?

thanks in advance

---

