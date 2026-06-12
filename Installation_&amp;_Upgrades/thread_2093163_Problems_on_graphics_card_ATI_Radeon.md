---
title: "Problems on graphics card ATI Radeon"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by towenyu on 2012-12-10
I'v been struggling many days for the display issue on my system(PowerPC based) with ATI Radeon Graphics card. Much appreciation if anyone can help me out or guide me how to solve the problem.

Here's more details:

My system is Ubuntu 12.04.
My kernel is compiled on 3.4.20, tried different options related to graphics support ( like DRM, framebuffer, etc, but with all possibilities tried out, the results the same)


lspci will give below results:

0001:01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV380 [Radeon X600 (PCIE)]
0001:01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV380 [Radeon X600]

dmesg will got below results:

udevd[1108]: starting version 175
170 Adding 3951984k swap on /dev/sda2.  Priority:-1 extents:1 across:3951984k
171 EXT3-fs (sda3): using internal journal
172 init: udev-fallback-graphics main process (1990) terminated with status 1
173 init: plymouth main process (1055) killed by SEGV signal
174 init: plymouth-splash main process (1993) terminated with status 2
175 init: plymouth-log main process (2009) terminated with status 1

My xorg.conf file and Xorg.0.log is attached as well, along with a complete dmesg log file.

In brief, Xorg is fail to find any device/screen to start.


I really get crazy on this problem. Please help me.

---

### Post by towenyu on 2012-12-10
I'm sorry but I failed to upload attachments. Try it again here.

log for dmesg: [ATTACH]228482[/ATTACH]

log for Xorg.0.log: [ATTACH]228483[/ATTACH][ATTACH]228484[/ATTACH]

xorg.conf :  [ATTACH]228485[/ATTACH]

---

### Post by Mark Phelps on 2012-12-10
Are you trying to install the AMD drivers? Or are you having problems getting the default Radeon drivers working?

Asking because there are no AMD Linux drivers that will work work with your card and any Ubuntu version later than 8.10.

The default open-source Radeon drivers, however, should work OK.

---

### Post by towenyu on 2012-12-11
> **Mark Phelps said:**
> Are you trying to install the AMD drivers? Or are you having problems getting the default Radeon drivers working?

Asking because there are no AMD Linux drivers that will work work with your card and any Ubuntu version later than 8.10.

The default open-source Radeon drivers, however, should work OK.


Thanks Mark. 

First in the kernel compiling, I enabled "DRM" and ATI RADEON support under its catalog.
And, I installed Xserver-xorg-video-ati package from Ubuntu. 

I'm not sure what's the exact "default open-source Radeon drivers " you are mentioning. And how can I enable it? 

I managed to find a tarball from xorg named xf86-video-ati-6.14.0 ( I try not to use the latest version ). Is this the default open-source driver? 

Best Regards,
Wenyu

---

### Post by Mark Phelps on 2012-12-11
Sorry, I missed that you are compiling your own kernel ...

The default Radeon drivers are installed automatically when you install Ubuntu, after it does its device polling and discovers that you have a Radeon card/chipset.

Since I don't compile my own kernels, I don't deal with which packages need to be incorporated ... but I think the one you named is the correct one.

Understand, though, that the latest X-server version that will work with ATI drivers that work with your card was the one used in Ubuntu 8.10.  So, you will need to use that version, not anything newer.

A very good source to check for such technical details is the Phoronix forums.  They do a lot of testing with Radeon code and can probably answer your question.

---

### Post by towenyu on 2012-12-12
[QUOTE=Mark Phelps;12399080]

Thanks Mark, for your great help. 

I will try to find some clues from the forum you recommended.

---

