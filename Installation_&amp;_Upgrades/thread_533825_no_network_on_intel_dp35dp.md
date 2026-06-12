---
title: "no network on intel dp35dp"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by fast orange on 2007-08-24
I installed the 64 bit version of 7.04 on my desktop with my intel dp35dp motherboard, and I seem to have no network driver.  I found it listed on the desktop hardware incompatibility list: 
"1)Type Of Hardware : Integrated network card.
2)Hardware Maker : Intel
3)Hardware Model : Intel® 82566DC Gigabit Ethernet Controller integrated into DP35DP
4)Known Issue : Ubuntu 7.04 (64 bit) installs, but network card is not installed"

also here is my output for lspci, it looks like some other things are missing:
00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:01.0 PCI bridge: Intel Corporation Unknown device 29c1 (rev 02)
00:03.0 Communication controller: Intel Corporation Unknown device 29c4 (rev 02)
00:19.0 Ethernet controller: Intel Corporation Unknown device 294c (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 02)
00:1c.1 PCI bridge: Intel Corporation Unknown device 2942 (rev 02)
00:1c.2 PCI bridge: Intel Corporation Unknown device 2944 (rev 02)
00:1c.3 PCI bridge: Intel Corporation Unknown device 2946 (rev 02)
00:1c.4 PCI bridge: Intel Corporation Unknown device 2948 (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2916 (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0421 (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)



Help setting up this up would be appreciated, also do you see other errors in the lspci?

---

### Post by fast orange on 2007-08-24
Figured it out! downloaded the Intel® 82566 Gigabit Ethernet PHY driver from intel's site.

---

### Post by espi3d on 2007-08-28
I have a DP35DP too, and tried to install Ubuntu 7.04 (64 bits) but I cant get my keyboard to work what keyboard do you have? Did you have any issues related to this? if so, how did you make it work?
 Thanks

---

### Post by gertmul on 2007-08-29
I installed Gutsy Gibbon 7.10 (downloaded 2007-08-07) and the network device worked fine, however, after enabling the nVidia Quadro FX 350 in proprietary devices, the network device stopped working.

lspci
00:19:0 Ethernet controller: Intel Corporation Unknown device 294c (rev 02)

and most of the other Intel device also unknown...not that I know what they were before the change.

I downloaded the Intel PHY driver, as suggested, but trying to compile it complains about "missing kernel source"...Is there an easier way to get this driver installed other than downloading the kernel sources?

Thank you

---

### Post by gertmul on 2007-08-29
A little more information:

When you boot live from the cd (Gutsy), the device is still shown as "Intel Corp Unknown device" when looking at lspci

But I've noted that ```
lsmod | grep e1000
``` says:

e1000_ich9     188736   0

So after some trouble compiling the Intel PHY driver from the web and insmod, the new result by running Gutsy from the installed hard drive, with ```
lsmod | grep e1000
```

e1000     124480   0

but still no "eth0", et0: ERROR xxx : No such device

To build the drivers I used
[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)
and the README in the src folder of the e1000 driver.

---

### Post by espi3d on 2007-09-05
what is your keyboard brand/model?
mine doesnt work

---

### Post by FrozenFlame22 on 2007-09-12
I am having the same problem as the original poster, and I can't get the driver that he specified to finish installing nor can I access the internet.

To recap: I just this evening built a computer using an Intel DP35DP motherboard. We attempted to install the driver for the onboard ethernet (Intel® 82566 Gigabit Ethernet PHY) while logged in as root and I get an error saying: "Cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode" The install always stops there.

Even after doing this, we are able to ping our other computer on the network and receive pings from the new Ubuntu computer from the other computer. We can also access the router settings and the modem settings pages from the new Ubuntu computer. However, we cannot access the internet at all. We've tried with static and dynamic IPs, all firewalls on the router and modem are off. We're reasonably certain that the router and modem are configured properly.

I find this frustrating because if we can ping each other, we should be able to reach the net. :confused:

---

### Post by fast orange on 2007-09-14
sorry I ignored you guys, I'll look up what I did and post it for you.

---

### Post by fast orange on 2007-09-14
I downloaded "e1000-7.6.5.tar.gz" from intel's site.  Here it is:
[http://downloadcenter.intel.com/Detail_Desc.aspx?strState=LIVE&ProductID=983&DwnldID=9180&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?strState=LIVE&ProductID=983&DwnldID=9180&lang=eng")

I followed the install in the readme with no troubles.
Note that #5 says:
5. Load the module using either the insmod or modprobe command:

     modprobe e1000

     insmod e1000

modprobe worked for me, right away too.  Though you could always do a restart if you don't see activity.  
Keep the package around, I accidentally updated over it once.

---

### Post by fast orange on 2007-09-14
In regards to the keyboard, I'm on a wireless logitech, I have no idea how an ethernet install could have affected that.

---

### Post by FrozenFlame22 on 2007-09-23
Sorry for the late reply!

I did get it working eventually. Here's how I did it:
[http://ubuntuforums.org/showthread.php?t=549510](http://ubuntuforums.org/showthread.php?t=549510)

---

