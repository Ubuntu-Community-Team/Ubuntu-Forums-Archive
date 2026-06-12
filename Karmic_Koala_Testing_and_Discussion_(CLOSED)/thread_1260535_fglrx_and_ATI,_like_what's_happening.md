---
title: "fglrx and ATI, like what's happening?"
date: 2009-09-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-09-07
Finally, I can use my ATI Radeon HD3200! I am using 'fglrx' on my Jaunty install (.28 kernel) Nothing newer has worked until .31.9 kernel.  Running Karmic 64 bit with the 'fglrx' Hardware Driver and over all my machine is being more responsive. Compiz running great.
Any one else enjoying this?

---

### Post by patasenko on 2009-09-07
Yes same here, much more frust power from my Mobility Radeon HD 2600. I even don't have Jaunty on my laptop. However there is still a long way to go, as Windows (yes sadly) have better performance.
The main reason, i can watch 1080p movie without any glitches, but in Linux, it just does not cut it. 
Maybe it has something to do with newer kernel?

---

### Post by jwssr on 2009-09-07
magic....

I too have ati 3200 plus azalia digital sound..I found a post elsewhere sat 5th about new drivers...alas  it worked...but more importantly for me....my digital sound thru hdmi came back on...with vigor...

I have a post about pulseaudio coming up..hope it is helpful..  PulseAudio Magic          it is related to ati drivers.

glad to see these positive post showing up....

---

### Post by JCoster on 2009-09-07
Just so I'm sure, the fglrx driver is the one installed through Restricted Drivers yeah?

I'm experiencing maximise/restore lag on it at the moment with my HD3650.

---

### Post by JCoster on 2009-09-07
please delete; hit post twice.

---

### Post by Sophont on 2009-09-07
Does anybody have **Mobility** Radeon **4670** working with fglrx?

The (non-Mobility) 4670 is listed on the official side, but under the Mobility Radeons 4670 is not listed  - which seems to be weird as the 2 variants seem to be very closely related according to Wikipedia.

---

### Post by alphacrucis2 on 2009-09-07
I thought we had to wait till ATI release a Catalyst version that works with the 2.6.31 series kernels?

---

### Post by DougieFresh4U on 2009-09-07
> **alphacrucis2 said:**
> I thought we had to wait till ATI release a Catalyst version that works with the 2.6.31 series kernels?

There is the new Catalyst that works with .31.9 generic

---

### Post by alphacrucis2 on 2009-09-07
Not according to Phoronix. The latest Catalyst 9.8 is said to support 2.6.29 & 2.6.30.

[http://www.phoronix.com/scan.php?page=news_item&px=NzQ2Mw]("http://www.phoronix.com/scan.php?page=news_item&px=NzQ2Mw")

---

### Post by Reiger on 2009-09-07
But Ubuntu gets: [http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA](http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA) (Catalyst 9.10)

---

### Post by alphacrucis2 on 2009-09-08
> **Reiger said:**
> But Ubuntu gets: [http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA](http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA) (Catalyst 9.10)

Cool!

---

### Post by Longinus00 on 2009-09-08
How is dual monitor working with fglrx these days? In Jaunty, I can't get dual monitor working in fglrx without all sorts of issues. The open source driver gives me great dual screen functionality but, of course, no 3D acceleration. I checked the radeon roadmaps and it looks like there's not going to be 3D acceleration for my 4800 series for a long time.

---

### Post by taavikko on 2009-09-08
Although the latest mesa+git + xorg tweaking fixes the gdm looping
I decided to test the fglrx and Im so happy :)

my HD3450 works beautifully.

will nevertheless keep reverting to open drivers every time there's an update.

---

### Post by DougieFresh4U on 2009-09-08
> **taavikko said:**
> Although the latest mesa+git + xorg tweaking fixes the gdm looping
I decided to test the fglrx and Im so happy :)

my HD3450 works beautifully.

will nevertheless keep reverting to open drivers every time there's an update.

Yesterday I was so happy as all was working excellent, compiz, etc. After updating last nite and today, no compiz working. Hardware Drivers says installed. So what happened after updating to make things not work any more?

---

### Post by taavikko on 2009-09-08
> **DougieFresh4U said:**
> Yesterday I was so happy as all was working excellent, compiz, etc. After updating last nite and today, no compiz working. Hardware Drivers says installed. So what happened after updating to make things not work any more?

