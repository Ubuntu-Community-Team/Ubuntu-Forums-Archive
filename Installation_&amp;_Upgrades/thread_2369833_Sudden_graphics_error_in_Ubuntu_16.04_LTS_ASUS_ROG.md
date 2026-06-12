---
title: "Sudden graphics error in Ubuntu 16.04 LTS ASUS ROG laptop"
date: 2017-08-27
forum: Installation &amp; Upgrades
---

### Post by chsriram on 2017-08-27
Using Ubuntu 16.04 LTS, most probably after an upgrade, the initial graphics of my ASUS ROG laptop is not working. I have attached a snapshot of what I see and would be happy to provide more information.. Please help resolve as my work with a raspberry pi3 and some other hardware is held up.

---

### Post by ubfan1 on 2017-08-27
Do you have proprietary video hardware like Nvidia?  Can you run in safe mode (a grub menu choice)?  Can you successfully run an older kernel (at the grub prompt, select "advanced options" and select the former kernel?

---

### Post by chsriram on 2017-08-29
Yes it has Nvidia GEFORCE GTX 960m video hardware. I ran an older kernel. Still same result.

---

### Post by Bashing-om on 2017-08-29
chsriram; Hello;

Broken proprietary graphic's driver ?
At the login screen key combo ctl+alt+F1 to gain a console interface. Log in here with username and password .
Post back:
```

sudo lshw -C

```

See if a driver is loaded .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by chsriram on 2017-09-01
This might be a naive question but

---

### Post by Bashing-om on 2017-09-01
chsriram;chsriram; Hey;

> 
This might be a naive question but


Ask; here the only dumb questions are the ones not asked .
-here to help-

---

### Post by chsriram on 2017-09-09
lshw -C is just displaying help for the command. Here are the dmesg ! grep nvidia messages: 
[IMG]mtp://[usb:001,014]/Internal%20storage/DCIM/Camera/P_20170909_114654.jpg[/IMG]

---

### Post by chsriram on 2017-09-09
lshw -C is just displaying help for the command. How can I post an image of the dmesg from my Android phone? The insert image option is only allowing me to post a link and I dont know if mtp link actually uploads an image.

---

### Post by Bashing-om on 2017-09-09
chsriram; Ouch !
Incomplete thought on my part !

Make that lshw command as :
```

sudo lshw -C display

```
(edited above with the correction ) 
The command now works ?

As to :
> 
 How can I post an image of the dmesg from my Android phone? 


I can not advise in that respect as I do not have the experience . Others here will fill in on my gap . 


Still, want to know what the graphis situation may be.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by chsriram on 2017-09-12
*-display 
   description: 3d controller
   product: GM107M [GEForce GTX 960m]
   vendor: NVIDIA Corporation
   physical id: 0
   bus info: pic@0000:01:00.0
   version: a2
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress bus_master cap_list rom
   configuration: driver=nvidia latency=0
   resources: irq:16 memory: de000000-deffffff .....
This is a bit of a work emergency and I need to get a fix soon. Is there a maintenance or tech support vendor I can send the laptop to get it fixed?

---

### Post by Bashing-om on 2017-09-12
chsriram.; Well.

A driver is loaded :
```

dpkg -l | grep linux- 

```
to tell what driver and it's install state.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by chsriram on 2017-10-12
```
dpkg  -l | grep linux-
ii  linux-base                                                       4.0ubuntu1                                                all          Linux image base package
iF  linux-firmware                                                   1.157.12                                                  all          Firmware for Linux kernel drivers
iU  linux-generic                                                    4.4.0.96.101                                              amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-83                                           4.4.0-83.106                                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-83-generic                                   4.4.0-83.106                                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-87                                           4.4.0-87.110                                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-87-generic                                   4.4.0-87.110                                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-89                                           4.4.0-89.112                                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-89-generic                                   4.4.0-89.112                                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-91                                           4.4.0-91.114                                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-91-generic                                   4.4.0-91.114                                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-92                                           4.4.0-92.115                                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-92-generic                                   4.4.0-92.115                                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-96                                           4.4.0-96.119                                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-96-generic                                   4.4.0-96.119                                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.2-040402                                       4.4.2-040402.201602171633                                 all          Header files related to Linux kernel version 4.4.2
ii  linux-headers-4.4.2-040402-generic                               4.4.2-040402.201602171633                                 amd64        Linux kernel headers for version 4.4.2 on 64 bit x86 SMP
ii  linux-headers-4.4.3-040403                                       4.4.3-040403.201602251634                                 all          Header files related to Linux kernel version 4.4.3
ii  linux-headers-4.4.3-040403-generic                               4.4.3-040403.201602251634                                 amd64        Linux kernel headers for version 4.4.3 on 64 bit x86 SMP
ii  linux-headers-generic                                            4.4.0.96.101                                              amd64        Generic Linux kernel headers
iF  linux-image-4.4.0-83-generic                                     4.4.0-83.106                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-87-generic                                     4.4.0-87.110                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-89-generic                                     4.4.0-89.112                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-91-generic                                     4.4.0-91.114                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-92-generic                                     4.4.0-92.115                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-96-generic                                     4.4.0-96.119                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.2-040402-generic                                 4.4.2-040402.201602171633                                 amd64        Linux kernel image for version 4.4.2 on 64 bit x86 SMP
ii  linux-image-4.4.3-040403-generic                                 4.4.3-040403.201602251634                                 amd64        Linux kernel image for version 4.4.3 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-83-generic                               4.4.0-83.106                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-87-generic                               4.4.0-87.110                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-89-generic                               4.4.0-89.112                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-91-generic                               4.4.0-91.114                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-92-generic                               4.4.0-92.115                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-96-generic                               4.4.0-96.119                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                                              4.4.0.96.101                                              amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                             4.4.0-97.120                                              amd64        Linux Kernel Headers for development
iU  linux-signed-generic                                             4.4.0.96.101                                              amd64        Complete Signed Generic Linux kernel and headers
iU  linux-signed-image-4.4.0-83-generic                              4.4.0-83.106                                              amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-87-generic                              4.4.0-87.110                                              amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-89-generic                              4.4.0-89.112                                              amd64        Signed kernel image generic
iU  linux-signed-image-4.4.0-91-generic                              4.4.0-91.114                                              amd64        Signed kernel image generic
iU  linux-signed-image-4.4.0-92-generic                              4.4.0-92.115                                              amd64        Signed kernel image generic
iU  linux-signed-image-4.4.0-96-generic                              4.4.0-96.119                                              amd64        Signed kernel image generic
iU  linux-signed-image-generic                                       4.4.0.96.101                                              amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                                 1.0.25+dfsg-0ubuntu5                                      all          base package for ALSA and OSS sound systems
ii  syslinux-common                                                  3:6.03+dfsg-11ubuntu1                                     all          collection of bootloaders (common)
ii  syslinux-legacy                                                  2:3.63+dfsg-2ubuntu8                                      amd64        Bootloader for Linux/i386 using MS-DOS floppies

/
```

---

### Post by Bashing-om on 2017-10-12
chsriram; Hey ...

But put between code tags please - helps much to maintain formatting so we ca read:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Ouch ! Let's see what we can do to get this system cleaned up and the kernel fully installed :
> 
iU linux-generic 4.4.0.96.101 amd64 Complete Generic Linux kernel and headers

Where the "iU" is desired= installed, U= Unpacked but NOT installed.

We start this process with:
```

sudo apt autoremove

```
See what the system screams and hollers about, then take remedial action per that response.

Once the kernel is fully installed - then we can go back to working the graphics.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

