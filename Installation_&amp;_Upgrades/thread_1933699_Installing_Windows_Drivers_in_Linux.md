---
title: "Installing Windows Drivers in Linux"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by HoneyBadger1 on 2012-02-29
Guys I have an HP 300-1020, I recently installed Ubuntu 10.04
I went to the HP website here:

[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=4063&lc=en&cc=us&dlc=en&sw_lang=&product=4007375#N317](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=4063&lc=en&cc=us&dlc=en&sw_lang=&product=4007375#N317)

I downloaded all the original drivers, but they were made for Windows 7.
How do I install them in Linux?

---

### Post by grahammechanical on 2012-02-29
Why do you want to install drivers for another operating system on Ubuntu?

What do you think that you need then for?

Regards.

---

### Post by HoneyBadger1 on 2012-02-29
> **grahammechanical said:**
> Why do you want to install drivers for another operating system on Ubuntu?

What do you think that you need then for?

Regards.

My speakers no longer work, my microphone also does not work, and my wireless card does not get detected.

I think it is because after I autonuked my hardrive, all the HP drivers got deleted.
I was running Windows 7 previously, but after autonuking my hardrive decided to switch to Ubuntu 10.04 instead.

---

### Post by ottosykora on 2012-03-01
windows drivers can not be used directly, but some can be used with a workaround, try:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Bucky Ball on 2012-03-01
> **ottosykora said:**
> windows drivers can not be used directly, but some can be used with a workaround, try:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Not a good plan. Ndiswrapper for wireless = AVOID! It is superseded for most wireless cards and unnecessary (and generally a nightmare).

HoneyBadger1: Open a terminal (Applications>Accessories>Terminal) and paste this in:
```

sudo lspci
```Post the result back here and that will tell us what you have in there.

BUT FIRST: Plug in an ethernet cable, get online, and get all updates (System>Administration>Update Manager if you are not automatically offered updates) then check System>Adminstration>Additional Drivers (could be Hardware Drivers). Is there a driver for your wireless card in there disabled or have you been offered one by the update???

---

### Post by mastablasta on 2012-03-01
also drivers inlinux are part of kernel. so newer version of the OS (latest stable is 11.10) would more likely have all drivers that you need.

---

### Post by HoneyBadger1 on 2012-03-01
> **Bucky Ball said:**
> Not a good plan. Ndiswrapper for wireless = AVOID! It is superseded for most wireless cards and unnecessary (and generally a nightmare).

HoneyBadger1: Open a terminal (Applications>Accessories>Terminal) and paste this in:
```

sudo lspci
```Post the result back here and that will tell us what you have in there.

BUT FIRST: Plug in an ethernet cable, get online, and get all updates (System>Administration>Update Manager if you are not automatically offered updates) then check System>Adminstration>Additional Drivers (could be Hardware Drivers). Is there a driver for your wireless card in there disabled or have you been offered one by the update???

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Network controller: RaLink RT3092 Wireless 802.11n 2T/2R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```

---

### Post by HoneyBadger1 on 2012-03-01
> **mastablasta said:**
> also drivers inlinux are part of kernel. so newer version of the OS (latest stable is 11.10) would more likely have all drivers that you need.


Yeah my brother is running Linux 11.10 and did not have these problems...
But that is the thing, I am had Linux 11.10 to before I installed 10.04(I didn't like the new layout of 11)
and I still didn't have sound.....I think it's because I am using a HP Touchsmart and he has a normal laptop.

---

### Post by HoneyBadger1 on 2012-03-01
I gave up, I went back to Windows 7. I am running Ubuntu inside VirtualBox.

---

### Post by mastablasta on 2012-03-01
that's strange this one: 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

should work ok. also as you can see it recognises the device.

maybe the volume is only muted. try typing 

alsamixer 

in terminal when it opens check that you have all volumes up to maxmium.

want old layout with new kernel try Xubuntu. it's faster anyway. :-O ;-)

---

### Post by MAFoElffen on 2012-03-01
> **mastablasta said:**
> that's strange this one: 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

should work ok. also as you can see it recognises the device.

maybe the volume is only muted. try typing 

alsamixer 

in terminal when it opens check that you have all volumes up to maxmium.

want old layout with new kernel try Xubuntu. it's faster anyway. :-O ;-)
Goog catch. 10.04 had sound muted as a default.

On returned PCI data: Intel HDA chipset, uses ALSA "snd-card-hda-intel" driver.

There is a script /user/src/sbin/alsa that loads ALSA and it's drivers at boot --AND-- displays whether pass or fail... Did you notice what it said? After boot <Cntrl><Alt><F1> will show those boot messages. <Shift><PageUp> and <Shift><PageDown> will let you scroll the messages to review.

I know that when we were testing in the dev-cycle from 10.04 to 10.10... there were a number of drivers added to ALSA. A few more between 10.10 and 11.04.  Can't remember which those were.

Here is your wireless driver:
[https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090")

---

### Post by HoneyBadger1 on 2012-03-01
I reinstalled Windows 7, and installed Ubuntu inside VirtualBox. All the problems went away, my Ubuntu running inside VirtualBox has sound, camera, microphone etc.
I guess it had problems finding the right drivers when it was the main operating system, but with Windows 7 running in the background it had no problems running anymore.

Still it would have been nice for it to be the other way around though: 
Ubuntu > Windows 7 Virtual.......not Windows 7 > Ubuntu Virtual

But it's ok, I am running Ubuntu with a full screen inside VirtualBox:
[http://www.youtube.com/watch?v=jGlCdxKx0gI&list=FLAB1Dh8q0J3E4eVUDraOQfw&index=2&feature=plpp_video](http://www.youtube.com/watch?v=jGlCdxKx0gI&list=FLAB1Dh8q0J3E4eVUDraOQfw&index=2&feature=plpp_video)

---

### Post by MAFoElffen on 2012-03-02
> **HoneyBadger1 said:**
> I reinstalled Windows 7, and installed Ubuntu inside VirtualBox. All the problems went away, my Ubuntu running inside VirtualBox has sound, camera, microphone etc.
I guess it had problems finding the right drivers when it was the main operating system, but with Windows 7 running in the background it had no problems running anymore.

Still it would have been nice for it to be the other way around though: 
Ubuntu > Windows 7 Virtual.......not Windows 7 > Ubuntu Virtual

But it's ok, I am running Ubuntu with a full screen inside VirtualBox:
[http://www.youtube.com/watch?v=jGlCdxKx0gI&list=FLAB1Dh8q0J3E4eVUDraOQfw&index=2&feature=plpp_video](http://www.youtube.com/watch?v=jGlCdxKx0gI&list=FLAB1Dh8q0J3E4eVUDraOQfw&index=2&feature=plpp_video)
That is because the VirtualBox'es Virtual Machine is presenting any OS installing in it ID as generic hardware (so that any OS will have drivers for it) and translates it to the Host's devices. For instance, it goes through the hosts audio, whatever it is, but looks to the client OS as an ICH AC97. I think if you installed a newer version of Ubuntu, the sound would be there.  

The wifi driver is still going to be a manual install after the initial install. It's not common, but there is drivers available.  Unlike when I started, the NIC driver for this box I had to compile from source... More devices are supported now... and in more of a user friendly format.

---

### Post by mastablasta on 2012-03-02
VirtualBox is a nice option (i have it on the XP maschine). but it doesn't really compare to the propper install. especially in the boot speed and such :-)

---