That's pretty damn hard to say without better details.
Xorg.0.log will provide some answers.

Is the module installed to running kernel?
Is the system using the fglrx driver?
What are the packages upgraded?

---

### Post by DougieFresh4U on 2009-09-08
> **taavikko said:**
> That's pretty damn hard to say without better details.
Xorg.0.log will provide some answers.

Is the module installed to running kernel?
Is the system using the fglrx driver?
What are the packages upgraded?

Sorry for lack of details. Didn't really know what I was looking for.
Yesterday fglrx was working great. I mean wobbly, burning windows and and all. Then I updated, My 32 bit install only had 11 updates, my 64 bit had about 60 updates. But after updating, no wobbly, etc.
Hardware Drivers says installed. Gonna check logs now. Don't know what I'm looking for, but I'll know when I see it, I guess.

---

### Post by DougieFresh4U on 2009-09-08
ok, so theres a log 'jockey.log' and it says this
```
2009-09-08 11:35:13,870 DEBUG: Installing package: xorg-driver-fglrx
2009-09-08 11:35:27,189 DEBUG: install progress statusChange fglrx-kernel-source 0.000000
2009-09-08 11:35:27,198 DEBUG: install progress statusChange fglrx-kernel-source 6.666670
2009-09-08 11:35:27,579 DEBUG: install progress statusChange fglrx-kernel-source 13.333300
2009-09-08 11:35:27,620 DEBUG: install progress statusChange fglrx-kernel-source 20.000000
2009-09-08 11:35:27,750 DEBUG: install progress statusChange xorg-driver-fglrx 20.000000
2009-09-08 11:35:27,753 DEBUG: install progress statusChange xorg-driver-fglrx 26.666700
2009-09-08 11:35:30,348 DEBUG: install progress statusChange xorg-driver-fglrx 33.333300
2009-09-08 11:35:30,394 DEBUG: install progress statusChange xorg-driver-fglrx 40.000000
2009-09-08 11:35:30,499 DEBUG: install progress statusChange fglrx-amdcccle 40.000000
2009-09-08 11:35:30,502 DEBUG: install progress statusChange fglrx-amdcccle 46.666700
2009-09-08 11:35:31,039 DEBUG: install progress statusChange fglrx-amdcccle 53.333300
2009-09-08 11:35:31,091 DEBUG: install progress statusChange fglrx-amdcccle 60.000000
2009-09-08 11:35:31,150 DEBUG: install progress statusChange man-db 60.000000
2009-09-08 11:35:31,688 DEBUG: install progress statusChange sreadahead 60.000000
2009-09-08 11:35:31,807 DEBUG: install progress statusChange desktop-file-utils 60.000000
2009-09-08 11:35:32,705 DEBUG: install progress statusChange fglrx-kernel-source 60.000000
2009-09-08 11:35:32,742 DEBUG: install progress statusChange fglrx-kernel-source 66.666700
2009-09-08 11:35:58,136 DEBUG: install progress statusChange fglrx-kernel-source 73.333300
2009-09-08 11:35:58,330 DEBUG: install progress statusChange xorg-driver-fglrx 73.333300
2009-09-08 11:35:58,914 DEBUG: install progress statusChange xorg-driver-fglrx 80.000000
2009-09-08 11:35:59,051 DEBUG: install progress statusChange xorg-driver-fglrx 86.666700
2009-09-08 11:35:59,134 DEBUG: install progress statusChange fglrx-amdcccle 86.666700
2009-09-08 11:35:59,176 DEBUG: install progress statusChange fglrx-amdcccle 93.333300
2009-09-08 11:35:59,227 DEBUG: install progress statusChange fglrx-amdcccle 100.000000
2009-09-08 11:35:59,278 DEBUG: install progress statusChange initramfs-tools 100.000000
2009-09-08 11:36:09,799 DEBUG: install progress statusChange libc6 100.000000
2009-09-08 11:36:10,802 DEBUG: Selecting previously deselected package fglrx-kernel-source.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 114263 files and directories currently installed.)
Unpacking fglrx-kernel-source (from .../fglrx-kernel-source_2%3a8.660-0ubuntu1_amd64.deb) ...
Selecting previously deselected package xorg-driver-fglrx.
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_2%3a8.660-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.660-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for sreadahead ...
sreadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils ...
Setting up fglrx-kernel-source (2:8.660-0ubuntu1) ...
Loading new fglrx-8.660 DKMS files...
Building initial module for 2.6.31-9-generic, architecture -a x86_64
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-9-generic/updates/dkms/

depmod......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Setting up xorg-driver-fglrx (2:8.660-0ubuntu1) ...

Setting up fglrx-amdcccle (2:8.660-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-9-generic
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

2009-09-08 11:36:11,081 DEBUG: unbind/rebind on driver /sys/module/fglrx/drivers/pci:fglrx_pci: device 0000:01:05.0
2009-09-08 11:36:11,147 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tDriver\t"fglrx"\n']})
2009-09-08 11:36:11,204 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-09-08 11:36:11,294 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-09-08 11:36:11,409 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-09-08 11:36:11,499 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-09-08 11:36:11,819 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-09-08 11:36:11,971 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-09-08 11:36:12,119 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-09-08 11:36:12,215 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
```
and then the next one says this
```
2009-09-08 11:10:21,544 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0>
2009-09-08 11:10:21,611 DEBUG: reading modalias file /lib/modules/2.6.31-9-generic/modules.alias
2009-09-08 11:10:21,803 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2009-09-08 11:10:21,815 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2009-09-08 11:10:21,858 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2009-09-08 11:10:21,871 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2009-09-08 11:10:21,887 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2009-09-08 11:10:21,898 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-71
2009-09-08 11:10:21,900 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2009-09-08 11:10:21,902 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2009-09-08 11:10:21,911 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2009-09-08 11:10:21,935 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2009-09-08 11:10:22,126 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2009-09-08 11:10:22,127 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2009-09-08 11:10:22,128 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2009-09-08 11:10:22,158 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2009-09-08 11:10:22,242 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2009-09-08 11:10:22,243 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2009-09-08 11:10:22,399 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2009-09-08 11:10:22,400 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2009-09-08 11:10:22,426 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2009-09-08 11:10:22,427 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2009-09-08 11:10:22,428 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2009-09-08 11:10:22,450 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2009-09-08 11:10:22,451 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2009-09-08 11:10:22,452 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2009-09-08 11:10:22,452 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2009-09-08 11:10:22,499 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2009-09-08 11:10:22,551 DEBUG: Software modem not available
2009-09-08 11:10:22,552 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2009-09-08 11:10:22,600 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2009-09-08 11:10:22,602 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2009-09-08 11:10:22,602 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2009-09-08 11:10:22,603 DEBUG: all custom handlers loaded
2009-09-08 11:10:22,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2009-09-08 11:10:22,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2009-09-08 11:10:23,025 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'acpi:PNP0103:')
2009-09-08 11:10:23,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'acpi:PNP0200:')
2009-09-08 11:10:23,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v00001022d00009600sv00001019sd00001B61bc06sc00i00')
2009-09-08 11:10:23,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'usb:v046Dp092Ed0000dcFFdscFFdp00icFFisc00ip00')
2009-09-08 11:10:23,128 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'gspca_spca561', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,128 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2009-09-08 11:10:23,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2009-09-08 11:10:23,129 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'acpi:PNP0B00:')
2009-09-08 11:10:23,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'platform:pcspkr')
2009-09-08 11:10:23,130 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,130 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2009-09-08 11:10:23,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v00001022d00009602sv00000000sd00000000bc06sc04i00')
2009-09-08 11:10:23,130 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001019sd00001B61bc06sc01i00')
2009-09-08 11:10:23,411 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2009-09-08 11:10:23,411 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'acpi:PNP0000:')
2009-09-08 11:10:23,411 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001019sd00008111bc02sc00i00')
2009-09-08 11:10:23,418 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,419 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v00001002d00004383sv00001019sd00002816bc04sc03i00')
2009-09-08 11:10:23,424 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,424 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'acpi:PNP0100:')
2009-09-08 11:10:23,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2009-09-08 11:10:23,425 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2009-09-08 11:10:23,426 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('printer_deviceid', 'MFG:hp;MDL:photosmart 7550;DES:photosmart 7550;CMD:;')
2009-09-08 11:10:23,426 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2009-09-08 11:10:23,427 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2009-09-08 11:10:23,427 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'acpi:PNP0C02:')
2009-09-08 11:10:23,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2009-09-08 11:10:23,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2009-09-08 11:10:23,428 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr080014:bd07/31/2008:svnECS:pnA780GM-A:pvr1.0:rvnECS:rnA780GM-A:rvr1.0:cvnECS:ct3:cvr:')
2009-09-08 11:10:23,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'acpi:PNP0800:')
2009-09-08 11:10:23,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2009-09-08 11:10:23,447 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'input:b0001v8384p7645e0001-e0,12,kramls1,2,fw')
2009-09-08 11:10:23,447 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,448 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'usb:v03F0p3E02d0100dc00dsc00dp00ic07isc01ip03')
2009-09-08 11:10:23,469 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2009-09-08 11:10:23,471 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v00001002d00004396sv00001019sd00001B61bc0Csc03i20')
2009-09-08 11:10:23,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2009-09-08 11:10:23,477 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v00001002d00004390sv00001019sd00004390bc01sc06i01')
2009-09-08 11:10:23,482 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'acpi:PNP0C04:')
2009-09-08 11:10:23,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v00001002d00009610sv00001019sd00001B61bc03sc00i00')
2009-09-08 11:10:23,489 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-09-08 11:10:23,489 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2009-09-08 11:10:23,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,604 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-09-08 11:10:23,604 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2009-09-08 11:10:23,693 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'acpi:LNXTHERM:')
2009-09-08 11:10:23,693 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2009-09-08 11:10:23,694 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v00001002d00004385sv00001019sd00001B61bc0Csc05i00')
2009-09-08 11:10:23,700 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2009-09-08 11:10:23,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2009-09-08 11:10:23,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-09-08 11:10:23,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2009-09-08 11:10:23,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x165cef0> about HardwareID('modalias', 'acpi:PNP0C01:')
2009-09-08 11:10:23,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2009-09-08 11:10:23,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2009-09-08 11:10:23,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'acpi:PNP0103:')
2009-09-08 11:10:23,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'acpi:PNP0200:')
2009-09-08 11:10:23,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v00001022d00009600sv00001019sd00001B61bc06sc00i00')
2009-09-08 11:10:23,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'usb:v046Dp092Ed0000dcFFdscFFdp00icFFisc00ip00')
2009-09-08 11:10:23,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2009-09-08 11:10:23,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2009-09-08 11:10:23,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'acpi:PNP0B00:')
2009-09-08 11:10:23,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'platform:pcspkr')
2009-09-08 11:10:23,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2009-09-08 11:10:23,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v00001022d00009602sv00000000sd00000000bc06sc04i00')
2009-09-08 11:10:23,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001019sd00001B61bc06sc01i00')
2009-09-08 11:10:23,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2009-09-08 11:10:23,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'acpi:PNP0000:')
2009-09-08 11:10:23,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001019sd00008111bc02sc00i00')
2009-09-08 11:10:23,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001019sd00002816bc04sc03i00')
2009-09-08 11:10:23,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'acpi:PNP0100:')
2009-09-08 11:10:23,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2009-09-08 11:10:23,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2009-09-08 11:10:23,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('printer_deviceid', 'MFG:hp;MDL:photosmart 7550;DES:photosmart 7550;CMD:;')
2009-09-08 11:10:23,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2009-09-08 11:10:23,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2009-09-08 11:10:23,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'acpi:PNP0C02:')
2009-09-08 11:10:23,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2009-09-08 11:10:23,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2009-09-08 11:10:23,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr080014:bd07/31/2008:svnECS:pnA780GM-A:pvr1.0:rvnECS:rnA780GM-A:rvr1.0:cvnECS:ct3:cvr:')
2009-09-08 11:10:23,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'acpi:PNP0800:')
2009-09-08 11:10:23,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2009-09-08 11:10:23,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'input:b0001v8384p7645e0001-e0,12,kramls1,2,fw')
2009-09-08 11:10:23,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'usb:v03F0p3E02d0100dc00dsc00dp00ic07isc01ip03')
2009-09-08 11:10:23,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2009-09-08 11:10:23,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001019sd00001B61bc0Csc03i20')
2009-09-08 11:10:23,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2009-09-08 11:10:23,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v00001002d00004390sv00001019sd00004390bc01sc06i01')
2009-09-08 11:10:23,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'acpi:PNP0C04:')
2009-09-08 11:10:23,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v00001002d00009610sv00001019sd00001B61bc03sc00i00')
2009-09-08 11:10:23,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'acpi:LNXTHERM:')
2009-09-08 11:10:23,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2009-09-08 11:10:23,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v00001002d00004385sv00001019sd00001B61bc0Csc05i00')
2009-09-08 11:10:23,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2009-09-08 11:10:23,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2009-09-08 11:10:23,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2009-09-08 11:10:23,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1d02bd8> about HardwareID('modalias', 'acpi:PNP0C01:')
2009-09-08 11:10:23,742 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-09-08 11:10:24,090 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-09-08 11:10:24,299 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
```

