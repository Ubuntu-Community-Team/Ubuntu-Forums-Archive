---
title: "upgrade to 10.10 and error while ati 3470"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by patka on 2011-01-03
2011-01-03 20:10:30,620 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec>
2011-01-03 20:10:30,652 DEBUG: reading modalias file /lib/modules/2.6.35-24-generic-pae/modules.alias
2011-01-03 20:10:30,841 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-01-03 20:10:30,851 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-01-03 20:10:30,862 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-01-03 20:10:30,903 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-01-03 20:10:30,918 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-01-03 20:10:30,944 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-01-03 20:10:30,947 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-01-03 20:10:30,966 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-01-03 20:10:31,320 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-01-03 20:10:31,425 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-01-03 20:10:31,425 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-01-03 20:10:31,462 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-01-03 20:10:31,463 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-01-03 20:10:31,463 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-01-03 20:10:31,490 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-01-03 20:10:31,491 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-01-03 20:10:31,491 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-01-03 20:10:31,491 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-01-03 20:10:31,612 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-01-03 20:10:31,613 DEBUG: Firmware for DVB cards not available
2011-01-03 20:10:31,613 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-01-03 20:10:31,622 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-01-03 20:10:31,634 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-01-03 20:10:31,634 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-01-03 20:10:31,634 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-01-03 20:10:31,646 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-01-03 20:10:31,712 DEBUG: Software modem not available
2011-01-03 20:10:31,713 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-01-03 20:10:31,786 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 184, in __init__
    raise SystemError, 'does not currently work with xserver 1.9'
