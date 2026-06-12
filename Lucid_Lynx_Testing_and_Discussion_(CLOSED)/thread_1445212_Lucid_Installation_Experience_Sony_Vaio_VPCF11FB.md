---
title: "Lucid Installation Experience Sony Vaio VPCF11FB"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ricardo.gloe on 2010-04-02
I installed Ubuntu 10.04, LL, latest Beta version, and everything went smoothly. Everything seems to be working fine, only major issue was the nvidia driver and the edid problem, but the solution is pretty easy. 

If this issue is not resolved for the final release, it would be interesting to have a final correct page/link describing the problem and solution. Most links I found said you had to get a .bin file with the laptops edid info, using windows and then there are lots of sony vaio users asking for edid files like a edid file blackmarket.

But you don't need to download this file.

Anyway, the second issue is using a dual monitor or connecting the laptop to a TV using HDMI. Still haven't figured that one.

---

### Post by Niej on 2010-04-02
Hi, I also installed lucid beta on a vaio VPCF1 and experienced
some problems with the nvidia driver. I was looking for solutions but none ended well.
I have native full resolution with the nouveau driver, but when
trying to load the restricted driver, I receive and error from jockey (see jockey log) and at the next boot a have the screen shifted one half (the left edge is at the center of the screen) at low resolution.
Also an error message "Can't load Nvidia module, no screen found or there is a screen with a unusable configuration"
So, at the moment I still have nouveau without 3D effects.
```

2010-03-31 03:52:58,681 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0>
2010-03-31 03:52:58,683 DEBUG: reading modalias file /lib/modules/2.6.32-18-generic/modules.alias
2010-03-31 03:52:58,765 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-03-31 03:52:58,779 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-03-31 03:52:58,823 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-03-31 03:52:58,829 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-03-31 03:52:58,842 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-03-31 03:52:58,846 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-03-31 03:52:58,857 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-03-31 03:52:59,004 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-03-31 03:52:59,084 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-03-31 03:52:59,085 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-03-31 03:52:59,114 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-03-31 03:52:59,119 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-03-31 03:52:59,120 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-03-31 03:52:59,130 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-03-31 03:52:59,131 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-03-31 03:52:59,146 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-03-31 03:52:59,146 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-03-31 03:52:59,157 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-03-31 03:52:59,157 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-03-31 03:52:59,197 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-03-31 03:52:59,198 DEBUG: Firmware for DVB cards not available
2010-03-31 03:52:59,199 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-03-31 03:52:59,205 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-03-31 03:52:59,206 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-03-31 03:52:59,206 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-03-31 03:52:59,207 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-03-31 03:52:59,221 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-03-31 03:52:59,270 DEBUG: Software modem not available
2010-03-31 03:52:59,270 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-03-31 03:52:59,277 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-03-31 03:52:59,287 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-03-31 03:52:59,288 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-03-31 03:52:59,288 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-03-31 03:52:59,313 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-03-31 03:52:59,314 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-03-31 03:52:59,324 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-03-31 03:52:59,325 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-03-31 03:52:59,370 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-03-31 03:52:59,371 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-03-31 03:52:59,392 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-03-31 03:52:59,392 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-03-31 03:52:59,392 DEBUG: all custom handlers loaded
2010-03-31 03:52:59,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-03-31 03:52:59,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-03-31 03:52:59,482 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:52:59,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002CA3sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:52:59,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002CA1sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:52:59,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-03-31 03:52:59,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:device:')
2010-03-31 03:52:59,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v000010DEd00000BE3sv0000104Dsd00009067bc04sc03i00')
2010-03-31 03:52:59,946 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:52:59,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'platform:sony-laptop')
2010-03-31 03:52:59,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d0000D151sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:52:59,948 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002CA8sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:52:59,950 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,2,k112,r8,amlsfw')
2010-03-31 03:52:59,950 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:52:59,950 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-03-31 03:52:59,950 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-03-31 03:52:59,950 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002CA9sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:52:59,952 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'platform:regulatory')
2010-03-31 03:52:59,953 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002C98sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:52:59,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-03-31 03:52:59,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002CA2sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:52:59,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d0000D132sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:52:59,959 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d0000D150sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:52:59,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:PNP0303:')
2010-03-31 03:52:59,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00003B30sv0000104Dsd00009067bc0Csc05i00')
2010-03-31 03:52:59,963 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:52:59,963 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:INT0800:')
2010-03-31 03:52:59,963 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v000010DEd00000A75sv0000104Dsd00009067bc03sc00i00')
2010-03-31 03:52:59,966 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:52:59,966 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:52:59,970 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-03-31 03:52:59,971 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-03-31 03:53:00,469 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d0000D158sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:53:00,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:PNP0100:')
2010-03-31 03:53:00,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002C52sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,482 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v000011ABd00004380sv0000104Dsd00009067bc02sc00i00')
2010-03-31 03:53:00,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00001180d0000E822sv0000104Dsd00009067bc08sc05i00')
2010-03-31 03:53:00,507 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00003B03sv0000104Dsd00009067bc06sc01i00')
2010-03-31 03:53:00,510 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'usb:v064Ep2100d0300dcEFdsc02dp01ic0Eisc02ip00')
2010-03-31 03:53:00,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'usb:v0489pE00Fd0346dcE0dsc01dp01icFEisc01ip01')
2010-03-31 03:53:00,533 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,533 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002C90sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'input:b0003v064Ep2100e0300-e0,1,kD4,ramlsfw')
2010-03-31 03:53:00,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002CA0sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,4,k71,72,73,8A,94,95,9E,A1,B7,B8,B9,CA,CB,CD,D4,E0,E1,E3,ED,EE,121,174,1A2,1A3,1D0,1D1,1D2,1D3,1D9,1DA,1DC,1E0,1E1,1E2,1E3,1E4,ram4,lsfw')
2010-03-31 03:53:00,537 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-03-31 03:53:00,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v0000168Cd0000002Esv0000105Bsd0000E030bc02sc80i00')
2010-03-31 03:53:00,546 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-03-31 03:53:00,546 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:SNY5001:')
2010-03-31 03:53:00,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002C81sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,548 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrR0250Y6:bd12/07/2009:svnSonyCorporation:pnVPCF11KFX:pvrR5839592:rvnSonyCorporation:rnVAIO:rvrN/A:cvnSonyCorporation:ct10:cvrN/A:')
2010-03-31 03:53:00,558 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00003B34sv0000104Dsd00009067bc0Csc03i20')
2010-03-31 03:53:00,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:PNP0103:')
2010-03-31 03:53:00,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00001180d0000E230sv0000104Dsd00009067bc08sc80i00')
2010-03-31 03:53:00,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-03-31 03:53:00,560 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'usb:v0489pE00Fd0346dcE0dsc01dp01icFFiscFFipFF')
2010-03-31 03:53:00,561 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-03-31 03:53:00,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2010-03-31 03:53:00,562 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00003B2Fsv0000104Dsd00009067bc01sc06i01')
2010-03-31 03:53:00,564 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,564 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,564 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d0000D156sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:53:00,566 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-03-31 03:53:00,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-03-31 03:53:00,568 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:SNY9011:PNP0F13:')
2010-03-31 03:53:00,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d0000D155sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:53:00,570 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002CABsv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002C9Csv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:PNP0000:')
2010-03-31 03:53:00,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'usb:v0489pE00Fd0346dcE0dsc01dp01icE0isc01ip01')
2010-03-31 03:53:00,575 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-03-31 03:53:00,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-03-31 03:53:00,575 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-03-31 03:53:00,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'usb:v064Ep2100d0300dcEFdsc02dp01ic0Eisc01ip00')
2010-03-31 03:53:00,576 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002C91sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,578 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'platform:pcspkr')
2010-03-31 03:53:00,578 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,578 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,579 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00001180d0000E832sv0000104Dsd00009067bc0Csc00i10')
2010-03-31 03:53:00,579 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,579 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,579 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002CAAsv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d0000D157sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:53:00,583 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00003B56sv0000104Dsd00009067bc04sc03i00')
2010-03-31 03:53:00,585 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-03-31 03:53:00,592 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,593 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00002C99sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,595 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2010-03-31 03:53:00,595 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:53:00,595 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'pci:v00008086d00003B3Csv0000104Dsd00009067bc0Csc03i20')
2010-03-31 03:53:00,597 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x287c5f0> about HardwareID('modalias', 'acpi:PNP0200:')
2010-03-31 03:53:00,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-03-31 03:53:00,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-03-31 03:53:00,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002CA3sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002CA1sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-03-31 03:53:00,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:device:')
2010-03-31 03:53:00,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v000010DEd00000BE3sv0000104Dsd00009067bc04sc03i00')
2010-03-31 03:53:00,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'platform:sony-laptop')
2010-03-31 03:53:00,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d0000D151sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:53:00,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002CA8sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,2,k112,r8,amlsfw')
2010-03-31 03:53:00,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-03-31 03:53:00,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-03-31 03:53:00,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002CA9sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'platform:regulatory')
2010-03-31 03:53:00,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002C98sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-03-31 03:53:00,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002CA2sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d0000D132sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d0000D150sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:53:00,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:PNP0303:')
2010-03-31 03:53:00,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00003B30sv0000104Dsd00009067bc0Csc05i00')
2010-03-31 03:53:00,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:INT0800:')
2010-03-31 03:53:00,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v000010DEd00000A75sv0000104Dsd00009067bc03sc00i00')
2010-03-31 03:53:00,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d0000D158sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:53:00,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:PNP0100:')
2010-03-31 03:53:00,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002C52sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v000011ABd00004380sv0000104Dsd00009067bc02sc00i00')
2010-03-31 03:53:00,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00001180d0000E822sv0000104Dsd00009067bc08sc05i00')
2010-03-31 03:53:00,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00003B03sv0000104Dsd00009067bc06sc01i00')
2010-03-31 03:53:00,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'usb:v064Ep2100d0300dcEFdsc02dp01ic0Eisc02ip00')
2010-03-31 03:53:00,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'usb:v0489pE00Fd0346dcE0dsc01dp01icFEisc01ip01')
2010-03-31 03:53:00,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002C90sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'input:b0003v064Ep2100e0300-e0,1,kD4,ramlsfw')
2010-03-31 03:53:00,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002CA0sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,4,k71,72,73,8A,94,95,9E,A1,B7,B8,B9,CA,CB,CD,D4,E0,E1,E3,ED,EE,121,174,1A2,1A3,1D0,1D1,1D2,1D3,1D9,1DA,1DC,1E0,1E1,1E2,1E3,1E4,ram4,lsfw')
2010-03-31 03:53:00,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-03-31 03:53:00,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v0000168Cd0000002Esv0000105Bsd0000E030bc02sc80i00')
2010-03-31 03:53:00,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-03-31 03:53:00,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:SNY5001:')
2010-03-31 03:53:00,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002C81sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrR0250Y6:bd12/07/2009:svnSonyCorporation:pnVPCF11KFX:pvrR5839592:rvnSonyCorporation:rnVAIO:rvrN/A:cvnSonyCorporation:ct10:cvrN/A:')
2010-03-31 03:53:00,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00003B34sv0000104Dsd00009067bc0Csc03i20')
2010-03-31 03:53:00,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:PNP0103:')
2010-03-31 03:53:00,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00001180d0000E230sv0000104Dsd00009067bc08sc80i00')
2010-03-31 03:53:00,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-03-31 03:53:00,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'usb:v0489pE00Fd0346dcE0dsc01dp01icFFiscFFipFF')
2010-03-31 03:53:00,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-03-31 03:53:00,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2010-03-31 03:53:00,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00003B2Fsv0000104Dsd00009067bc01sc06i01')
2010-03-31 03:53:00,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d0000D156sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:53:00,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-03-31 03:53:00,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-03-31 03:53:00,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:SNY9011:PNP0F13:')
2010-03-31 03:53:00,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d0000D155sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:53:00,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002CABsv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002C9Csv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:PNP0000:')
2010-03-31 03:53:00,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'usb:v0489pE00Fd0346dcE0dsc01dp01icE0isc01ip01')
2010-03-31 03:53:00,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-03-31 03:53:00,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-03-31 03:53:00,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-03-31 03:53:00,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'usb:v064Ep2100d0300dcEFdsc02dp01ic0Eisc01ip00')
2010-03-31 03:53:00,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002C91sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'platform:pcspkr')
2010-03-31 03:53:00,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00001180d0000E832sv0000104Dsd00009067bc0Csc00i10')
2010-03-31 03:53:00,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002CAAsv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d0000D157sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:53:00,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00003B56sv0000104Dsd00009067bc04sc03i00')
2010-03-31 03:53:00,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-03-31 03:53:00,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00002C99sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:53:00,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2010-03-31 03:53:00,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'pci:v00008086d00003B3Csv0000104Dsd00009067bc0Csc03i20')
2010-03-31 03:53:00,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d19cf8> about HardwareID('modalias', 'acpi:PNP0200:')
2010-03-31 03:53:32,210 DEBUG: Shutting down
2010-03-31 03:57:40,573 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0>
2010-03-31 03:57:40,575 DEBUG: reading modalias file /lib/modules/2.6.32-18-generic/modules.alias
2010-03-31 03:57:40,662 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-03-31 03:57:40,662 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-03-31 03:57:40,684 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-03-31 03:57:40,685 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-03-31 03:57:40,687 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-03-31 03:57:40,688 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-03-31 03:57:40,690 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-03-31 03:57:40,832 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-03-31 03:57:40,837 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-03-31 03:57:40,838 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-03-31 03:57:40,847 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-03-31 03:57:40,852 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-03-31 03:57:40,853 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-03-31 03:57:40,863 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-03-31 03:57:40,863 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-03-31 03:57:40,869 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-03-31 03:57:40,869 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-03-31 03:57:40,880 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-03-31 03:57:40,880 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-03-31 03:57:40,896 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-03-31 03:57:40,897 DEBUG: Firmware for DVB cards not available
2010-03-31 03:57:40,898 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-03-31 03:57:40,904 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-03-31 03:57:40,905 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-03-31 03:57:40,905 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-03-31 03:57:40,905 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-03-31 03:57:40,918 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-03-31 03:57:40,932 DEBUG: Software modem not available
2010-03-31 03:57:40,932 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-03-31 03:57:40,939 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-03-31 03:57:40,949 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-03-31 03:57:40,950 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-03-31 03:57:40,950 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-03-31 03:57:40,957 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-03-31 03:57:40,958 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-03-31 03:57:40,968 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-03-31 03:57:40,968 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-03-31 03:57:40,985 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-03-31 03:57:40,985 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-03-31 03:57:40,991 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-03-31 03:57:40,992 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-03-31 03:57:40,992 DEBUG: all custom handlers loaded
2010-03-31 03:57:40,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-03-31 03:57:40,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-03-31 03:57:41,081 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002CA3sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002CA1sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-03-31 03:57:41,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:device:')
2010-03-31 03:57:41,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v000010DEd00000BE3sv0000104Dsd00009067bc04sc03i00')
2010-03-31 03:57:41,537 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'platform:sony-laptop')
2010-03-31 03:57:41,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d0000D151sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:57:41,539 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002CA8sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,541 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,2,k112,r8,amlsfw')
2010-03-31 03:57:41,541 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,541 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-03-31 03:57:41,541 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-03-31 03:57:41,541 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002CA9sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,543 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'platform:regulatory')
2010-03-31 03:57:41,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002C98sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-03-31 03:57:41,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002CA2sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,548 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d0000D132sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d0000D150sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:57:41,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:PNP0303:')
2010-03-31 03:57:41,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00003B30sv0000104Dsd00009067bc0Csc05i00')
2010-03-31 03:57:41,554 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,554 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:INT0800:')
2010-03-31 03:57:41,554 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v000010DEd00000A75sv0000104Dsd00009067bc03sc00i00')
2010-03-31 03:57:41,557 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,557 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,561 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-03-31 03:57:41,562 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-03-31 03:57:41,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d0000D158sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:57:41,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:PNP0100:')
2010-03-31 03:57:41,654 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002C52sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v000011ABd00004380sv0000104Dsd00009067bc02sc00i00')
2010-03-31 03:57:41,677 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00001180d0000E822sv0000104Dsd00009067bc08sc05i00')
2010-03-31 03:57:41,679 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00003B03sv0000104Dsd00009067bc06sc01i00')
2010-03-31 03:57:41,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,682 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'usb:v064Ep2100d0300dcEFdsc02dp01ic0Eisc02ip00')
2010-03-31 03:57:41,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'usb:v0489pE00Fd0346dcE0dsc01dp01icFEisc01ip01')
2010-03-31 03:57:41,700 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,700 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002C90sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'input:b0003v064Ep2100e0300-e0,1,kD4,ramlsfw')
2010-03-31 03:57:41,702 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002CA0sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,4,k71,72,73,8A,94,95,9E,A1,B7,B8,B9,CA,CB,CD,D4,E0,E1,E3,ED,EE,121,174,1A2,1A3,1D0,1D1,1D2,1D3,1D9,1DA,1DC,1E0,1E1,1E2,1E3,1E4,ram4,lsfw')
2010-03-31 03:57:41,704 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-03-31 03:57:41,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v0000168Cd0000002Esv0000105Bsd0000E030bc02sc80i00')
2010-03-31 03:57:41,712 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-03-31 03:57:41,712 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:SNY5001:')
2010-03-31 03:57:41,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002C81sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrR0250Y6:bd12/07/2009:svnSonyCorporation:pnVPCF11KFX:pvrR5839592:rvnSonyCorporation:rnVAIO:rvrN/A:cvnSonyCorporation:ct10:cvrN/A:')
2010-03-31 03:57:41,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00003B34sv0000104Dsd00009067bc0Csc03i20')
2010-03-31 03:57:41,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:PNP0103:')
2010-03-31 03:57:41,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00001180d0000E230sv0000104Dsd00009067bc08sc80i00')
2010-03-31 03:57:41,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-03-31 03:57:41,727 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,727 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'usb:v0489pE00Fd0346dcE0dsc01dp01icFFiscFFipFF')
2010-03-31 03:57:41,727 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,727 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-03-31 03:57:41,727 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2010-03-31 03:57:41,728 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00003B2Fsv0000104Dsd00009067bc01sc06i01')
2010-03-31 03:57:41,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d0000D156sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:57:41,732 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-03-31 03:57:41,734 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-03-31 03:57:41,734 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,734 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:SNY9011:PNP0F13:')
2010-03-31 03:57:41,734 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d0000D155sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:57:41,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002CABsv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002C9Csv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:PNP0000:')
2010-03-31 03:57:41,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'usb:v0489pE00Fd0346dcE0dsc01dp01icE0isc01ip01')
2010-03-31 03:57:41,740 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,741 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-03-31 03:57:41,741 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-03-31 03:57:41,741 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,741 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-03-31 03:57:41,741 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'usb:v064Ep2100d0300dcEFdsc02dp01ic0Eisc01ip00')
2010-03-31 03:57:41,741 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,741 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002C91sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'platform:pcspkr')
2010-03-31 03:57:41,744 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,744 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,744 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00001180d0000E832sv0000104Dsd00009067bc0Csc00i10')
2010-03-31 03:57:41,744 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,744 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,744 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002CAAsv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d0000D157sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:57:41,748 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00003B56sv0000104Dsd00009067bc04sc03i00')
2010-03-31 03:57:41,750 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-03-31 03:57:41,758 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,758 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00002C99sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2010-03-31 03:57:41,760 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-03-31 03:57:41,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'pci:v00008086d00003B3Csv0000104Dsd00009067bc0Csc03i20')
2010-03-31 03:57:41,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x14545f0> about HardwareID('modalias', 'acpi:PNP0200:')
2010-03-31 03:57:41,762 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-03-31 03:57:41,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-03-31 03:57:41,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002CA3sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002CA1sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-03-31 03:57:41,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:device:')
2010-03-31 03:57:41,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v000010DEd00000BE3sv0000104Dsd00009067bc04sc03i00')
2010-03-31 03:57:41,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'platform:sony-laptop')
2010-03-31 03:57:41,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d0000D151sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:57:41,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002CA8sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,2,k112,r8,amlsfw')
2010-03-31 03:57:41,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-03-31 03:57:41,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-03-31 03:57:41,763 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002CA9sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'platform:regulatory')
2010-03-31 03:57:41,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002C98sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-03-31 03:57:41,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002CA2sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d0000D132sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d0000D150sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:57:41,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:PNP0303:')
2010-03-31 03:57:41,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00003B30sv0000104Dsd00009067bc0Csc05i00')
2010-03-31 03:57:41,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:INT0800:')
2010-03-31 03:57:41,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v000010DEd00000A75sv0000104Dsd00009067bc03sc00i00')
2010-03-31 03:57:41,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d0000D158sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:57:41,764 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:PNP0100:')
2010-03-31 03:57:41,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002C52sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v000011ABd00004380sv0000104Dsd00009067bc02sc00i00')
2010-03-31 03:57:41,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00001180d0000E822sv0000104Dsd00009067bc08sc05i00')
2010-03-31 03:57:41,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00003B03sv0000104Dsd00009067bc06sc01i00')
2010-03-31 03:57:41,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'usb:v064Ep2100d0300dcEFdsc02dp01ic0Eisc02ip00')
2010-03-31 03:57:41,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'usb:v0489pE00Fd0346dcE0dsc01dp01icFEisc01ip01')
2010-03-31 03:57:41,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002C90sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'input:b0003v064Ep2100e0300-e0,1,kD4,ramlsfw')
2010-03-31 03:57:41,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002CA0sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,4,k71,72,73,8A,94,95,9E,A1,B7,B8,B9,CA,CB,CD,D4,E0,E1,E3,ED,EE,121,174,1A2,1A3,1D0,1D1,1D2,1D3,1D9,1DA,1DC,1E0,1E1,1E2,1E3,1E4,ram4,lsfw')
2010-03-31 03:57:41,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-03-31 03:57:41,765 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v0000168Cd0000002Esv0000105Bsd0000E030bc02sc80i00')
2010-03-31 03:57:41,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-03-31 03:57:41,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:SNY5001:')
2010-03-31 03:57:41,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002C81sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrR0250Y6:bd12/07/2009:svnSonyCorporation:pnVPCF11KFX:pvrR5839592:rvnSonyCorporation:rnVAIO:rvrN/A:cvnSonyCorporation:ct10:cvrN/A:')
2010-03-31 03:57:41,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00003B34sv0000104Dsd00009067bc0Csc03i20')
2010-03-31 03:57:41,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:PNP0103:')
2010-03-31 03:57:41,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00001180d0000E230sv0000104Dsd00009067bc08sc80i00')
2010-03-31 03:57:41,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-03-31 03:57:41,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'usb:v0489pE00Fd0346dcE0dsc01dp01icFFiscFFipFF')
2010-03-31 03:57:41,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-03-31 03:57:41,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2010-03-31 03:57:41,766 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00003B2Fsv0000104Dsd00009067bc01sc06i01')
2010-03-31 03:57:41,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d0000D156sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:57:41,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-03-31 03:57:41,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-03-31 03:57:41,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:SNY9011:PNP0F13:')
2010-03-31 03:57:41,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d0000D155sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:57:41,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002CABsv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002C9Csv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:PNP0000:')
2010-03-31 03:57:41,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'usb:v0489pE00Fd0346dcE0dsc01dp01icE0isc01ip01')
2010-03-31 03:57:41,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-03-31 03:57:41,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-03-31 03:57:41,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-03-31 03:57:41,767 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'usb:v064Ep2100d0300dcEFdsc02dp01ic0Eisc01ip00')
2010-03-31 03:57:41,768 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002C91sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,768 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'platform:pcspkr')
2010-03-31 03:57:41,768 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00001180d0000E832sv0000104Dsd00009067bc0Csc00i10')
2010-03-31 03:57:41,768 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002CAAsv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,768 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d0000D157sv0000004Dsd00000067bc08sc80i00')
2010-03-31 03:57:41,768 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00003B56sv0000104Dsd00009067bc04sc03i00')
2010-03-31 03:57:41,768 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-03-31 03:57:41,768 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00002C99sv0000104Dsd00009067bc06sc00i00')
2010-03-31 03:57:41,768 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2010-03-31 03:57:41,768 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'pci:v00008086d00003B3Csv0000104Dsd00009067bc0Csc03i20')
2010-03-31 03:57:41,768 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18f0cf8> about HardwareID('modalias', 'acpi:PNP0200:')
2010-03-31 03:57:52,931 DEBUG: Installing package: nvidia-current
2010-03-31 03:57:53,282 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-03-31 03:57:53,441 DEBUG: install progress statusChange nvidia-current 0.000000
2010-03-31 03:57:53,441 DEBUG: install progress statusChange nvidia-current 10.000000
2010-03-31 03:57:58,181 DEBUG: install progress statusChange nvidia-current 20.000000
2010-03-31 03:57:58,236 DEBUG: install progress statusChange nvidia-current 30.000000
2010-03-31 03:57:58,320 DEBUG: install progress statusChange nvidia-settings 30.000000
2010-03-31 03:57:58,422 DEBUG: install progress statusChange nvidia-settings 40.000000
2010-03-31 03:57:58,536 DEBUG: install progress statusChange nvidia-settings 50.000000
2010-03-31 03:57:58,591 DEBUG: install progress statusChange nvidia-settings 60.000000
2010-03-31 03:57:58,652 DEBUG: install progress statusChange man-db 60.000000
2010-03-31 03:57:59,229 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-03-31 03:57:59,277 DEBUG: install progress statusChange nvidia-current 60.000000
2010-03-31 03:57:59,443 DEBUG: install progress statusChange nvidia-current 70.000000
2010-03-31 03:58:27,402 DEBUG: install progress statusChange nvidia-current 80.000000
2010-03-31 03:58:27,529 DEBUG: install progress statusChange nvidia-settings 80.000000
2010-03-31 03:58:27,590 DEBUG: install progress statusChange nvidia-settings 90.000000
2010-03-31 03:58:28,316 DEBUG: install progress statusChange nvidia-settings 100.000000
2010-03-31 03:58:29,234 DEBUG: install progress statusChange python-gmenu 100.000000
2010-03-31 03:58:29,962 DEBUG: install progress statusChange python-support 100.000000
2010-03-31 03:58:30,464 DEBUG: Selecting previously deselected package nvidia-current.
(Reading database ... 179390 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_195.36.15-0ubuntu1_amd64.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (195.36.15-0ubuntu1) ...
Loading new nvidia-current-195.36.15 DKMS files...
Building only for 2.6.32-18-generic
Building for architecture x86_64
Building initial module for 2.6.32-18-generic
Done.

nvidia-current.ko:
Running module version sanity check.

```
Another issue, I can't mount an external HD (Samsung S2 portable usb hard drive)The drive works just fine, I used it in a another machine, also in mine using Karmic. I can mount automatically a Wester Digital usb ext hard drive, but nothing happens with this Samsung.
No sol. at the moment in the forum.