---

### Post by NCLI on 2009-09-08
I'd suggest [downgrading the driver]("http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue") if you can't wait for a fix.

---

### Post by khelben1979 on 2009-09-08
> **DougieFresh4U said:**
> Finally, I can use my ATI Radeon HD3200! I am using 'fglrx' on my Jaunty install (.28 kernel) Nothing newer has worked until .31.9 kernel.  Running Karmic 64 bit with the 'fglrx' Hardware Driver and over all my machine is being more responsive. Compiz running great.
Any one else enjoying this?

When I installed Ubuntu Hardy for my brother in summer 2008 I got full speed from the ATi Radeon HD3200 chip. I ran Doom 3 on it to test the performance, worked pretty good.

So from my experience the ATi drivers has been working since then.

---

### Post by oldrocker99 on 2009-09-08
I guess my question is whether my Radeon Mobility X1200 will be supported under Karmic, since ATI has abandoned the chip and Jaunty won't support the fglrx drivers. I tried Jaunty with the OSS drivers, and, while compiz worked fine, I couldn't really play Neverwinter Nights without turning all the effects down all the way (and it still crawled). I downgraded to Intrepid with the ATI 9.3 drivers (the last ones that support my "legacy" chip (I will never patronize ATI, or AMD, again)), and I'm happy.

