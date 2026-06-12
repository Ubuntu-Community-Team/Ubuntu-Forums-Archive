---
title: "After update from 18.04 to 2004 Kaffeine will no longer display Digital TV"
date: 2021-04-07
forum: Installation &amp; Upgrades
---

### Post by adrian-h on 2021-04-07
I am on a rather old PC with a quite old graphics card, but I hope someone can help

I have Kaffeine installed and this worked well in Ubuntu 18.04 generally used for watching the odd bit of TV using a SDR-RTL USB stick.  I have done an upgrade to 20.0.2 LTS and now the Digital TV picture is like the image below.

I can still view mp4 files OK so I can only guess something has not come across in the upgrade.  I have installed ubuntu-restricted-extras and wonder if anyone can suggest what could be causing the problem.[ATTACH=CONFIG]288230[/ATTACH]

Cheers

Adrian

---

### Post by adrian-h on 2021-04-07
Well this looks like something is no longer supported with Ubuntu 20.04 such as my old video card which according to lspci is a : -
VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 7350/8350 / R5 220]

There may be drivers I can still get and will continue to look for them as all was OK in 18.04.  I have another computer on Ubuntu 20.04 which I installed Kaffeine on and it runs OK, but does have a NVIDIA NVS 510 fitted which is why I am thinking this at present.

Adrian

---

### Post by adrian-h on 2021-04-07
I continue to play with lots of web searching and dead ends, not sure if I have got anywhere really.

I found some comments elsewhere about the 5.8 Kernels and AMD drivers.

The system had initially installed a Radeon driver.  With this the PC could at least detect my monitor and set it to be 1600x900 resolution even though it would not do everything properly.  The final posts for tonight I found sent me to AMD, downloading 'amdgpu-pro-20.50-1234664-ubuntu-20.04' and installing that.

I had previously tried version 20.20 but that would not compile.  Well 20.50 went through the process all OK and installed a kernel module.  after a reboot things changed a bit.

The monitor is no longer recognised and ends up with a resolution of 1152x864, so from 16:9 to 4:3.  But the TV section of Kaffeine now works, so I guess some part of it is working.

A last try at using the line in grub 

GRUB_GFXMODE=1600x900 does not make any difference It will not go above 1152x864 in use.

I wish I knew what I was doing!

Adrian

---

### Post by CelticWarrior on 2021-04-07
If your card is running with the radeon driver then you CAN'T install the proprietary amdgpu-pro. If you have a new card supported by the open-source amdgpu then you can try - for no good reason outside of very specific professional usages - the proprietary overlay.

---

### Post by adrian-h on 2021-04-08
Sorry for delay I am not getting alerts.

CelticWarrior can you please explain a bit more what you mean for me, why I can not try the amd driver.  Within the package there are two install scripts amdgpu-install and amdgpu-pro-install I am actually running the  the first and it installs OK and the site says it supports the card I have?
There was still issues as I mentioned one being that
sudo lshw -c video

Reported that it was an unsupported monitor and no driver, but it gave the correct display to the TV application where as back at the radeon driver to 
sudo lshw -c video
I get a better response

*-display                 
       description: VGA compatible controller
       product: Cedar [Radeon HD 7350/8350 / R5 220]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:35 memory:e0000000-efffffff memory:f7de0000-f7dfffff ioport:dc00(size=256) memory:c0000-dffff

I have at the moment uninstalled it all anyway so I am back with the Radeon driver

I also tried the information from this site [https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation](https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation)
which is basically 
1)   Leave it as it is
2)   A PPA third party repository which I tried and,
3)   The AMD Radeon drivers which installs but does not work properly.

 I am considering putting the PC back to 18.04 and leaving it down there at least it all worked.  the PC is getting old i appreciate that, it's just like me.

Adrian

---

### Post by CelticWarrior on 2021-04-08
Drivers for all AMD cards are always already installed automatically since AMD opted in for the open source model many years ago. No user action required.

Old cards use radeon.
New cards use amdgpu.
The selection is done by the installer/system automatically.

Cards using radeon have no other options. There's a PPA to supposedly update to slightly newer versions of Radeon/Mesa but seldom there's a reason to do that and it may break the system at a later date. Benefits for the end users are still to be proven.

Cards using amdgpu can alternative use amdgpu-pro, the AMD proprietary layer. End users outside of very specific professional usages have no benefits from it, often the opposite.

It's funny that you're asking why you can't install the proprietary driver from AMD after you broke your system but OK...
The fact is your problem may well be related with the newer radeon version in 20.04 but can have totally different causes including the newer version of the software you're using rather than the drivers. Regarding the graphics drivers, again, there's NOTHING you can do about it, it either works or it doesn't. You may try 18.04 in a live session to see if the problem is now the same or not. If it works there you may install it and keep until 2023. If the problem is the same then preferably reinstall 20.04, supported until 2025, and troubleshoot from there. In any case do NOT try to install anything else graphics driver related.

---

### Post by adrian-h on 2021-04-08
I actually got a notification.

OK so I can now follow that Radeon = old gear and AMD newer gear and it is all open source.  So my Radion is old and outdated, well I could guess that thanks for a bit more detail.  I can use it for generating old 405 line TV format which is why I use the old card, the newer ones past a certain point will not go that slow!

I actually thought my system was broken after the upgrade because it would not run Kaffeine correctly, and it did under version 18.04, hence why I tried the different drivers. When I did try the AMD, Kaffeine worked but with a lower monitor resolution.

I am just confused about upgrading but things then not working I guess, but better than Windows or this PC would have to be in the bin some time ago.

I have started the process of going back to what I had which was version 18.04 LTS and leave it at that for the next few years, then it can probably go to landfill anyway.

Thanks for clearing a few things with me I will make this thread as closed/solved.

Adrian

---

### Post by adrian-h on 2021-04-10
just to finish the thread off.

I took the computer back to 18.04.5 and all is OK once again.  Kaffeine TV pictures display OK, the resolution is OK at 1600x900 and everything appears to work OK.

Adrian

---

