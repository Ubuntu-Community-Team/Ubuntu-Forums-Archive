---
title: "ATI drivers broken after update"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by AlexRamallo on 2011-04-22
Hi everyone. I recently got a notification telling me there were updates available via the update manager, so naturally I updated.

I'm on Ubuntu 10.04 LTS (Lucid Lynx) and I installed the updates yesterday around 3:30pm iirc

Before the update, everything was working perfectly. I have a ati 4870 card and the proprietary drivers were functioning with desktop effects and cube and all that good stuff, but after the update I got a message that said **"Sorry, the package "fglrx" failed to install or upgrade."**

I tried restarting a couple of times but it didn't work. Also, whenever I tried enabling the drivers via the System->Administration->Hardware Drivers thing, first it says "Downloading and Installing drivers" (and the progress bar gets stuck halfway, if thats important), then I get an error saying **SystemError: installArchives() failed**

I tried reinstalling the fglrx package from synaptic but I got the error **"E: fglrx: subprocess installed post-installation script returned error exit status 10"** and the output on the installation dialog also gave errors:
```

Error! Bad return status for module on kernel: 2.6.32-31-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.723.1/build/ for more information
....

```
here is that make.log:
```

DKMS make.log for fglrx-8.723.1 for kernel 2.6.32-31-generic (x86_64)
Fri Apr 22 09:04:44 EDT 2011
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.32-31-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.723.1/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-31-generic'
Makefile:303: /usr/src/linux-headers-2.6.32-31-generic/scripts/Kbuild.include: No such file or directory
Makefile:538: /usr/src/linux-headers-2.6.32-31-generic/arch/x86/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.32-31-generic/arch/x86/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-31-generic'
make: *** [kmod_build] Error 2
build failed with return value 2

```


