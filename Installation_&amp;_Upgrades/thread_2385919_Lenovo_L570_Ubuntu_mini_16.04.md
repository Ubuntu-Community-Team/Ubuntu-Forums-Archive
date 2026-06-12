---
title: "Lenovo L570 Ubuntu mini 16.04"
date: 2018-02-26
forum: Installation &amp; Upgrades
---

### Post by Drenriza on 2018-02-26
I am trying to install Ubuntu 16.04 mini on my Lenovo L570 but are running into two errors
i dont really know how to deal with and seeking advice.

#1 
Installation step: Detect network hardware
Error: Error while running 'modprobe -v usb-storage'

After pressing continue to the first error to see what happends i get a 'new' error

#2
Error: [!] Configure the network
No network interfaces were found. The installation system was unable to find a network device.

I had a ethernet cable plugged into the machine at this point.

I am speculating that the mini ISO comes with less drivers out of the gate for all the different systems out their.
How can i add the driver to my installation stick (USB) and load the driver before i start the installation?

Thanks in advance
Kind regards

---

### Post by cruzer001 on 2018-02-26
Your right, no drivers installed with the mini iso.  You need to have your ethernet cable plugged in from the start to finish.  

Are you adding any desktop to this?  Ubuntu, Xubuntu, Lubuntu or something else?

> How can i add the driver to my installation stick (USB) and load the driver before i start the installation?

Load it to what?  You have nothing to load a driver to until the mini install is complete.  And then you only have a text screen that will only accept code.

Tell us how you are planning to use this install.

---

### Post by Drenriza on 2018-02-27
> **cruzer001 said:**
> Your right, no drivers installed with the mini iso.  You need to have your ethernet cable plugged in from the start to finish.  

Are you adding any desktop to this?  Ubuntu, Xubuntu, Lubuntu or something else?

Load it to what?  You have nothing to load a driver to until the mini install is complete.  And then you only have a text screen that will only accept code.

Tell us how you are planning to use this install.

I am planning to use i3 as my window manager, and use it as a regular laptop for working,
Eclipse, firefox, git ect.

I would like to use the mini ISO because for me i find the Ubuntu desktop installation to be quite cluttered with fancy graphics and packages that i do not need.

I can't finish the installation because the ISO cannot detect the network hardware, even with the
ethernet cable plugged in from the start.

---

### Post by kerry_s on 2018-02-27
have you tried a live version to make sure your stuff works, before you jumped straight to a net install?

---

### Post by Drenriza on 2018-02-27
> **kerry_s said:**
> have you tried a live version to make sure your stuff works, before you jumped straight to a net install?

I have found out that my first problem was that the UEFI secure boot was messing with the installation.

Afterwards the network device was still not detected so tried manually to load e1000 and e1000e, none of these modules worked.
I looked up that my machine uses Intel I219-V for it's network controller.

Will try and run Ubuntu live CD to make sure the network NIC is functioning as expected

---

### Post by Drenriza on 2018-02-27
The Ubuntu live CD worked without any problems.
After giving interface enp0s31f6 an address and a service restart, the NIC also worked without problems.

After boot i checked the network controllers.
```

lspci|egrep -i --color "network|ethernet"

```
> 
Output
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (4) I219-V (rev 21)
03:00.0 Network controller: Intel Corporation Device 24fd (rev 78)


When looking at the loaded modules
```

sudo lshw -C network

```
> 
Output of interest
logical name: enp0s31f6
configuration: driver=e1000e driverversion=3.2.6-k firmware=0.1-4


Q: Which leads me to the question, why cant the mini ISO detect the NIC when loading the module e1000e manually?
A: ?

Q: Is their a way that i can see the module version used under installation process?
A: Under installation process i execute a shell with command 'modinfo e1000e|grep -i version'
    Which gives the version output of '3.2.6-k'

So the network driver version is the same but the mini ISO still cannot detect the NIC, seeking advice.

---

### Post by kerry_s on 2018-02-27
from what i see -> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
doesn't work with uefi

it points to here-> [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)
for the work around

---

### Post by Drenriza on 2018-02-27
> **kerry_s said:**
> from what i see -> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
doesn't work with uefi

it points to here-> [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)
for the work around

Wont it work if switching the machine into **legacy mode only**?

---

### Post by kerry_s on 2018-02-27
yeap, should work.

---

### Post by cruzer001 on 2018-02-27
> **kerry_s said:**
> from what i see -> doesn't work with uefi

That is correct, you must use the server iso.  It will give you the same results/install as the mini iso, but will handle uefi systems.  At the start of the server install press F4 and choose minimal install.  That will give you a mini iso install and you will find it faster to load than the mini.  All the packages are on the DVD.  I prefer this over the mini just for that :)

PS
When you get to the screen to choose what packages to install choose "manual install".

---

### Post by Drenriza on 2018-02-27
> **kerry_s said:**
> yeap, should work.
Great, did that and tried the install but still it does not recognize the NIC in legacy mode only.

I was here thinking to myself that maybe the problem could be that i dont have a DHCP server on my network,
and it was trying to get a DHCP address failed and gave this error. But after installing a quick DHCP server i still get the error.

_**Something i noticed**_, when i tried to install the Ubuntu desktop in UEFI mode (just to see if i could) the installation said that their was no network connection
over the ethernet cable which was plugged in, but after install it all worked fine.

Is it possible that the installation process load the correct drivers but for some reason cant "jump start" the NIC to establish a network connection?
When i look under /sys/class/net i only see the lo interface, in the terminal under the installation process, can this be the issue?

Brainstorming here.

---

### Post by Drenriza on 2018-02-27
> **cruzer001 said:**
> That is correct, you must use the server iso.  It will give you the same results/install as the mini iso, but will handle uefi systems.  At the start of the server install press F4 and choose minimal install.  That will give you a mini iso install and you will find it faster to load than the mini.  All the packages are on the DVD.  I prefer this over the mini just for that :)

PS
When you get to the screen to choose what packages to install choose "manual install".

Ye i saw this guide on the UEFI mini server install. I dont quite know what makes it a server install but i choose to skip this cause of the cumbersome guide
that goes along with it.

---

### Post by cruzer001 on 2018-02-27
Legacy mode works for me, kerry_s has you covered.  I'm on the side, good luck :)

---

### Post by kerry_s on 2018-02-27
> **Drenriza said:**
> Great, did that and tried the install but still it does not recognize the NIC in legacy mode only.

I was here thinking to myself that maybe the problem could be that i dont have a DHCP server on my network,
and it was trying to get a DHCP address failed and gave this error. But after installing a quick DHCP server i still get the error.

_**Something i noticed**_, when i tried to install the Ubuntu desktop in UEFI mode (just to see if i could) the installation said that their was no network connection
over the ethernet cable which was plugged in, but after install it all worked fine.

Is it possible that the installation process load the correct drivers but for some reason cant "jump start" the NIC to establish a network connection?
When i look under /sys/class/net i only see the lo interface, in the terminal under the installation process, can this be the issue?

Brainstorming here.

just throwing this out there, you sure your wires good? i've had ton's of bad wires, turn out to be the root of many a issues.

---

### Post by Drenriza on 2018-02-27
> **kerry_s said:**
> just throwing this out there, you sure your wires good? i've had ton's of bad wires, turn out to be the root of many a issues.

All the wires and laptop components are working as expected. I went the other way around and installed Ubuntu server 16.04 LTS with UEFI, had no issues and than installed a display manager with more that
i needed. The installation is a bit larger, so i will need to clean out packages that i dont need but now i atleast got past these driver issues for the NIC.

Thanks to all for suggestions and advice.

---