SystemError: does not currently work with xserver 1.9
2011-01-03 20:10:31,799 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-01-03 20:10:31,801 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-01-03 20:10:31,811 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-01-03 20:10:31,812 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-01-03 20:10:31,816 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-01-03 20:10:31,818 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-01-03 20:10:31,831 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-01-03 20:10:31,832 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-01-03 20:10:31,837 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-01-03 20:10:31,839 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-01-03 20:10:31,849 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-01-03 20:10:31,850 DEBUG: all custom handlers loaded
2011-01-03 20:10:31,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'pci:v00001039d00000968sv00000000sd00000000bc06sc01i00')
2011-01-03 20:10:31,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-01-03 20:10:32,731 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:32,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-01-03 20:10:32,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-01-03 20:10:32,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'pci:v00001039d00007002sv00001043sd00001B07bc0Csc03i20')
2011-01-03 20:10:32,732 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'input:b0003v1241p1166e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-01-03 20:10:32,732 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:32,732 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'platform:asus_laptop')
2011-01-03 20:10:32,733 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-01-03 20:10:32,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-01-03 20:10:32,760 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:32,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpiNP0B00:')
2011-01-03 20:10:32,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-01-03 20:10:32,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'platform:regulatory')
2011-01-03 20:10:32,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'pci:v00001039d00000671sv00001039sd00000671bc06sc00i00')
2011-01-03 20:10:32,762 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sis_agp', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:32,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpiNP0C02:')
2011-01-03 20:10:32,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpi:device:')
2011-01-03 20:10:32,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'pci:v00001002d000095C4sv00001043sd000019E2bc03sc00i00')
2011-01-03 20:10:33,121 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-01-03 20:10:34,966 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-03 20:10:33,123 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-01-03 20:10:34,966 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:34,966 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpiNP0303NP030B:')
2011-01-03 20:10:34,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpiNP0C01:')
2011-01-03 20:10:34,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpiNP0100:')
2011-01-03 20:10:34,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpiNP0C04:')
2011-01-03 20:10:34,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'pci:v00001039d00001183sv00001043sd00001B07bc01sc01i85')
2011-01-03 20:10:34,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_sis', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:34,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-01-03 20:10:34,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:34,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-01-03 20:10:34,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:34,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-01-03 20:10:34,969 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr203:bd08/14/2008:svnASUSTeKComputerInc.nF5SRvr1.0:rvnPEGATRONCORPORATION:rnF5SR:rvr1.0:cvnASUSTeKComputerInc.:ct10:cvr:')
2011-01-03 20:10:34,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpiNP0800:')
2011-01-03 20:10:34,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-01-03 20:10:34,988 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:34,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'usb:v1241p1166d0270dc00dsc00dp00ic03isc01ip02')
2011-01-03 20:10:34,989 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:34,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-01-03 20:10:34,989 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:34,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-01-03 20:10:34,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-01-03 20:10:34,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'pci:v00001039d00000191sv00001043sd00001815bc02sc00i00')
2011-01-03 20:10:34,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sis190', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:34,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'pci:v0000168Cd0000002Asv00001A3Bsd00001067bc02sc80i00')
2011-01-03 20:10:35,002 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:35,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'platformcspkr')
2011-01-03 20:10:35,003 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:35,003 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:35,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'input:b0011v0002p0007eA3B3-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2011-01-03 20:10:35,004 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:35,004 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:35,004 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:35,004 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpi:ATK0100:')
2011-01-03 20:10:35,004 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'usb:v0BDAp0116d1610dc00dsc00dp00ic08isc06ip50')
2011-01-03 20:10:35,014 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:35,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'pci:v00001039d00007502sv00001043sd00001783bc04sc03i00')
2011-01-03 20:10:35,015 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:35,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'platform:eisa')
2011-01-03 20:10:35,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-01-03 20:10:35,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:35,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:35,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k71,72,73,8C,94,96,98,A3,A4,A5,A6,A9,B7,D4,D7,E2,E3,E5,E6,EC,ED,EE,174,ramlsfw')
2011-01-03 20:10:35,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-03 20:10:35,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa750fec> about HardwareID('modalias', 'acpi:SYN0A04:SYN0A00:SYN0002NP0F03:AUI1307:AUI1303:')
2011-01-03 20:10:35,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'pci:v00001039d00000968sv00000000sd00000000bc06sc01i00')
2011-01-03 20:10:35,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-01-03 20:10:35,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpiNP0000:')
2011-01-03 20:10:35,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpiNP0200:')
2011-01-03 20:10:35,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'pci:v00001039d00007002sv00001043sd00001B07bc0Csc03i20')
2011-01-03 20:10:35,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'input:b0003v1241p1166e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-01-03 20:10:35,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'platform:asus_laptop')
2011-01-03 20:10:35,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-01-03 20:10:35,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-01-03 20:10:35,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpiNP0B00:')
2011-01-03 20:10:35,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-01-03 20:10:35,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'platform:regulatory')
2011-01-03 20:10:35,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'pci:v00001039d00000671sv00001039sd00000671bc06sc00i00')
2011-01-03 20:10:35,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpiNP0C02:')
2011-01-03 20:10:35,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpi:device:')
2011-01-03 20:10:35,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'pci:v00001002d000095C4sv00001043sd000019E2bc03sc00i00')
2011-01-03 20:10:35,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpiNP0303NP030B:')
2011-01-03 20:10:35,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpiNP0C01:')
2011-01-03 20:10:35,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpiNP0100:')
2011-01-03 20:10:35,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpiNP0C04:')
2011-01-03 20:10:35,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'pci:v00001039d00001183sv00001043sd00001B07bc01sc01i85')
2011-01-03 20:10:35,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-01-03 20:10:35,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-01-03 20:10:35,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-01-03 20:10:35,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr203:bd08/14/2008:svnASUSTeKComputerInc.nF5SRvr1.0:rvnPEGATRONCORPORATION:rnF5SR:rvr1.0:cvnASUSTeKComputerInc.:ct10:cvr:')
2011-01-03 20:10:35,030 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpiNP0800:')
2011-01-03 20:10:35,030 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-01-03 20:10:35,030 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'usb:v1241p1166d0270dc00dsc00dp00ic03isc01ip02')
2011-01-03 20:10:35,030 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-01-03 20:10:35,030 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-01-03 20:10:35,030 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-01-03 20:10:35,030 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'pci:v00001039d00000191sv00001043sd00001815bc02sc00i00')
2011-01-03 20:10:35,030 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'pci:v0000168Cd0000002Asv00001A3Bsd00001067bc02sc80i00')
2011-01-03 20:10:35,030 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'platformcspkr')
2011-01-03 20:10:35,031 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'input:b0011v0002p0007eA3B3-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2011-01-03 20:10:35,031 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpi:ATK0100:')
2011-01-03 20:10:35,031 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'usb:v0BDAp0116d1610dc00dsc00dp00ic08isc06ip50')
2011-01-03 20:10:35,031 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'pci:v00001039d00007502sv00001043sd00001783bc04sc03i00')
2011-01-03 20:10:35,031 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'platform:eisa')
2011-01-03 20:10:35,031 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-01-03 20:10:35,031 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k71,72,73,8C,94,96,98,A3,A4,A5,A6,A9,B7,D4,D7,E2,E3,E5,E6,EC,ED,EE,174,ramlsfw')
2011-01-03 20:10:35,031 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa9eb88c> about HardwareID('modalias', 'acpi:SYN0A04:SYN0A00:SYN0002NP0F03:AUI1307:AUI1303:')
2011-01-03 20:10:35,113 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-03 20:10:35,317 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-03 20:10:35,383 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-03 20:24:31,940 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-03 20:24:39,969 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-01-03 20:24:39,969 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-01-03 20:24:39,970 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-01-03 20:25:11,901 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-03 20:25:11,922 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-03 20:25:28,157 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-03 20:25:28,181 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-03 20:25:28,232 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-03 20:25:28,252 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-03 20:25:28,325 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-03 20:25:28,353 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-03 20:32:06,616 DEBUG: Shutting down
and this log file 
/var/log/auth.log.0: Error stating file '/var/log/auth.log.0': No such file or directory
/var/log/daemon.log.0: Error stating file '/var/log/daemon.log.0': No such file or directory
/var/log/btmp: You don't have enough permissions to read the file.
/var/log/debug.0: Error stating file '/var/log/debug.0': No such file or directory
/var/log/kern.log.0: Error stating file '/var/log/kern.log.0': No such file or directory
/var/log/messages.0: Error stating file '/var/log/messages.0': No such file or directory
/var/log/syslog.0: Error stating file '/var/log/syslog.0': No such file or directory

---

