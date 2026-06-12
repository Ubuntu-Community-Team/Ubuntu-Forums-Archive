---
title: "Problem with Graphics"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by C.C.C.P. on 2011-01-25
Well, my problem started yesterday, a new driver came when I tried to update my NVIDIA graphics driver, it was version 96, when I upgraded it reboot gave me nothing, just black screen writing writing smth ending with at tty1, well anyway I fixed it bu generating a new xorg.config and copying it under into /etc/X11... folder, but now I can not see COMPIZ effects, Search Drivers shows me that there are three NVIDIA drivers, one of them is enabled, but when I choose try to enable graphics it says me "Desktop effects could not be enabled" My card is NVIDIA 9700 GT

---

### Post by DesignSuccessU on 2011-01-25
I also want to know  graphics card is a hardware or software. if it is a  software then what system is required to install nvidia geforce 8800.how  to solve graphics problem of pcsx2. my system configuration is:
intel core 2 duo
1 gb ram
2.04 ghz

---

### Post by cascade9 on 2011-01-25
> **C.C.C.P. said:**
> Well, my problem started yesterday, a new driver came when I tried to update my NVIDIA graphics driver, it was version 96, when I upgraded it reboot gave me nothing, just black screen writing writing smth ending with at tty1, well anyway I fixed it bu generating a new xorg.config and copying it under into /etc/X11... folder, but now I can not see COMPIZ effects, Search Drivers shows me that there are three NVIDIA drivers, one of them is enabled, but when I choose try to enable graphics it says me "Desktop effects could not be enabled" My card is NVIDIA 9700 GT

I think you mean 9800GT, or 9600GT. There is no 9700GT... 

nVidia 6XXX-9XXX (and newer) cards should be using nvidia-current, not the old 96.xx drivers. Those drivers wont even support the 9XXX cards. 

How did you install these 96.xx drivers? 

> **DesignSuccessU said:**
> I also want to know  graphics card is a hardware or software. if it is a  software then what system is required to install nvidia geforce 8800.how  to solve graphics problem of pcsx2. my system configuration is:
intel core 2 duo
1 gb ram
2.04 ghz

A video card/graphics card is hardware.....but you need software for the hardware to work. 

The easy way to install the drivers with ubuntu is to go-

System-> Administration-> Hardware Drivers

*edit- you dont  need to install the nvidia drivers, there are open source drivers that work just fine. They are sklower than the nvidia closed source drivers, which is why most people use the nvidia drivers.

---

### Post by C.C.C.P. on 2011-01-25
Well, when I first installed the driver i did it from System>Administration>Software Drivers! Even now it shows me that my current recommended driver is installed, but looks like it doesn't work! And my graphics is NVIDIA 9700 GT, it was a card for Asus G50A1! I tried to reinstall the driver, and it gave me nothing, cant still enable compiz. It was functioning nice, before yesterday, when an update to NVIDIA ver. 96 came!

---

### Post by cascade9 on 2011-01-25
9700M GT. Not quite a 9700 GT. 

I have no idea why you've got a 96.xx driver update, like I said..those drivers will never work with that card. 

I'd try removing all the drivers, then try  System-> Administration-> Hardware Drivers again.

---

### Post by C.C.C.P. on 2011-01-25
Or yeahh It is 9700m GT I tried to remove them once, reboot and then install again, result is the same! It says that driver is installed and in use, but I dont see it working!

---

