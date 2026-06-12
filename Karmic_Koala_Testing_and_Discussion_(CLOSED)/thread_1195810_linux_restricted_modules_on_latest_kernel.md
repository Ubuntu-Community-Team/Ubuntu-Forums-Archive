---
title: "linux restricted modules on latest kernel"
date: 2009-06-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-06-24
i am using the hp mini 2133, the first model, and i depend on the restricted modules for my wireless..

why dont we have the restricted modules for the 2.6.30 kernel line?
any reason for this?

i can see the source for the 2.6.28-12 kernel, can i compile it for the 2.6.30 and if so, how do i do it?

---

### Post by taavikko on 2009-06-24
Most of the wireless drivers are included in the kernel, 
so no need for the "restricted" package.

If it is atheros chipset it should work o-o-t-b, without enabling restricted drivers...

And if I remember correctly, dkms is going to replace "restricted-modules" method altogether...

---

### Post by bcat on 2009-06-24
Yeah, DKMS has replaced LRM for Broadcom cards. "sudo apt-get install bcmwl-kernel-source".

---

### Post by puccaso on 2009-06-25
sorted! wokrs like a charm :D


now all i need to fix is the grahpics..

---

### Post by FarJumper on 2009-06-26
But what about DRI kernel drivers for NVIDIA/ATI proprietary blobs? fglrx 8.620 was uploaded recently but it's unusable without its kernel module.

---

### Post by FarJumper on 2009-06-26
Probably I'm doing something wrong. It looks that DKMS compiled out all necessary modules, but the module is not loading in the boot time, thus my X still have no acceleration:

(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


$ dkms status
fglrx, 8.620, 2.6.30-10-generic, i686: installed 
fglrx, 8.620, 2.6.28-11-generic, i686: installed 
fglrx, 8.620, 2.6.30-9-generic, i686: installed 
vboxdrv, 2.2.4, 2.6.30-10-generic, i686: installed 
vboxdrv, 2.2.4, 2.6.28-11-generic, i686: installed 
vboxdrv, 2.2.4, 2.6.30-9-generic, i686: installed 
vboxnetflt, 2.2.4, 2.6.30-10-generic, i686: installed 
vboxnetflt, 2.2.4, 2.6.28-11-generic, i686: installed 
vboxnetflt, 2.2.4, 2.6.30-9-generic, i686: installed 

$ lsmod |grep gl
$

---

### Post by lithorus on 2009-06-26
> **FarJumper said:**
> Probably I'm doing something wrong. It looks that DKMS compiled out all necessary modules, but the module is not loading in the boot time, thus my X still have no acceleration:

(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


$ dkms status
fglrx, 8.620, 2.6.30-10-generic, i686: installed 
fglrx, 8.620, 2.6.28-11-generic, i686: installed 
fglrx, 8.620, 2.6.30-9-generic, i686: installed 
vboxdrv, 2.2.4, 2.6.30-10-generic, i686: installed 
vboxdrv, 2.2.4, 2.6.28-11-generic, i686: installed 
vboxdrv, 2.2.4, 2.6.30-9-generic, i686: installed 
vboxnetflt, 2.2.4, 2.6.30-10-generic, i686: installed 
vboxnetflt, 2.2.4, 2.6.28-11-generic, i686: installed 
vboxnetflt, 2.2.4, 2.6.30-9-generic, i686: installed 

$ lsmod |grep gl
$
Have you tried loading the module manually? You can also add the modulename to /etc/modules to get it startup automatically.

---

### Post by FarJumper on 2009-06-30
I tried to load fglrx module manually and it fails:

$ sudo modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.30-10-generic/updates/dkms/fglrx.ko): Unknown symbol in module, or unknown parameter (see dmesg)

$ dmesg|tail -n 2
[19837.157542] udev: starting version 144
[20687.201647] fglrx: Unknown symbol flush_tlb_page

---

### Post by jfanaian on 2009-06-30
I am having the exact same issue with my fglrx drivers. If I try to load the fglrx module manually it will give me the same error FarJumper reported. Is there anything else I can try to fix acceleration? I was hoping the updates from today would fix the issue, but I had no such luck.

Thanks.

EDIT:
I wanted to include some of my Xorg log, where the DRI failure is noted, because it is mentioning that it can't query the X.org version.

```

21971-(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
22032-(WW) fglrx(0): could not detect X server version (query_status=-1)
22099-(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
22169-(WW) fglrx(0): ***********************************************
22232:(WW) fglrx(0): * DRI initialization failed!                  *
22295-(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
22358-(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
22421-(WW) fglrx(0): * no 3D acceleration available                *
22484-(WW) fglrx(0): ********************************************* *

```

---

### Post by lithorus on 2009-06-30
> **jfanaian said:**
> I am having the exact same issue with my fglrx drivers. If I try to load the fglrx module manually it will give me the same error FarJumper reported. Is there anything else I can try to fix acceleration? I was hoping the updates from today would fix the issue, but I had no such luck.

Thanks.

EDIT:
I wanted to include some of my Xorg log, where the DRI failure is noted, because it is mentioning that it can't query the X.org version.

```

21971-(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
22032-(WW) fglrx(0): could not detect X server version (query_status=-1)
22099-(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
22169-(WW) fglrx(0): ***********************************************
22232:(WW) fglrx(0): * DRI initialization failed!                  *
22295-(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
22358-(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
22421-(WW) fglrx(0): * no 3D acceleration available                *
22484-(WW) fglrx(0): ********************************************* *

```
Which version of fglrx have you installed?
See [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/387773](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/387773)

---

### Post by jfanaian on 2009-06-30
> **lithorus said:**
> Which version of fglrx have you installed?
See [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/387773](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/387773)

I'm running version 2:8.620-0ubuntu2 which is the one that is supposed to have the fix in that bug report :(.

Also, I have no issues installing the module. I installed it through the Hardware Drivers app without problems. The app now says "This driver is activated but not currently in use." and shows a green bubble next to the driver.

---

### Post by FarJumper on 2009-07-01
Filled bug report. Please comment.
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/394176](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/394176)

---

### Post by DougieFresh4U on 2009-07-01
> **jfanaian said:**
> I'm running version 2:8.620-0ubuntu2 which is the one that is supposed to have the fix in that bug report :(.

Also, I have no issues installing the module. I installed it through the Hardware Drivers app without problems. The app now says "This driver is activated but not currently in use." and shows a green bubble next to the driver.

Had the same issue, where 'Hard ware Drivers' is stating 'activated but not currently in use'.
Also while it was 'activated', some thing was causing horrible scrolling in all browsers but once I 'removed' driver all returned to normal

---