No sound from speakers, although sounds works using headphones.
Brightness Fn keys don't working (ok in Karmic)
Sound Fn keys ok
wifi          ok
sd slot       ok
dvd rom       ok
Resume and Hybern NO  
HDMI not used yet
eSata not used yet
touchpad scroll not working since las kernel update
cheers
Seba

---

### Post by ricardo.gloe on 2010-04-02
This is how I solved the Nvidia issue:

1 - Download and install the NVidia Driver and reboot.

2 - on error msg, either go to low-graphics mode or go directly to cli

3 - open and edit your xorg.conf file, so it looks like this:

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "ConnectedMonitor" "DFP-0,DFP-1"
    Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"

``` 

The problem is the driver is unable to identify the correct EDID info, so by adding these lines, it is able to find this info which is located in the path. There is NO need to create your own EDID file using software on ms windows, as some suggest.

Also, by adding "DFP-1", I was able to connect the laptop to a samsung led tv via HDMI. I have video but no sound.

I also couldn't mount an external drive, but the duo bay HD case manufacturer informs it is not compatible with linux. Not sure if that is the problem or if it's LL 10.04. Don't really know what to do...

I had speaker sound, then I just updated some files through the update manager (today!) while I was using earphones that were working also. Now I lost ALL sound!

Hope this works to fix your NVidia.

---

### Post by Niej on 2010-04-03
Thank you!
O brigado!
Now it works just fine!
The downside, lcd brightness doesn't respond, it only
works on the next boot. But I don't complain.
Temp looks good, 41C on idle mode.
It would be nice to keep posting the experience on the upcoming updates for this laptop.
Again, muito brigado!
seba

---

### Post by Niej on 2010-04-03
About not mounting my external HDD (Samsung S2 portable usb HDD)
I found a solution, 
> 
In my case the problem was in /lib/udev/rules.d/85-hdparm.rules
renaming it to .disabled fixed the issue:
Code:

sudo mv /lib/udev/rules.d/85-hdparm.rules /lib/udev/rules.d/85-hdparm.rules.disabled

see [https://bugs.launchpad.net/ubuntu/+s...rm/+bug/515023](https://bugs.launchpad.net/ubuntu/+s...rm/+bug/515023) for reference

Now it works just fine!
One less thing at the moment
cheers.
seba

---

### Post by ricardo.gloe on 2010-04-03
Upgrade to Linux kernel 2.6.33.2 restored analog speaker sound, although the nothing from the earphones. 

On the downside, I can no longer get maximum resolution on a second screen (I was connecting to a LED TV with HDMI). 

Going to try that external HD fix and see if it works!

---

### Post by ricardo.gloe on 2010-04-03
Hey Niej, 

Could you give me a copy of your xorg.conf? 

Somehow I lost it, and the new generated file does not have all the original configurations.

---

### Post by Niej on 2010-04-04
Hi, yes, sure thing.
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Fri Mar 12 02:12:40 PST 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "yes"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "ConnectedMonitor" "DFP-0,DFP-1"
    Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



```

since last update, no vertical scroll nor horizontal scroll.
I think I should add some lines for the touchpad also.
I will look for some info about resuming and hibernating the machine.
cheers.
seba

---

### Post by ricardo.gloe on 2010-04-04
The only difference between my current xorg.conf and yours is the "Emulate3buttons" option is set to "no". I have H and V scoll on the touchpad...

Still working on getting HDMI audio, but I have figured out how to get video over HDMI working adequately, although it requires a manual change to xorg and restart everytime.

---

### Post by Niej on 2010-04-04
Yes, I changed the "Emulate3buttons" option hoping
that would take effect (it has nothing to do with it).
I had gsynaptics before also. The scroll stopped
working since the new kernel installation.
I'm still having sound from headphones, some people
suggest to install a new version of alsa to deal with the
speakers sound.
I'm not so sure about that.
cheers

---

### Post by mghg on 2010-04-20
I have submitted a bug-report concerning the NVIDIA issue described above, see [https://bugs.launchpad.net/bugs/565382](https://bugs.launchpad.net/bugs/565382) . 

My thanks to the solution by ricardo.gloe :)

---