Also, I remember messing around with stuff and something told me to look at jockey.log, but I don't remember what it was, but here it is just incase since it does talk about drivers and fglrx:
```
2011-04-21 21:24:52,979 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998>
2011-04-21 21:24:52,980 DEBUG: reading modalias file /lib/modules/2.6.32-31-generic/modules.alias
2011-04-21 21:24:53,107 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-04-21 21:24:53,115 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-04-21 21:24:53,154 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-04-21 21:24:53,160 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-04-21 21:24:53,171 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-04-21 21:24:53,175 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-04-21 21:24:53,187 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-04-21 21:24:53,419 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-04-21 21:24:53,444 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-04-21 21:24:53,478 DEBUG: Software modem not available
2011-04-21 21:24:53,478 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-04-21 21:24:53,507 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-04-21 21:24:53,507 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-04-21 21:24:53,507 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-04-21 21:24:53,507 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-04-21 21:24:53,512 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-04-21 21:24:53,518 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-04-21 21:24:53,518 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-04-21 21:24:53,518 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-04-21 21:24:53,555 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-04-21 21:24:53,557 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-04-21 21:24:53,565 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-04-21 21:24:53,565 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-04-21 21:24:53,634 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-04-21 21:24:53,634 DEBUG: Firmware for DVB cards not available
2011-04-21 21:24:53,635 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-04-21 21:24:53,642 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-04-21 21:24:53,644 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-04-21 21:24:53,650 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-04-21 21:24:53,653 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-04-21 21:24:53,655 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-04-21 21:24:53,662 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-04-21 21:24:53,662 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-04-21 21:24:53,667 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-04-21 21:24:53,670 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-04-21 21:24:53,677 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-04-21 21:24:53,677 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-04-21 21:24:53,750 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-04-21 21:24:53,750 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-04-21 21:24:53,777 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-04-21 21:24:53,778 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-04-21 21:24:53,778 DEBUG: all custom handlers loaded
2011-04-21 21:24:53,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-04-21 21:24:53,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'input:b0003v15CAp00C3e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-04-21 21:24:53,974 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:53,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd00000269sv00001043sd00008221bc06sc80i00')
2011-04-21 21:24:54,254 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:54,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:PNP0400:')
2011-04-21 21:24:54,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:device:')
2011-04-21 21:24:54,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003AAsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:54,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'usb:v15CAp00C3d0512dc00dsc00dp00ic03isc01ip02')
2011-04-21 21:24:54,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:54,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003ADsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:54,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-04-21 21:24:54,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:54,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-04-21 21:24:54,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:PNP0200:')
2011-04-21 21:24:54,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'platform:pcspkr')
2011-04-21 21:24:54,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:54,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:54,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd00000266sv00001043sd000081BCbc01sc01i85')
2011-04-21 21:24:54,287 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:54,287 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-04-21 21:24:54,287 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003A3sv00000000sd00000000bc06sc00i00')
2011-04-21 21:24:54,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003B4sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:54,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:PNP0700:')
2011-04-21 21:24:54,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd00000270sv00001043sd000081BCbc05sc00i00')
2011-04-21 21:24:54,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-04-21 21:24:54,298 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003ACsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:54,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003B5sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:54,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:PNP0000:')
2011-04-21 21:24:54,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd00000260sv00001043sd000081BCbc06sc01i00')
2011-04-21 21:24:54,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003BCsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:54,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003B2sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:54,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v00001002d00009440sv00001043sd00000256bc03sc00i00')
2011-04-21 21:24:54,539 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-04-21 21:24:55,639 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-04-21 21:24:54,542 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-04-21 21:24:55,639 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,639 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'usb:v18D1p4E22d0227dc00dsc00dp00ic08isc06ip50')
2011-04-21 21:24:55,640 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,640 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd0000026Esv00001043sd000081BCbc0Csc03i20')
2011-04-21 21:24:55,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'input:b0001v10ECp0883e0001-e0,12,kramls1,2,fw')
2011-04-21 21:24:55,644 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd0000026Csv00001043sd0000829Ebc04sc03i00')
2011-04-21 21:24:55,648 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:PNP0103:')
2011-04-21 21:24:55,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:PNP0100:')
2011-04-21 21:24:55,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003B1sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,651 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd00000272sv00001043sd000081BCbc05sc00i00')
2011-04-21 21:24:55,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-04-21 21:24:55,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd00000264sv00001043sd000081BCbc0Csc05i00')
2011-04-21 21:24:55,663 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvrASUSP5N-DACPIBIOSRevision0801:bd08/01/2008:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5N-D:rvr1.XX:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-04-21 21:24:55,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003BAsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-04-21 21:24:55,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003B3sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,682 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003AEsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-04-21 21:24:55,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'usb:v0A12p0001d4839dcE0dsc01dp01icE0isc01ip01')
2011-04-21 21:24:55,686 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v00001002d0000AA30sv00001043sd0000AA30bc04sc03i00')
2011-04-21 21:24:55,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003ABsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,693 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000005BFsv00000000sd00000000bc06sc04i00')
2011-04-21 21:24:55,696 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2011-04-21 21:24:55,728 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,728 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,728 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:PNP0800:')
2011-04-21 21:24:55,728 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003A9sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,732 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd0000026Fsv00000000sd00000000bc06sc04i01')
2011-04-21 21:24:55,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:PNP0501:')
2011-04-21 21:24:55,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'usb:v18D1p4E22d0227dc00dsc00dp00icFFisc42ip01')
2011-04-21 21:24:55,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-04-21 21:24:55,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-04-21 21:24:55,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-04-21 21:24:55,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-04-21 21:24:55,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd00000265sv00001043sd000081BCbc01sc01i8a')
2011-04-21 21:24:55,740 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003B6sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,744 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003A8sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,747 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003B0sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd00000267sv00001043sd000081BCbc01sc01i85')
2011-04-21 21:24:55,754 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,754 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-04-21 21:24:55,754 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-04-21 21:24:55,754 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'pci:v000010DEd000003AFsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1138998> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-04-21 21:24:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-04-21 21:24:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'input:b0003v15CAp00C3e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-04-21 21:24:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd00000269sv00001043sd00008221bc06sc80i00')
2011-04-21 21:24:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:PNP0400:')
2011-04-21 21:24:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:device:')
2011-04-21 21:24:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003AAsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'usb:v15CAp00C3d0512dc00dsc00dp00ic03isc01ip02')
2011-04-21 21:24:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003ADsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-04-21 21:24:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-04-21 21:24:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:PNP0200:')
2011-04-21 21:24:55,759 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'platform:pcspkr')
2011-04-21 21:24:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd00000266sv00001043sd000081BCbc01sc01i85')
2011-04-21 21:24:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-04-21 21:24:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003A3sv00000000sd00000000bc06sc00i00')
2011-04-21 21:24:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003B4sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:PNP0700:')
2011-04-21 21:24:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd00000270sv00001043sd000081BCbc05sc00i00')
2011-04-21 21:24:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-04-21 21:24:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003ACsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003B5sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:PNP0000:')
2011-04-21 21:24:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd00000260sv00001043sd000081BCbc06sc01i00')
2011-04-21 21:24:55,760 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003BCsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003B2sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v00001002d00009440sv00001043sd00000256bc03sc00i00')
2011-04-21 21:24:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'usb:v18D1p4E22d0227dc00dsc00dp00ic08isc06ip50')
2011-04-21 21:24:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd0000026Esv00001043sd000081BCbc0Csc03i20')
2011-04-21 21:24:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'input:b0001v10ECp0883e0001-e0,12,kramls1,2,fw')
2011-04-21 21:24:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd0000026Csv00001043sd0000829Ebc04sc03i00')
2011-04-21 21:24:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:PNP0103:')
2011-04-21 21:24:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:PNP0100:')
2011-04-21 21:24:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003B1sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd00000272sv00001043sd000081BCbc05sc00i00')
2011-04-21 21:24:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-04-21 21:24:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd00000264sv00001043sd000081BCbc0Csc05i00')
2011-04-21 21:24:55,761 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvrASUSP5N-DACPIBIOSRevision0801:bd08/01/2008:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5N-D:rvr1.XX:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-04-21 21:24:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003BAsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-04-21 21:24:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003B3sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003AEsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-04-21 21:24:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'usb:v0A12p0001d4839dcE0dsc01dp01icE0isc01ip01')
2011-04-21 21:24:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v00001002d0000AA30sv00001043sd0000AA30bc04sc03i00')
2011-04-21 21:24:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003ABsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000005BFsv00000000sd00000000bc06sc04i00')
2011-04-21 21:24:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2011-04-21 21:24:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:PNP0800:')
2011-04-21 21:24:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003A9sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd0000026Fsv00000000sd00000000bc06sc04i01')
2011-04-21 21:24:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:PNP0501:')
2011-04-21 21:24:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'usb:v18D1p4E22d0227dc00dsc00dp00icFFisc42ip01')
2011-04-21 21:24:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-04-21 21:24:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-04-21 21:24:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-04-21 21:24:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-04-21 21:24:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd00000265sv00001043sd000081BCbc01sc01i8a')
2011-04-21 21:24:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003B6sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003A8sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003B0sv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd00000267sv00001043sd000081BCbc01sc01i85')
2011-04-21 21:24:55,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-04-21 21:24:55,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'pci:v000010DEd000003AFsv00000000sd00000000bc05sc00i00')
2011-04-21 21:24:55,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18abb00> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-04-21 21:27:46,053 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-04-21 21:27:46,218 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-04-21 21:27:46,349 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-04-21 21:27:49,147 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-04-21 21:27:52,302 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-04-21 21:27:52,303 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-04-21 21:27:52,303 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-04-21 21:27:59,349 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-04-21 21:27:59,458 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-04-21 21:28:28,972 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-04-21 21:28:29,075 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-04-21 21:28:29,187 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-04-21 21:28:29,286 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-04-21 21:28:29,418 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-04-21 21:28:29,523 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-04-21 21:28:41,814 DEBUG: Shutting down
```
I'm 90% that reinstalling will fix the problem, but I have over 6 months worth of code in 5gb for a very important project I'm working on and my environment is set up very specifically for it and I would *really* preffer to not have to back up the code and set up my work environment all over again. Any help is greatly appreciated

---

### Post by Mark Phelps on 2011-04-22
Restricted driver (fglrx) versions are tied to specific kernel versions. When you update the kernel, you "break" fglrx.

Since you're pressed for time, you should probably just follow the instructions in the link below to remove the flgrx drivers:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

When you reboot, Ubuntu should sense your card and install the default open-source drivers.

---

### Post by AlexRamallo on 2011-04-22
When I try to run
```
sudo apt-get remove --purge fglrx*
```
it says 110MB will be removed, but when I enter Y I get this error
```
(Reading database ... 333017 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/mesa/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--purge):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
rebooting does nothing :(

---

### Post by AlexRamallo on 2011-04-23
Fixed the problem! All I had to do was remove the diversion(whatever that is) with dpkg-divert remove. more information in this article:
[http://caulfield.info/emmet/2008/07/manually-removing-diversions-w.html](http://caulfield.info/emmet/2008/07/manually-removing-diversions-w.html)

after that I was able to remove it by purging fglrx

I was able to reinstall it normally with synaptic, but now my dual monitors are messed up. it says please log out and log back in again when I try to enable the second one but logging out and/or restarting doesn't do anything. All I get now is mirrored monitors on both :[

---