If the laptop I purchased LAST DECEMBER from Best Buy is unable to run Karmic as well, I'm inclined to, uh, take advantage of the warranty.

:guitar:

---

### Post by Reiger on 2009-09-08
X1200 falls in the category of old ATI cards which should be reasonably well supported by the Open Source drivers: I am sitting here typing this behind a laptop which has a Xpress 1100 according to the sticker and I get desktop effects and all from the Open Source drivers. :)

---

### Post by ranch hand on 2009-09-10
Well I finally got A5 to run on 4 of 5 64bit variations and 4 of 4 32bit variations and decided to try the driver on for size.

I have always been quite happy with no desktop effects and generic drivers.  But we are supposed to testing.

Fired the driver up in 1 32bit and 1 64bit.  Did not freeze the system (the result of all previous attempt to use it on my Radeon 2400 PRO).

I can set desktop effects to extra which is better than normal as at normal I can only have 2 work stations.

I can install the compiz configureation manager.  Using it is a big mistake as any alteration of the default setting freezes system so tight the only way out is to pull the plug.

This came as no surprise to me as this has been my experience pretty much all along.  This is actually a little "better".  I can't drag apps from one workspace to another with any setting except none in effects.

As I generally run 6 workstations all full, I see no need for this silly crap at all so this does not bother me.

