---
title: "LiveUSB - 3D Unity Works...After Install - No 3D, only 2D...Laptop with Optimus"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by TJet1.8 on 2012-06-18
Hello All,

Got a really strange issue with my Ubuntu 12.04.

When I boot ubuntu with the LiveUSB key, I get perfect Unity 3D graphics with no issues.

After I install Ubuntu, I loose my 3D graphics and it falls back to 2D.

Now....I have a Dell Vostro 3750 with Dual Intel/nVidia graphics controllers (Optimus).
I am well aware of the issues with Linux and Optimus Laptops.
I have had to install bumblebee in order to get 3D on the less efficient Intel Graphics controller.

My question is: Why do the graphics work properly booting the LiveUSB and not after installed on the hard drive??

Is there a way I can tell which graphics controller is active after booting the LiveUSB key?

Thanks All.

:)

---

### Post by fantab on 2012-06-18
Did you install Additional Drivers? It is a Proprietary Drivers issue I think. 

Use in terminal:

lspci

---

### Post by mastablasta on 2012-06-19
> **TJet1.8 said:**
> My question is: Why do the graphics work properly booting the LiveUSB and not after installed on the hard drive??
 
 
i will guess that because on live boot nvidia gets used and their opensource drivers are rather good.

---

### Post by TJet1.8 on 2012-06-19
> **fantab said:**
> Did you install Additional Drivers? It is a Proprietary Drivers issue I think. 

Use in terminal:

lspci

No other drivers installed initially.
I installed bumblebee after the fact just to get my 3D Unity, but I'd rather use stock Ubuntu drivers personally.

Here is my lspci (with bumblebee installed):

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev ff)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
03:00.0 USB controller: Fresco Logic Device 1009 (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

---

### Post by TJet1.8 on 2012-06-19
> **mastablasta said:**
> i will guess that because on live boot nvidia gets used and their opensource drivers are rather good.

Is there a way I can pull them off the LiveUSB key and install on my Laptop???

---

### Post by mastablasta on 2012-06-20
> **TJet1.8 said:**
> Is there a way I can pull them off the LiveUSB key and install on my Laptop???
 
 
they are already installed (in linux drivers are part of kernel - i.e. core)
 
anyway as i read & understand you need to install proprietary nvidia drivers and then you would use bumblebee to do the switching between nvidia and intel. i also knwo that this doens't always work. would suggest you have a look at some good tutorial on how to do it. maybe also someone from here with more experience on optimus will be able to give you a link to a good how to.
 
[http://www.webupd8.org/2012/01/bumblebee-30-released-nvidia-optimus.html](http://www.webupd8.org/2012/01/bumblebee-30-released-nvidia-optimus.html)

---

