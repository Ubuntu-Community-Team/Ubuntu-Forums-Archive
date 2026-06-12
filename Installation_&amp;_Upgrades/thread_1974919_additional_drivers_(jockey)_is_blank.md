---
title: "additional drivers (jockey) is blank"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by braingram on 2012-05-06
After updating my machine today to 12.04, the restricted/additional drivers window (jockey) does not list any additional drivers.

I tried running jockey-text and got this:
```
>>> jockey-text
Additional Drivers
Searching for available drivers...
>>>
```

The computer has a nvidia card so I assume that at least those drivers should be listed.

I attempted to attach my jockey.log (and the forums said "Invalid file"). However, it doesn't seem to show any errors.

== jockey.log ==
```
2012-05-06 17:53:25,200 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290>
2012-05-06 17:53:26,768 DEBUG: reading modalias file /lib/modules/3.2.0-24-generic/modules.alias
2012-05-06 17:53:26,838 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-05-06 17:53:26,838 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-05-06 17:53:26,894 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-05-06 17:53:26,903 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-05-06 17:53:26,904 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-05-06 17:53:26,904 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-05-06 17:53:26,904 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-05-06 17:53:26,915 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-05-06 17:53:26,924 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-05-06 17:53:27,046 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-05-06 17:53:27,046 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-05-06 17:53:27,054 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-05-06 17:53:27,054 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-05-06 17:53:27,084 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-05-06 17:53:27,085 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-05-06 17:53:27,097 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-05-06 17:53:27,106 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-05-06 17:53:27,107 DEBUG: fglrx.available: falling back to default
2012-05-06 17:53:27,167 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-06 17:53:27,175 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-05-06 17:53:27,183 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-05-06 17:53:27,184 DEBUG: fglrx.available: falling back to default
2012-05-06 17:53:27,245 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-05-06 17:53:27,246 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-05-06 17:53:27,285 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-05-06 17:53:27,286 DEBUG: Firmware for DVB cards not available
2012-05-06 17:53:27,287 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-05-06 17:53:27,295 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-06 17:53:27,328 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-05-06 17:53:27,329 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-05-06 17:53:27,329 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-05-06 17:53:27,342 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-05-06 17:53:27,351 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-05-06 17:53:27,354 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-05-06 17:53:27,354 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-06 17:53:27,370 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-05-06 17:53:27,371 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-05-06 17:53:27,371 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-06 17:53:27,387 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-05-06 17:53:27,388 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-05-06 17:53:27,389 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-06 17:53:27,395 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-05-06 17:53:27,405 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-05-06 17:53:27,406 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-05-06 17:53:27,406 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-06 17:53:27,413 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-05-06 17:53:27,422 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-05-06 17:53:27,423 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-05-06 17:53:27,423 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-06 17:53:27,430 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-05-06 17:53:27,439 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-05-06 17:53:27,441 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-05-06 17:53:27,441 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-06 17:53:27,441 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-05-06 17:53:27,474 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-05-06 17:53:27,491 DEBUG: Software modem not available
2012-05-06 17:53:27,491 DEBUG: all custom handlers loaded
2012-05-06 17:53:27,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-06 17:53:27,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-05-06 17:53:27,504 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 17:53:27,585 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:27,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:37F85341-4418-4F24-8533-38FFC7295542')
2012-05-06 17:53:27,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-06 17:53:27,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-06 17:53:27,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-05-06 17:53:27,773 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-05-06 17:53:27,773 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:27,773 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'platform:ideapad')
2012-05-06 17:53:27,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 17:53:27,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,D4,D9,E0,E1,E2,F5,F7,ram4,l0,1,2,sfw')
2012-05-06 17:53:27,783 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 17:53:27,783 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:27,783 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 17:53:27,783 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:27,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'usb:v064EpF231d0434dcEFdsc02dp01ic0Eisc02ip00')
2012-05-06 17:53:27,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:PNP0303:')
2012-05-06 17:53:27,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-06 17:53:27,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'platform:regulatory')
2012-05-06 17:53:27,784 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'input:b0003v064EpF231e0434-e0,1,kD4,ramlsfw')
2012-05-06 17:53:27,784 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 17:53:27,784 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:27,784 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 17:53:27,784 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:27,784 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-06 17:53:27,784 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:921A2F40-0DC4-402D-AC18-B48444EF9ED2')
2012-05-06 17:53:27,784 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v000010DEd00000DF6sv000017AAsd00003981bc03sc00i00')
2012-05-06 17:53:27,948 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2012-05-06 17:53:27,948 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:27,948 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2012-05-06 17:53:27,948 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:27,948 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates'}
2012-05-06 17:53:27,972 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-05-06 17:53:27,973 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 17:53:27,948 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-05-06 17:53:27,982 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-05-06 17:53:28,006 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-05-06 17:53:28,007 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 17:53:27,982 DEBUG: ignoring unavailable handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-05-06 17:53:28,007 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2012-05-06 17:53:28,033 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-05-06 17:53:28,033 DEBUG: nvidia_current is not the alternative in use
2012-05-06 17:53:28,007 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-05-06 17:53:28,043 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-05-06 17:53:28,069 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-05-06 17:53:28,070 DEBUG: nvidia_current is not the alternative in use
2012-05-06 17:53:28,044 DEBUG: ignoring unavailable handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-05-06 17:53:28,070 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2012-05-06 17:53:28,095 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-05-06 17:53:28,095 DEBUG: nvidia_current is not the alternative in use
2012-05-06 17:53:28,070 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-05-06 17:53:28,106 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-05-06 17:53:28,131 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-05-06 17:53:28,131 DEBUG: nvidia_current is not the alternative in use
2012-05-06 17:53:28,106 DEBUG: ignoring unavailable handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-05-06 17:53:28,132 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2012-05-06 17:53:28,158 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-05-06 17:53:28,158 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 17:53:28,132 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-05-06 17:53:28,169 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-05-06 17:53:28,194 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-05-06 17:53:28,194 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 17:53:28,169 DEBUG: ignoring unavailable handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-05-06 17:53:28,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-05-06 17:53:28,203 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi'}
2012-05-06 17:53:28,204 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:C12AD361-9FA9-4C74-901F-95CB0945CF3E')
2012-05-06 17:53:28,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:A1799AC5-9429-4529-927E-DFE13736EEBA')
2012-05-06 17:53:28,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-06 17:53:28,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:INT0800:')
2012-05-06 17:53:28,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:A1799ACB-9429-4529-927E-DFE13736EEBA')
2012-05-06 17:53:28,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v00008086d00000116sv000017AAsd00003981bc03sc00i00')
2012-05-06 17:53:28,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2012-05-06 17:53:28,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v000014E4d000016B1sv000017AAsd00003975bc02sc00i00')
2012-05-06 17:53:28,244 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2012-05-06 17:53:28,245 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:PNP0103:')
2012-05-06 17:53:28,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-05-06 17:53:28,247 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-05-06 17:53:28,247 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v0000197Bd00002393sv000017AAsd00003976bc08sc80i00')
2012-05-06 17:53:28,249 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms'}
2012-05-06 17:53:28,249 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFEisc01ip01')
2012-05-06 17:53:28,251 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-05-06 17:53:28,251 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'usb:v064EpF231d0434dcEFdsc02dp01ic0Eisc01ip00')
2012-05-06 17:53:28,251 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-05-06 17:53:28,252 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-06 17:53:28,252 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 17:53:28,252 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:A1799AF2-9429-4529-927E-DFE13736EEBA')
2012-05-06 17:53:28,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-06 17:53:28,252 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 17:53:28,252 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-06 17:53:28,257 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-05-06 17:53:28,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-05-06 17:53:28,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-05-06 17:53:28,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 17:53:28,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 17:53:28,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-05-06 17:53:28,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v0000197Bd00002391sv000017AAsd00003976bc08sc05i01')
2012-05-06 17:53:28,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-05-06 17:53:28,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-05-06 17:53:28,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-06 17:53:28,259 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 17:53:28,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,259 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 17:53:28,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-06 17:53:28,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:1E519311-3E75-4208-B05E-EBE17E3FF41F')
2012-05-06 17:53:28,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr47CN30WW(V2.08):bd08/01/2011:svnLENOVO:pn0855:pvrLenovoIdeaPadY470:rvnLENOVO:rnBaseBoardProductName:rvrBaseBoardVersion:cvnChassisManufacturer:ct10:cvrChassisVersion:')
2012-05-06 17:53:28,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-05-06 17:53:28,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-06 17:53:28,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v0000197Bd00002394sv000017AAsd00003976bc08sc80i00')
2012-05-06 17:53:28,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-05-06 17:53:28,272 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 17:53:28,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,272 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 17:53:28,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-05-06 17:53:28,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-05-06 17:53:28,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icE0isc01ip01')
2012-05-06 17:53:28,272 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-05-06 17:53:28,273 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-05-06 17:53:28,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-05-06 17:53:28,277 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-05-06 17:53:28,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-06 17:53:28,277 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 17:53:28,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:VPC2004:')
2012-05-06 17:53:28,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:A1799AC3-9429-4529-927E-DFE13736EEBA')
2012-05-06 17:53:28,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-06 17:53:28,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-05-06 17:53:28,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-05-06 17:53:28,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:SYN0733:SYN0700:SYN0002:PNP0F13:')
2012-05-06 17:53:28,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-05-06 17:53:28,277 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 17:53:28,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,278 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-06 17:53:28,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,278 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-06 17:53:28,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,278 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-06 17:53:28,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,278 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 17:53:28,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:A1799ACA-9429-4529-927E-DFE13736EEBA')
2012-05-06 17:53:28,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFFiscFFipFF')
2012-05-06 17:53:28,278 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-05-06 17:53:28,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2012-05-06 17:53:28,279 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2012-05-06 17:53:28,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'platform:pcspkr')
2012-05-06 17:53:28,279 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-05-06 17:53:28,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,279 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-05-06 17:53:28,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-05-06 17:53:28,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-05-06 17:53:28,283 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-06 17:53:28,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,283 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-06 17:53:28,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v0000197Bd00002392sv000017AAsd00003976bc08sc80i00')
2012-05-06 17:53:28,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-05-06 17:53:28,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:3ADEBD0F-0C5F-46ED-AB2E-04962B4FDCBC')
2012-05-06 17:53:28,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-05-06 17:53:28,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,E3,EE,F0,ram4,lsfw')
2012-05-06 17:53:28,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 17:53:28,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 17:53:28,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 17:53:28,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'pci:v00001033d00000194sv000017AAsd00003975bc0Csc03i30')
2012-05-06 17:53:28,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:42848006-8886-490E-8C72-2BDCA93A8A09')
2012-05-06 17:53:28,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27e2290> about HardwareID('modalias', 'wmi:E06BDE62-EE75-48F4-A583-B23E69ABF891')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:37F85341-4418-4F24-8533-38FFC7295542')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'platform:ideapad')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,D4,D9,E0,E1,E2,F5,F7,ram4,l0,1,2,sfw')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'usb:v064EpF231d0434dcEFdsc02dp01ic0Eisc02ip00')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:PNP0303:')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'platform:regulatory')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'input:b0003v064EpF231e0434-e0,1,kD4,ramlsfw')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:921A2F40-0DC4-402D-AC18-B48444EF9ED2')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v000010DEd00000DF6sv000017AAsd00003981bc03sc00i00')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-05-06 17:53:28,285 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:C12AD361-9FA9-4C74-901F-95CB0945CF3E')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:A1799AC5-9429-4529-927E-DFE13736EEBA')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:INT0800:')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:A1799ACB-9429-4529-927E-DFE13736EEBA')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v00008086d00000116sv000017AAsd00003981bc03sc00i00')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v000014E4d000016B1sv000017AAsd00003975bc02sc00i00')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:PNP0103:')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v0000197Bd00002393sv000017AAsd00003976bc08sc80i00')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFEisc01ip01')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'usb:v064EpF231d0434dcEFdsc02dp01ic0Eisc01ip00')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:A1799AF2-9429-4529-927E-DFE13736EEBA')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v0000197Bd00002391sv000017AAsd00003976bc08sc05i01')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-06 17:53:28,286 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:1E519311-3E75-4208-B05E-EBE17E3FF41F')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr47CN30WW(V2.08):bd08/01/2011:svnLENOVO:pn0855:pvrLenovoIdeaPadY470:rvnLENOVO:rnBaseBoardProductName:rvrBaseBoardVersion:cvnChassisManufacturer:ct10:cvrChassisVersion:')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v0000197Bd00002394sv000017AAsd00003976bc08sc80i00')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icE0isc01ip01')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:VPC2004:')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:A1799AC3-9429-4529-927E-DFE13736EEBA')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:SYN0733:SYN0700:SYN0002:PNP0F13:')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:A1799ACA-9429-4529-927E-DFE13736EEBA')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'usb:v0489pE00Dd0472dcE0dsc01dp01icFFiscFFipFF')
2012-05-06 17:53:28,287 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2012-05-06 17:53:28,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'platform:pcspkr')
2012-05-06 17:53:28,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-05-06 17:53:28,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-05-06 17:53:28,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v0000197Bd00002392sv000017AAsd00003976bc08sc80i00')
2012-05-06 17:53:28,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:3ADEBD0F-0C5F-46ED-AB2E-04962B4FDCBC')
2012-05-06 17:53:28,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-05-06 17:53:28,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,E3,EE,F0,ram4,lsfw')
2012-05-06 17:53:28,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'pci:v00001033d00000194sv000017AAsd00003975bc0Csc03i30')
2012-05-06 17:53:28,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:42848006-8886-490E-8C72-2BDCA93A8A09')
2012-05-06 17:53:28,288 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2b57c68> about HardwareID('modalias', 'wmi:E06BDE62-EE75-48F4-A583-B23E69ABF891')
2012-05-06 17:53:28,297 DEBUG: Shutting down
```

---

### Post by haresear on 2012-05-06
There are some problems with nVidia proprietary drivers and the 3.2 kernel. If your nVidia card uses legacy drivers (173 or 96), the current nVidia driver versions are incompatible, and will not be offered by jockey.

---