I will keep the stuff on those to installs until the end of testing.  My testing drive will be wiped and I will not use this silly stuff on any install I intend to use.

The appeal of this is just beyond me.

---

### Post by rbmorse on 2009-09-10
It's something Windows can't do, so that makes it mandatory for a certain segment of the userbase. I don't understand it, either.

---

### Post by Reiger on 2009-09-10
Desktop effects for the sake of it are not so useful; but a dash of translucency and some window switching (alt+tab) magic does add a lot to the aesthetics of a DE..

But I should note I rather prefer the desktop effects of kwin to those of compiz; not because the compiz ones are worse per se but because in the KDE-total package with more emphasis (especially in the current Air theme) on 'lightness' of the widgets they blend in better. GTK+ bulky widgets (and especially so with dark themes, or beware: ancient default themes) don't mix well with them, I find.

---

### Post by dreddor on 2009-09-11
> **Longinus00 said:**
> How is dual monitor working with fglrx these days? In Jaunty, I can't get dual monitor working in fglrx without all sorts of issues. The open source driver gives me great dual screen functionality but, of course, no 3D acceleration. I checked the radeon roadmaps and it looks like there's not going to be 3D acceleration for my 4800 series for a long time.

All I had to do to get dual monitors working was enable it in ccsm. It's working well so far.

---

