---
title: "Installation problems Ubuntu 10.10"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by stryker617 on 2012-01-20
I am trying to install Ubuntu 10.10 on a new build. I have installed Windows 7, and used the windows installer. Once the computer restarts, it loads up the Ubuntu text, but for some reason stops there and that's it. The last part is

[  151.950512]  type=1400 audit(1327085699.384:9): apparmor="STATUS" operation="profile_load" name="usr/sbin/cupsd" pid=6989 comm="apparmor_parser"

I am not sure what all this means since I am new to Ubuntu. I have tried downloading the CD version, and installing that way, but same thing happens. I am not sure if I am doing something wrong, or if I just cannot use Ubuntu at all.

Here are the computer specs:
CPU = i5-2500
MB = GA-P67X-UD3-B3 Gigabyte
Mem = Patriot 8GB PC3 12800
GPU = GTX 550 Ti
PSU = OCZ 600W
HDD = Seagate SATA 6.0 GB/s 7200 RPM
DVD = Sony CD/DVD Burner

Thanks in advance if anyone can help me here

---

### Post by hansdown on 2012-01-20
Welcome to the forum, stryker617.

Could you please show the beginning of the error message?

Someone should be able to help.

---

### Post by nipunshakya on 2012-01-21
> **stryker617 said:**
> I am trying to install Ubuntu 10.10 on a new build. I have installed Windows 7, and used the windows installer. Once the computer restarts, it loads up the Ubuntu text, but for some reason stops there and that's it. The last part is

[  151.950512]  type=1400 audit(1327085699.384:9): apparmor="STATUS" operation="profile_load" name="usr/sbin/cupsd" pid=6989 comm="apparmor_parser"

I am not sure what all this means since I am new to Ubuntu. I have tried downloading the CD version, and installing that way, but same thing happens. I am not sure if I am doing something wrong, or if I just cannot use Ubuntu at all.

Here are the computer specs:
CPU = i5-2500
MB = GA-P67X-UD3-B3 Gigabyte
Mem = Patriot 8GB PC3 12800
GPU = GTX 550 Ti
PSU = OCZ 600W
HDD = Seagate SATA 6.0 GB/s 7200 RPM
DVD = Sony CD/DVD Burner

Thanks in advance if anyone can help me here

Just a simple query back to u here... Did u make sure that both OSs you are trying to run are of same architecture....i mean is both either x32 or x64???

Regards,WinuxUser

---

### Post by stryker617 on 2012-01-21
I installed both 64-bit windows 7, and 64-bit Ubuntu. For the hell of it I tried 32-bit ubuntu as well. I gave up on certain things. Turns out the 2 new power supplies, along with ubuntu, and my home electrical kept causing my fuses to blow. I got a whole new motherboard, and attached a different power supply. I am now using the Z68 Chipset.

I got Ubuntu 10.04 loaded and working, I upgraded to 11.10, and now nothing but a blank screen. I had tried installing 10.10 first, and all I got was a blank screen as well. No more text like before.

I swear, I must be the only person who apparently can't get this thing working, lol.

Thanks for any help. I am now stuck with Ubuntu ONLY on the drive, and no way to load up.

---

### Post by stryker617 on 2012-01-21
Ok, so I tried to reinstall. Have downloaded the 64-bit version of 11.10 twice, and have burned it 4 times now. Sometimes I get something to show, sometimes I don't. When I do get anything to show, it seems to lock up on this part, and just keeps repeating it until I shut the computer down:

udevd[127]: timeout: killing'/sbin/modprobe -bv pci:v 00008086d00000102sv00001458sd0000D000bc03sc80i00' [204]

that's all I get till I shut down.

Any ideas? I can't even get to an install screen.

---

### Post by stryker617 on 2012-01-21
Ok, so after much frustration with Ubuntu 11.10 and getting no where with the install, and no help really, I decided to switch out the video card. Now everything installed, and is running smoothly. From what I had gathered, from google and error messages, it had something to do with the PCI port. I was using a GTX 550 Ti GPU and switching to an ATI 5770 HD GPU made all the difference. From what I found, the newer NVIDIA drivers are not loaded into Ubuntu 11.10. Therefore nothing will show, or from what I've seen nothing will. Looks like I'm gonna stick with the ATI card in there for now till I can learn Ubuntu some more, and understand it better.

Thanks for the help though. Too bad I can't get everything working the way I wanted it to before

---

### Post by hansdown on 2012-01-21
Glad you fixed it, stryker617.

---

