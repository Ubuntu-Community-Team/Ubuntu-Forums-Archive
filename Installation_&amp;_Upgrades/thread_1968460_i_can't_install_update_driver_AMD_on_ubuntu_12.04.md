---
title: "i can't install update driver AMD on ubuntu 12.04"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by vonvon on 2012-04-29
i can't install update driver AMD on ubuntu 12.04
install update error message " sorry, installation of this driver failed. please have a look at the log file for details: /var/log/jockey.log

[HTML]2012-04-28 21:25:35,335 DEBUG: Updating repository indexes...
2012-04-28 21:25:35,664 DEBUG: ... fail!
2012-04-28 21:25:35,915 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ca9488>
2012-04-28 21:25:36,053 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-04-28 21:25:36,252 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-28 21:25:36,260 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-28 21:25:36,346 WARNING: _detect_handlers(): No package repositories available, skipping check
2012-04-28 21:25:36,387 WARNING: new_used_available(): No package repositories available, skipping check
2012-04-28 21:26:27,110 DEBUG: Updating repository indexes...
2012-04-28 21:26:27,340 DEBUG: ... fail!
2012-04-28 21:26:35,290 DEBUG: Shutting down
2012-04-28 22:24:12,967 DEBUG: Updating repository indexes...
2012-04-28 22:24:13,346 DEBUG: ... fail!
2012-04-28 22:24:13,620 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x22e0950>
2012-04-28 22:24:13,797 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-04-28 22:24:13,998 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-28 22:24:14,150 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-28 22:24:14,340 WARNING: _detect_handlers(): No package repositories available, skipping check
2012-04-28 22:24:14,417 WARNING: new_used_available(): No package repositories available, skipping check
2012-04-29 04:33:08,397 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8>
2012-04-29 04:33:11,816 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-04-29 04:33:11,979 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-29 04:33:11,980 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-29 04:33:12,102 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-29 04:33:12,200 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-29 04:33:12,224 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-29 04:33:12,224 DEBUG: fglrx.available: falling back to default
2012-04-29 04:33:12,397 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-29 04:33:12,411 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-29 04:33:12,423 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-29 04:33:12,424 DEBUG: fglrx.available: falling back to default
2012-04-29 04:33:12,496 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-29 04:33:12,497 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-29 04:33:12,510 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-29 04:33:12,511 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-29 04:33:12,548 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-29 04:33:12,549 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-29 04:33:12,561 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-29 04:33:12,570 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-29 04:33:12,572 DEBUG: nvidia.available: falling back to default
2012-04-29 04:33:12,608 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 04:33:12,608 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-29 04:33:12,615 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-29 04:33:12,624 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-29 04:33:12,625 DEBUG: nvidia.available: falling back to default
2012-04-29 04:33:12,701 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-29 04:33:12,708 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-29 04:33:12,717 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-29 04:33:12,718 DEBUG: nvidia.available: falling back to default
2012-04-29 04:33:12,797 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-29 04:33:12,804 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-29 04:33:12,813 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-29 04:33:12,814 DEBUG: nvidia.available: falling back to default
2012-04-29 04:33:12,849 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 04:33:12,850 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-29 04:33:12,856 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-29 04:33:12,865 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-29 04:33:12,866 DEBUG: nvidia.available: falling back to default
2012-04-29 04:33:12,920 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 04:33:12,921 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-29 04:33:12,928 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-29 04:33:12,936 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-29 04:33:12,938 DEBUG: nvidia.available: falling back to default
2012-04-29 04:33:12,976 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 04:33:12,977 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-29 04:33:12,977 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-29 04:33:12,985 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-29 04:33:13,044 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-29 04:33:13,045 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-29 04:33:13,045 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-29 04:33:13,056 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-29 04:33:13,057 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-29 04:33:13,057 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-29 04:33:13,057 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-29 04:33:13,148 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-29 04:33:13,149 DEBUG: Firmware for DVB cards not available
2012-04-29 04:33:13,149 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-29 04:33:13,160 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-29 04:33:13,174 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-29 04:33:13,255 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-29 04:33:13,255 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-29 04:33:13,288 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-29 04:33:13,330 DEBUG: Software modem not available
2012-04-29 04:33:13,330 DEBUG: all custom handlers loaded
2012-04-29 04:33:13,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:TOS1900:')
2012-04-29 04:33:13,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'input:b0003v1C4Fp0003e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-04-29 04:33:13,338 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:33:13,478 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:13,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:33:13,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:13,479 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-29 04:33:13,479 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:TOS1901:')
2012-04-29 04:33:13,479 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001002d00009613sv00001179sd0000FF6Abc03sc00i00')
2012-04-29 04:33:13,994 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-29 04:33:14,025 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-29 04:33:14,026 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:33:13,994 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 04:33:14,037 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-29 04:33:14,046 DEBUG: fglrx.available: falling back to default
2012-04-29 04:33:14,112 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-29 04:33:14,112 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:33:14,080 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 04:33:14,113 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-29 04:33:14,146 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-29 04:33:14,147 DEBUG: fglrx is not the alternative in use
2012-04-29 04:33:14,113 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-29 04:33:14,155 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-29 04:33:14,163 DEBUG: fglrx.available: falling back to default
2012-04-29 04:33:14,250 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-29 04:33:14,251 DEBUG: fglrx is not the alternative in use
2012-04-29 04:33:14,197 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-29 04:33:14,251 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-29 04:33:14,251 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-04-29 04:33:14,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 04:33:14,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-29 04:33:14,277 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:33:14,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,277 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:33:14,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2012-04-29 04:33:14,299 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek'}
2012-04-29 04:33:14,300 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,300 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-29 04:33:14,300 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-29 04:33:14,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'platform:regulatory')
2012-04-29 04:33:14,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-29 04:33:14,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001022d00009600sv00001179sd0000FF6Abc06sc00i00')
2012-04-29 04:33:14,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001179sd0000FF6Abc04sc03i00')
2012-04-29 04:33:14,328 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-29 04:33:14,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,329 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-29 04:33:14,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-29 04:33:14,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-29 04:33:14,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-04-29 04:33:14,330 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-04-29 04:33:14,330 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001179sd0000FF6Abc01sc01i8a')
2012-04-29 04:33:14,336 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-04-29 04:33:14,336 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-29 04:33:14,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2012-04-29 04:33:14,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2012-04-29 04:33:14,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00ic08isc06ip50')
2012-04-29 04:33:14,494 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-29 04:33:14,495 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc02ip00')
2012-04-29 04:33:14,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-29 04:33:14,502 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:33:14,502 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-29 04:33:14,502 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:33:14,502 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-29 04:33:14,503 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:33:14,503 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-29 04:33:14,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2012-04-29 04:33:14,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k100,101,102,103,110,111,145,14A,ra0,1,18,1C,mlsfw')
2012-04-29 04:33:14,504 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:33:14,504 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,504 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-29 04:33:14,504 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,504 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-29 04:33:14,504 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,504 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:33:14,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-29 04:33:14,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvr1.80:bd09/01/2009:svnTOSHIBA:pnSatelliteL300D:pvrPSLC8A-02200Y:rvnTOSHIBA:rnPortablePC:rvrBaseBoardVersion:cvnAMD:ct10:cvrNone:')
2012-04-29 04:33:14,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-29 04:33:14,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2012-04-29 04:33:14,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,80,8E,95,96,98,9B,A3,A4,A5,CD,E0,E1,E2,E3,E4,EC,EE,F0,1A2,1A3,1A4,1D0,212,ram4,lsfw')
2012-04-29 04:33:14,528 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:33:14,529 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,529 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:33:14,529 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc01ip00')
2012-04-29 04:33:14,530 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-29 04:33:14,530 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'usb:v1C4Fp0003d0110dc00dsc00dp00ic03isc01ip02')
2012-04-29 04:33:14,531 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-29 04:33:14,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,531 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-04-29 04:33:14,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 04:33:14,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001179sd0000FF6Abc0Csc03i20')
2012-04-29 04:33:14,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'input:b0003v04F2pB070e0834-e0,1,kD4,ramlsfw')
2012-04-29 04:33:14,538 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:33:14,538 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,538 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:33:14,538 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,539 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:SYN1913:SYN0700:SYN0002:PNP0F13:')
2012-04-29 04:33:14,539 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001002d00004390sv00001179sd0000FF6Abc01sc06i01')
2012-04-29 04:33:14,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-29 04:33:14,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'usb:v0BDAp8198d0200dc00dsc00dp00icFFiscFFipFF')
2012-04-29 04:33:14,545 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rtl8187'}
2012-04-29 04:33:14,545 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rtl8187', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-29 04:33:14,546 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:33:14,546 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,546 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:33:14,546 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-29 04:33:14,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00icFFiscFFipFF')
2012-04-29 04:33:14,549 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'option'}
2012-04-29 04:33:14,549 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'platform:pcspkr')
2012-04-29 04:33:14,550 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-29 04:33:14,550 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,550 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-29 04:33:14,550 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2012-04-29 04:33:14,551 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-04-29 04:33:14,551 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001002d00004385sv00001179sd0000FF6Abc0Csc05i00')
2012-04-29 04:33:14,557 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-04-29 04:33:14,557 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,557 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-04-29 04:33:14,558 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,558 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i00')
2012-04-29 04:33:14,564 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-04-29 04:33:14,564 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,564 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-29 04:33:14,576 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-29 04:33:14,576 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,576 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-29 04:33:14,576 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-29 04:33:14,577 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:33:14,577 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,577 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:33:14,577 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:33:14,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001179sd0000FF6Abc06sc01i00')
2012-04-29 04:33:14,583 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2525ea8> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-29 04:33:14,584 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:TOS1900:')
2012-04-29 04:33:14,584 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'input:b0003v1C4Fp0003e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-04-29 04:33:14,584 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-29 04:33:14,584 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:TOS1901:')
2012-04-29 04:33:14,584 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001002d00009613sv00001179sd0000FF6Abc03sc00i00')
2012-04-29 04:33:14,584 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-04-29 04:33:14,584 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 04:33:14,584 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-29 04:33:14,584 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2012-04-29 04:33:14,585 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-29 04:33:14,585 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'platform:regulatory')
2012-04-29 04:33:14,585 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-29 04:33:14,585 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001022d00009600sv00001179sd0000FF6Abc06sc00i00')
2012-04-29 04:33:14,585 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001002d00004383sv00001179sd0000FF6Abc04sc03i00')
2012-04-29 04:33:14,585 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-29 04:33:14,585 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-29 04:33:14,585 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-04-29 04:33:14,585 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001179sd0000FF6Abc01sc01i8a')
2012-04-29 04:33:14,585 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-29 04:33:14,586 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2012-04-29 04:33:14,586 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2012-04-29 04:33:14,586 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00ic08isc06ip50')
2012-04-29 04:33:14,586 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc02ip00')
2012-04-29 04:33:14,586 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-29 04:33:14,586 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-29 04:33:14,586 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-29 04:33:14,586 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-29 04:33:14,586 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2012-04-29 04:33:14,586 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k100,101,102,103,110,111,145,14A,ra0,1,18,1C,mlsfw')
2012-04-29 04:33:14,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-29 04:33:14,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvr1.80:bd09/01/2009:svnTOSHIBA:pnSatelliteL300D:pvrPSLC8A-02200Y:rvnTOSHIBA:rnPortablePC:rvrBaseBoardVersion:cvnAMD:ct10:cvrNone:')
2012-04-29 04:33:14,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-29 04:33:14,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2012-04-29 04:33:14,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,80,8E,95,96,98,9B,A3,A4,A5,CD,E0,E1,E2,E3,E4,EC,EE,F0,1A2,1A3,1A4,1D0,212,ram4,lsfw')
2012-04-29 04:33:14,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc01ip00')
2012-04-29 04:33:14,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'usb:v1C4Fp0003d0110dc00dsc00dp00ic03isc01ip02')
2012-04-29 04:33:14,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 04:33:14,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001002d00004396sv00001179sd0000FF6Abc0Csc03i20')
2012-04-29 04:33:14,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'input:b0003v04F2pB070e0834-e0,1,kD4,ramlsfw')
2012-04-29 04:33:14,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:SYN1913:SYN0700:SYN0002:PNP0F13:')
2012-04-29 04:33:14,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001002d00004390sv00001179sd0000FF6Abc01sc06i01')
2012-04-29 04:33:14,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-29 04:33:14,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'usb:v0BDAp8198d0200dc00dsc00dp00icFFiscFFipFF')
2012-04-29 04:33:14,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-29 04:33:14,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-29 04:33:14,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00icFFiscFFipFF')
2012-04-29 04:33:14,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'platform:pcspkr')
2012-04-29 04:33:14,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2012-04-29 04:33:14,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001002d00004385sv00001179sd0000FF6Abc0Csc05i00')
2012-04-29 04:33:14,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i00')
2012-04-29 04:33:14,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-29 04:33:14,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-29 04:33:14,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001179sd0000FF6Abc06sc01i00')
2012-04-29 04:33:14,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28953b0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-29 04:33:14,641 DEBUG: handler xorg:fglrx_updates previously unseen
2012-04-29 04:33:14,642 DEBUG: handler xorg:fglrx previously unseen
2012-04-29 04:33:14,642 DEBUG: writing back check cache /var/cache/jockey/check
2012-04-29 04:33:14,670 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-29 04:33:14,671 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:33:14,704 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-29 04:33:14,705 DEBUG: fglrx is not the alternative in use
2012-04-29 04:33:14,766 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-29 04:33:14,766 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:47:53,307 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-29 04:47:53,308 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:47:53,453 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-29 04:47:53,454 DEBUG: fglrx is not the alternative in use
2012-04-29 04:47:53,539 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-29 04:47:53,541 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:47:53,696 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-29 04:47:53,697 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:47:53,803 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-29 04:47:53,804 DEBUG: fglrx is not the alternative in use
2012-04-29 04:47:56,320 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-29 04:47:56,320 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:48:01,181 DEBUG: Installing package: fglrx-updates
2012-04-29 04:48:02,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-04-29 04:48:02,367 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-04-29 04:48:02,799 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-04-29 04:48:03,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-04-29 04:48:03,563 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-04-29 04:48:04,066 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.054290
2012-04-29 04:48:04,567 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.092008
2012-04-29 04:48:04,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.104421
2012-04-29 04:48:04,758 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.104421
2012-04-29 04:48:04,758 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.104811
2012-04-29 04:48:05,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.199585
2012-04-29 04:48:05,205 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.200593
2012-04-29 04:48:05,643 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.313163
2012-04-29 04:48:05,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.317117
2012-04-29 04:48:06,148 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.545311
2012-04-29 04:48:06,650 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.798022
2012-04-29 04:48:07,151 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.160115
2012-04-29 04:48:07,654 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.539181
2012-04-29 04:48:08,156 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.999341
2012-04-29 04:48:08,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.431212
2012-04-29 04:48:09,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.568883
2012-04-29 04:48:09,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.897030
2012-04-29 04:48:10,164 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.277982
2012-04-29 04:48:10,666 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.674022
2012-04-29 04:48:11,167 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.102121
2012-04-29 04:48:11,669 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.226591
2012-04-29 04:48:12,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.226591
2012-04-29 04:48:12,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.226591
2012-04-29 04:48:13,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.226591
2012-04-29 04:48:13,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.226591
2012-04-29 04:48:14,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.264309
2012-04-29 04:48:14,565 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.520240
2012-04-29 04:48:14,568 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.520240
2012-04-29 04:48:14,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.520240
2012-04-29 04:48:14,576 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.590671
2012-04-29 04:48:14,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.590671
2012-04-29 04:48:14,578 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.590671
2012-04-29 04:48:15,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.080307
2012-04-29 04:48:15,583 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.148200
2012-04-29 04:48:16,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.546125
2012-04-29 04:48:16,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.911990
2012-04-29 04:48:17,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.309915
2012-04-29 04:48:17,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.832310
2012-04-29 04:48:18,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.832310
2012-04-29 04:48:18,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.832310
2012-04-29 04:48:19,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.832310
2012-04-29 04:48:19,601 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.190159
2012-04-29 04:48:20,103 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.731413
2012-04-29 04:48:20,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.231177
2012-04-29 04:48:21,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.568753
2012-04-29 04:48:21,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.932732
2012-04-29 04:48:22,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.206188
2012-04-29 04:48:22,617 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.206188
2012-04-29 04:48:23,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.206188
2012-04-29 04:48:23,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.273608
2012-04-29 04:48:24,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.675305
2012-04-29 04:48:24,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.680963
2012-04-29 04:48:25,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 13.009110
2012-04-29 04:48:25,628 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 13.520189
2012-04-29 04:48:26,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 14.052014
2012-04-29 04:48:26,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 14.568751
2012-04-29 04:48:27,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 15.098689
2012-04-29 04:48:27,635 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 15.622970
2012-04-29 04:48:28,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.141593
2012-04-29 04:48:28,638 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.601753
2012-04-29 04:48:29,140 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.056255
2012-04-29 04:48:29,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.303308
2012-04-29 04:48:30,144 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.821931
2012-04-29 04:48:30,646 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.357527
2012-04-29 04:48:31,147 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.823345
2012-04-29 04:48:31,649 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.961016
2012-04-29 04:48:32,150 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 19.245787
2012-04-29 04:48:32,652 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 19.605994
2012-04-29 04:48:33,154 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.035980
2012-04-29 04:48:33,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.356583
2012-04-29 04:48:34,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.369784
2012-04-29 04:48:34,660 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.660213
2012-04-29 04:48:35,162 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.044937
2012-04-29 04:48:35,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.469265
2012-04-29 04:48:36,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.887935
2012-04-29 04:48:36,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.893593
2012-04-29 04:48:37,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 22.351867
2012-04-29 04:48:37,671 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 22.893121
2012-04-29 04:48:38,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 23.396656
2012-04-29 04:48:38,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 23.826642
2012-04-29 04:48:39,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 24.264171
2012-04-29 04:48:39,677 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 24.711130
2012-04-29 04:48:40,179 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 24.875203
2012-04-29 04:48:40,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.242954
2012-04-29 04:48:41,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.648423
2012-04-29 04:48:41,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.087838
2012-04-29 04:48:42,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.314146
2012-04-29 04:48:42,688 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.314146
2012-04-29 04:48:43,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.314146
2012-04-29 04:48:43,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.314146
2012-04-29 04:48:44,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.314146
2012-04-29 04:48:44,695 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.200048
2012-04-29 04:48:45,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.200048
2012-04-29 04:48:45,698 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.288685
2012-04-29 04:48:46,200 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.654550
2012-04-29 04:48:46,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.745073
2012-04-29 04:48:47,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.469260
2012-04-29 04:48:47,706 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.710655
2012-04-29 04:48:48,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.710655
2012-04-29 04:48:48,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.710655
2012-04-29 04:48:49,210 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.710655
2012-04-29 04:48:49,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.710655
2012-04-29 04:48:50,214 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.710655
2012-04-29 04:48:50,716 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.897359
2012-04-29 04:48:51,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.596557
2012-04-29 04:48:51,719 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.596557
2012-04-29 04:48:52,222 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.792691
2012-04-29 04:48:52,724 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.124609
2012-04-29 04:48:53,225 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.541394
2012-04-29 04:48:53,727 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.920460
2012-04-29 04:48:54,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.920460
2012-04-29 04:48:54,729 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.920460
2012-04-29 04:48:55,231 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.920460
2012-04-29 04:48:55,732 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.920460
2012-04-29 04:48:56,234 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.798818
2012-04-29 04:48:56,736 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.806361
2012-04-29 04:48:57,238 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.089247
2012-04-29 04:48:57,739 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.472085
2012-04-29 04:48:58,241 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.898299
2012-04-29 04:48:58,743 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.318855
2012-04-29 04:48:59,245 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.445210
2012-04-29 04:48:59,747 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.939316
2012-04-29 04:49:00,249 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.459825
2012-04-29 04:49:00,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.855864
2012-04-29 04:49:01,253 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.317910
2012-04-29 04:49:01,755 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.655487
2012-04-29 04:49:02,257 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.659259
2012-04-29 04:49:02,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.013808
2012-04-29 04:49:03,259 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.377787
2012-04-29 04:49:03,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.790800
2012-04-29 04:49:04,262 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.062369
2012-04-29 04:49:04,763 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.062369
2012-04-29 04:49:05,265 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.062369
2012-04-29 04:49:05,767 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.062369
2012-04-29 04:49:06,271 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.518286
2012-04-29 04:49:06,773 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.752137
2012-04-29 04:49:07,274 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.901124
2012-04-29 04:49:07,776 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 42.285847
2012-04-29 04:49:08,278 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 42.696974
2012-04-29 04:49:08,780 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.128846
2012-04-29 04:49:09,282 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.470194
2012-04-29 04:49:09,784 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.632381
2012-04-29 04:49:10,286 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.013333
2012-04-29 04:49:10,788 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.405601
2012-04-29 04:49:11,290 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.850674
2012-04-29 04:49:11,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.314606
2012-04-29 04:49:12,294 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.318377
2012-04-29 04:49:12,795 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.391928
2012-04-29 04:49:13,297 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.640867
2012-04-29 04:49:13,799 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.963356
2012-04-29 04:49:14,301 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.348080
2012-04-29 04:49:14,803 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.774293
2012-04-29 04:49:15,305 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.287259
2012-04-29 04:49:15,807 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.430587
2012-04-29 04:49:16,309 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.783251
2012-04-29 04:49:16,811 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.160431
2012-04-29 04:49:17,313 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.577215
2012-04-29 04:49:17,815 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.990228
2012-04-29 04:49:18,317 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.990228
2012-04-29 04:49:18,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.990228
2012-04-29 04:49:19,323 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.990228
2012-04-29 04:49:19,868 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.056235
2012-04-29 04:49:20,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.417856
2012-04-29 04:49:20,873 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.417856
2012-04-29 04:49:21,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.417856
2012-04-29 04:49:21,879 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 51.721014
2012-04-29 04:49:22,381 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.184945
2012-04-29 04:49:22,881 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.256610
2012-04-29 04:49:23,383 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.680938
2012-04-29 04:49:23,885 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.680938
2012-04-29 04:49:24,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.680938
2012-04-29 04:49:24,890 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.746944
2012-04-29 04:49:25,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.782304
2012-04-29 04:49:25,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.248122
2012-04-29 04:49:26,395 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.676221
2012-04-29 04:49:26,896 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.913845
2012-04-29 04:49:27,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.202388
2012-04-29 04:49:27,899 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.581454
2012-04-29 04:49:28,402 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.039728
2012-04-29 04:49:28,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.316956
2012-04-29 04:49:29,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.697908
2012-04-29 04:49:29,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.131665
2012-04-29 04:49:30,409 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.520161
2012-04-29 04:49:30,911 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.738926
2012-04-29 04:49:31,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.108563
2012-04-29 04:49:31,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.540434
2012-04-29 04:49:32,417 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.859151
2012-04-29 04:49:32,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.059057
2012-04-29 04:49:33,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.447553
2012-04-29 04:49:33,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.864337
2012-04-29 04:49:34,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.222658
2012-04-29 04:49:34,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.481027
2012-04-29 04:49:35,428 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.871408
2012-04-29 04:49:35,930 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.322139
2012-04-29 04:49:36,432 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.535246
2012-04-29 04:49:36,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.797386
2012-04-29 04:49:37,436 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.170795
2012-04-29 04:49:37,938 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.591351
2012-04-29 04:49:38,440 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.994934
2012-04-29 04:49:38,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.000591
2012-04-29 04:49:39,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.275933
2012-04-29 04:49:39,946 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.662543
2012-04-29 04:49:40,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.066126
2012-04-29 04:49:40,950 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.541373
2012-04-29 04:49:41,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.565890
2012-04-29 04:49:41,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.565890
2012-04-29 04:49:42,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.565890
2012-04-29 04:49:42,957 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.565890
2012-04-29 04:49:43,459 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.523456
2012-04-29 04:49:43,961 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.040193
2012-04-29 04:49:44,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.555044
2012-04-29 04:49:44,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.086868
2012-04-29 04:49:45,467 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.609263
2012-04-29 04:49:45,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.137316
2012-04-29 04:49:46,470 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.644623
2012-04-29 04:49:46,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.176447
2012-04-29 04:49:47,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.702614
2012-04-29 04:49:47,975 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.221237
2012-04-29 04:49:48,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.758719
2012-04-29 04:49:48,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.260369
2012-04-29 04:49:49,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.794079
2012-04-29 04:49:49,983 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.327789
2012-04-29 04:49:50,485 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.863385
2012-04-29 04:49:50,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.348062
2012-04-29 04:49:51,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.727128
2012-04-29 04:49:51,992 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.430569
2012-04-29 04:49:52,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.945421
2012-04-29 04:49:52,995 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.471587
2012-04-29 04:49:53,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.997754
2012-04-29 04:49:53,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.497518
2012-04-29 04:49:54,501 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.046315
2012-04-29 04:49:55,003 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.580025
2012-04-29 04:49:55,504 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.089219
2012-04-29 04:49:56,006 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.621043
2012-04-29 04:49:56,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.100062
2012-04-29 04:49:57,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.563994
2012-04-29 04:49:57,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.009067
2012-04-29 04:49:58,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.456025
2012-04-29 04:49:58,515 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.852065
2012-04-29 04:49:59,016 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 82.227359
2012-04-29 04:49:59,518 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 82.636600
2012-04-29 04:50:00,020 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.077901
2012-04-29 04:50:00,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.509772
2012-04-29 04:50:01,023 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.869979
2012-04-29 04:50:01,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.869979
2012-04-29 04:50:02,028 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.869979
2012-04-29 04:50:02,529 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.869979
2012-04-29 04:50:03,031 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.869979
2012-04-29 04:50:03,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.049140
2012-04-29 04:50:04,036 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.049140
2012-04-29 04:50:04,537 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.049140
2012-04-29 04:50:05,039 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.049140
2012-04-29 04:50:05,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.049140
2012-04-29 04:50:06,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.049140
2012-04-29 04:50:06,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.049140
2012-04-29 04:50:07,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.049140
2012-04-29 04:50:07,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.049140
2012-04-29 04:50:08,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.049140
2012-04-29 04:50:08,553 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.292421
2012-04-29 04:50:09,054 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.884122
2012-04-29 04:50:09,556 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.895438
2012-04-29 04:50:10,058 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.942585
2012-04-29 04:50:10,560 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.014250
2012-04-29 04:50:11,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.085914
2012-04-29 04:50:11,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.161350
2012-04-29 04:50:12,066 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.280162
2012-04-29 04:50:12,568 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.387658
2012-04-29 04:50:13,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.468752
2012-04-29 04:50:13,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.568705
2012-04-29 04:50:14,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.706375
2012-04-29 04:50:14,575 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.851590
2012-04-29 04:50:15,077 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.979831
2012-04-29 04:50:15,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.158992
2012-04-29 04:50:16,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.402273
2012-04-29 04:50:16,583 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.632353
2012-04-29 04:50:17,085 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.907695
2012-04-29 04:50:17,586 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.224526
2012-04-29 04:50:18,088 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.577190
2012-04-29 04:50:18,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.907223
2012-04-29 04:50:19,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.207081
2012-04-29 04:50:19,594 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.591805
2012-04-29 04:50:20,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.029334
2012-04-29 04:50:20,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.344280
2012-04-29 04:50:21,098 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.589447
2012-04-29 04:50:21,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.977943
2012-04-29 04:50:22,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.385298
2012-04-29 04:50:22,604 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.934095
2012-04-29 04:50:23,105 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.969927
2012-04-29 04:50:23,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.969927
2012-04-29 04:50:24,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.969927
2012-04-29 04:50:24,240 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.284541
2012-04-29 04:50:24,243 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.284541
2012-04-29 04:50:24,246 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.284541
2012-04-29 04:50:24,748 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.308515
2012-04-29 04:50:25,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.314173
2012-04-29 04:50:25,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.470702
2012-04-29 04:50:26,253 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.742272
2012-04-29 04:50:26,754 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.055332
2012-04-29 04:50:27,256 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.457029
2012-04-29 04:50:27,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.941706
2012-04-29 04:50:28,259 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.196302
2012-04-29 04:50:28,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.384893
2012-04-29 04:50:29,261 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.767731
2012-04-29 04:50:29,763 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.173199
2012-04-29 04:50:30,265 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.663534
2012-04-29 04:50:30,766 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.769144
2012-04-29 04:50:31,268 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.921902
2012-04-29 04:50:31,770 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.310398
2012-04-29 04:50:32,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.727182
2012-04-29 04:50:32,774 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.155282
2012-04-29 04:50:33,276 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.560751
2012-04-29 04:50:33,778 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.704079
2012-04-29 04:50:34,280 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.177441
2012-04-29 04:50:34,782 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.671547
2012-04-29 04:50:35,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 100.000000
2012-04-29 04:50:35,997 DEBUG: install progress dpkg-exec 0.000000
2012-04-29 04:50:36,590 DEBUG: install progress patch 0.000000
2012-04-29 04:50:36,591 DEBUG: install progress patch 2.857140
2012-04-29 04:50:36,973 DEBUG: install progress patch 5.714290
2012-04-29 04:50:37,042 DEBUG: install progress patch 8.571430
2012-04-29 04:50:37,416 DEBUG: install progress dkms 8.571430
2012-04-29 04:50:37,518 DEBUG: install progress dkms 11.428600
2012-04-29 04:50:38,038 DEBUG: install progress dkms 14.285700
2012-04-29 04:50:38,110 DEBUG: install progress dkms 17.142900
2012-04-29 04:50:38,462 DEBUG: install progress fakeroot 17.142900
2012-04-29 04:50:38,465 DEBUG: install progress fakeroot 20.000000
2012-04-29 04:50:38,820 DEBUG: install progress fakeroot 22.857100
2012-04-29 04:50:38,873 DEBUG: install progress fakeroot 25.714300
2012-04-29 04:50:39,301 DEBUG: install progress libc6-i386 25.714300
2012-04-29 04:50:39,403 DEBUG: install progress libc6-i386 28.571400
2012-04-29 04:50:40,196 DEBUG: install progress libc6-i386 31.428600
2012-04-29 04:50:40,250 DEBUG: install progress libc6-i386 34.285700
2012-04-29 04:50:40,644 DEBUG: install progress lib32gcc1 34.285700
2012-04-29 04:50:40,745 DEBUG: install progress lib32gcc1 37.142900
2012-04-29 04:50:40,870 DEBUG: install progress lib32gcc1 40.000000
2012-04-29 04:50:40,924 DEBUG: install progress lib32gcc1 42.857100
2012-04-29 04:50:41,377 DEBUG: install progress fglrx-updates 42.857100
2012-04-29 04:50:41,478 DEBUG: install progress fglrx-updates 45.714300
2012-04-29 04:50:49,998 DEBUG: install progress fglrx-updates 48.571400
2012-04-29 04:50:50,065 DEBUG: install progress fglrx-updates 51.428600
2012-04-29 04:50:50,291 DEBUG: install progress fglrx-amdcccle-updates 51.428600
2012-04-29 04:50:50,392 DEBUG: install progress fglrx-amdcccle-updates 54.285700
2012-04-29 04:50:51,050 DEBUG: install progress fglrx-amdcccle-updates 57.142900
2012-04-29 04:50:51,127 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2012-04-29 04:50:51,214 DEBUG: install progress man-db 60.000000
2012-04-29 04:50:54,276 DEBUG: install progress ureadahead 60.000000
2012-04-29 04:50:54,726 DEBUG: install progress dpkg-exec 60.000000
2012-04-29 04:50:54,795 DEBUG: install progress patch 60.000000
2012-04-29 04:50:54,891 DEBUG: install progress patch 62.857100
2012-04-29 04:50:54,971 DEBUG: install progress patch 65.714300
2012-04-29 04:50:55,041 DEBUG: install progress dkms 65.714300
2012-04-29 04:50:55,995 DEBUG: install progress dkms 68.571400
2012-04-29 04:50:56,078 DEBUG: install progress dkms 71.428600
2012-04-29 04:50:56,143 DEBUG: install progress fakeroot 71.428600
2012-04-29 04:50:56,225 DEBUG: install progress fakeroot 74.285700
2012-04-29 04:50:57,474 DEBUG: install progress fakeroot 77.142900
2012-04-29 04:50:57,552 DEBUG: install progress libc6-i386 77.142900
2012-04-29 04:50:57,667 DEBUG: install progress libc6-i386 80.000000
2012-04-29 04:50:57,819 DEBUG: install progress libc6-i386 82.857100
2012-04-29 04:50:57,956 DEBUG: install progress lib32gcc1 82.857100
2012-04-29 04:50:58,036 DEBUG: install progress lib32gcc1 85.714300
2012-04-29 04:50:58,177 DEBUG: install progress lib32gcc1 88.571400
2012-04-29 04:50:58,267 DEBUG: install progress fglrx-updates 88.571400
2012-04-29 04:50:58,568 DEBUG: install progress fglrx-updates 91.428600
2012-04-29 04:51:48,117 DEBUG: install progress fglrx-updates 94.285700
2012-04-29 04:51:48,451 DEBUG: install progress bamfdaemon 94.285700
2012-04-29 04:51:48,712 DEBUG: install progress fglrx-amdcccle-updates 94.285700
2012-04-29 04:51:48,815 DEBUG: install progress fglrx-amdcccle-updates 97.142900
2012-04-29 04:51:48,895 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-04-29 04:51:48,976 DEBUG: install progress libc-bin 100.000000
2012-04-29 04:51:49,231 DEBUG: install progress initramfs-tools 100.000000
2012-04-29 04:52:22,179 DEBUG: Selecting previously unselected package patch.
(Reading database ... 157427 files and directories currently installed.)
Unpacking patch (from .../patch_2.6.1-3_amd64.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_amd64.deb) ...
Selecting previously unselected package libc6-i386.
Unpacking libc6-i386 (from .../libc6-i386_2.15-0ubuntu10_amd64.deb) ...
Selecting previously unselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up patch (2.6.1-3) ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libc6-i386 (2.15-0ubuntu10) ...
Setting up lib32gcc1 (1:4.6.3-1ubuntu5) ...
Setting up fglrx-updates (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-23-generic
Building for architecture x86_64
Building initial module for 3.2.0-23-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-23-generic/updates/dkms/

depmod...........

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic

2012-04-29 04:52:22,643 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-04-29 04:53:07,286 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:07,287 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:07,382 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:07,383 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:07,697 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:07,699 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:53:07,833 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:07,834 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:07,924 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:07,925 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:08,072 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:08,073 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:08,115 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:08,116 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:08,183 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:08,184 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:53:08,767 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:08,767 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:08,820 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:08,822 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:12,913 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:12,914 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:13,008 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:13,009 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:13,152 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:13,153 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:53:13,292 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:13,293 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:13,388 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:13,389 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:13,548 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:13,550 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:13,644 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:13,645 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:13,777 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:13,778 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:53:15,481 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:15,482 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:15,575 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:53:15,577 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:53:20,835 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-04-29 04:54:01,781 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:01,782 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:01,881 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:01,882 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:09,967 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:09,968 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:10,063 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:10,064 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:10,206 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:10,207 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:54:10,343 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:10,345 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:10,440 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:10,441 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:10,592 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:10,593 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:10,688 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:10,689 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:10,820 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:10,821 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:54:12,056 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:12,057 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:54:12,148 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:12,148 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:54:13,319 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:13,320 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:13,415 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:13,416 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:14,551 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:14,552 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:14,639 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:14,640 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:15,744 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:15,745 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:54:16,708 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:16,708 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:16,747 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:16,747 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:17,425 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:17,426 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:54:19,614 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:19,615 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:19,708 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:19,709 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:21,767 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:21,768 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:21,863 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:54:21,864 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:54:22,481 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-04-29 04:55:03,370 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:55:03,372 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:55:03,467 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:55:03,468 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:21,143 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:21,143 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:21,193 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:21,194 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:21,337 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:21,339 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:56:21,478 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:21,480 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:21,575 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:21,576 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:21,728 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:21,729 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:21,822 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:21,823 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:21,959 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:21,960 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:56:24,685 DEBUG: Shutting down
2012-04-29 04:56:35,447 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0>
2012-04-29 04:56:38,893 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-04-29 04:56:39,048 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-29 04:56:39,048 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-29 04:56:39,178 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-29 04:56:39,263 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-29 04:56:39,264 DEBUG: fglrx.available: falling back to default
2012-04-29 04:56:39,495 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-29 04:56:39,506 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-29 04:56:39,519 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-29 04:56:39,520 DEBUG: fglrx.available: falling back to default
2012-04-29 04:56:39,664 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-29 04:56:39,665 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-29 04:56:39,686 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-29 04:56:39,687 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-29 04:56:39,753 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-29 04:56:39,755 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-29 04:56:39,781 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-29 04:56:39,807 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-29 04:56:39,834 DEBUG: nvidia.available: falling back to default
2012-04-29 04:56:39,902 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 04:56:39,903 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-29 04:56:39,920 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-29 04:56:39,934 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-29 04:56:39,937 DEBUG: nvidia.available: falling back to default
2012-04-29 04:56:40,081 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-29 04:56:40,100 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-29 04:56:40,132 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-29 04:56:40,135 DEBUG: nvidia.available: falling back to default
2012-04-29 04:56:40,274 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-29 04:56:40,293 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-29 04:56:40,320 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-29 04:56:40,324 DEBUG: nvidia.available: falling back to default
2012-04-29 04:56:40,397 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 04:56:40,398 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-29 04:56:40,417 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-29 04:56:40,443 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-29 04:56:40,446 DEBUG: nvidia.available: falling back to default
2012-04-29 04:56:40,513 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 04:56:40,514 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-29 04:56:40,539 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-29 04:56:40,565 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-29 04:56:40,568 DEBUG: nvidia.available: falling back to default
2012-04-29 04:56:40,647 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 04:56:40,648 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-29 04:56:40,648 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-29 04:56:40,672 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-29 04:56:40,748 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-29 04:56:40,749 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-29 04:56:40,750 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-29 04:56:40,762 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-29 04:56:40,764 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-29 04:56:40,765 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-29 04:56:40,766 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-29 04:56:40,888 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-29 04:56:40,891 DEBUG: Firmware for DVB cards not available
2012-04-29 04:56:40,891 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-29 04:56:40,921 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-29 04:56:40,951 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-29 04:56:41,068 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-29 04:56:41,069 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-29 04:56:41,140 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-29 04:56:41,250 DEBUG: Software modem not available
2012-04-29 04:56:41,251 DEBUG: all custom handlers loaded
2012-04-29 04:56:41,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:TOS1900:')
2012-04-29 04:56:41,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'input:b0003v1C4Fp0003e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-04-29 04:56:41,266 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:56:41,392 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:41,393 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:56:41,393 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:41,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-29 04:56:41,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:TOS1901:')
2012-04-29 04:56:41,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001002d00009613sv00001179sd0000FF6Abc03sc00i00')
2012-04-29 04:56:41,890 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-29 04:56:41,951 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:41,952 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:41,891 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 04:56:41,979 DEBUG: fglrx.available: falling back to default
2012-04-29 04:56:42,116 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:42,117 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:42,041 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 04:56:42,118 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-29 04:56:42,195 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:42,196 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:56:42,119 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-29 04:56:42,205 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-29 04:56:42,228 DEBUG: fglrx.available: falling back to default
2012-04-29 04:56:42,380 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:42,381 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:56:42,305 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-29 04:56:42,382 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-29 04:56:42,383 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,383 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-04-29 04:56:42,452 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:42,453 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:42,384 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 04:56:42,480 DEBUG: fglrx.available: falling back to default
2012-04-29 04:56:42,629 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:42,630 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:42,555 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 04:56:42,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-04-29 04:56:42,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 04:56:42,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-29 04:56:42,661 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:56:42,661 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,661 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:56:42,661 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc02ip00')
2012-04-29 04:56:42,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-29 04:56:42,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'platform:regulatory')
2012-04-29 04:56:42,669 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-29 04:56:42,670 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001022d00009600sv00001179sd0000FF6Abc06sc00i00')
2012-04-29 04:56:42,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2012-04-29 04:56:42,710 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek'}
2012-04-29 04:56:42,710 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,710 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-29 04:56:42,710 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-29 04:56:42,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-29 04:56:42,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-04-29 04:56:42,711 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-04-29 04:56:42,711 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001179sd0000FF6Abc01sc01i8a')
2012-04-29 04:56:42,718 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-04-29 04:56:42,718 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,718 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-29 04:56:42,718 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2012-04-29 04:56:42,719 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-04-29 04:56:42,719 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,719 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2012-04-29 04:56:42,719 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00ic08isc06ip50')
2012-04-29 04:56:42,877 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-29 04:56:42,877 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,877 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc01ip00')
2012-04-29 04:56:42,878 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-29 04:56:42,878 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-29 04:56:42,878 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:56:42,878 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-29 04:56:42,878 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:56:42,879 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-29 04:56:42,879 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:56:42,879 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-29 04:56:42,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i00')
2012-04-29 04:56:42,885 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-04-29 04:56:42,886 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,886 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k100,101,102,103,110,111,145,14A,ra0,1,18,1C,mlsfw')
2012-04-29 04:56:42,886 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:56:42,886 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,886 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-29 04:56:42,886 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,887 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-29 04:56:42,887 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,887 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:56:42,887 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,887 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-29 04:56:42,887 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvr1.80:bd09/01/2009:svnTOSHIBA:pnSatelliteL300D:pvrPSLC8A-02200Y:rvnTOSHIBA:rnPortablePC:rvrBaseBoardVersion:cvnAMD:ct10:cvrNone:')
2012-04-29 04:56:42,910 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2012-04-29 04:56:42,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-29 04:56:42,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2012-04-29 04:56:42,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,80,8E,95,96,98,9B,A3,A4,A5,CD,E0,E1,E2,E3,E4,EC,EE,F0,1A2,1A3,1A4,1D0,212,ram4,lsfw')
2012-04-29 04:56:42,911 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:56:42,911 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:56:42,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'usb:v1058p1100d0175dc00dsc00dp00ic08isc06ip50')
2012-04-29 04:56:42,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-29 04:56:42,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'usb:v1C4Fp0003d0110dc00dsc00dp00ic03isc01ip02')
2012-04-29 04:56:42,914 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-29 04:56:42,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,914 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-04-29 04:56:42,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 04:56:42,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001002d00004396sv00001179sd0000FF6Abc0Csc03i20')
2012-04-29 04:56:42,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'input:b0003v04F2pB070e0834-e0,1,kD4,ramlsfw')
2012-04-29 04:56:42,921 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:56:42,921 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,921 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:56:42,922 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:SYN1913:SYN0700:SYN0002:PNP0F13:')
2012-04-29 04:56:42,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001002d00004390sv00001179sd0000FF6Abc01sc06i01')
2012-04-29 04:56:42,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-29 04:56:42,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'usb:v0BDAp8198d0200dc00dsc00dp00icFFiscFFipFF')
2012-04-29 04:56:42,929 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rtl8187'}
2012-04-29 04:56:42,929 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rtl8187', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-29 04:56:42,929 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:56:42,930 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,930 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:56:42,930 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,930 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-29 04:56:42,930 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00icFFiscFFipFF')
2012-04-29 04:56:42,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'option'}
2012-04-29 04:56:42,933 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'platform:pcspkr')
2012-04-29 04:56:42,933 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-29 04:56:42,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,934 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-29 04:56:42,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2012-04-29 04:56:42,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001002d00004385sv00001179sd0000FF6Abc0Csc05i00')
2012-04-29 04:56:42,941 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-04-29 04:56:42,941 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,941 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-04-29 04:56:42,941 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,941 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001179sd0000FF6Abc06sc01i00')
2012-04-29 04:56:42,948 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-29 04:56:42,960 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-29 04:56:42,960 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,960 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-29 04:56:42,960 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-29 04:56:42,960 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 04:56:42,961 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,961 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 04:56:42,961 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'pci:v00001002d00004383sv00001179sd0000FF6Abc04sc03i00')
2012-04-29 04:56:42,967 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-29 04:56:42,967 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,968 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-29 04:56:42,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 04:56:42,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c7ef0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-29 04:56:42,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:TOS1900:')
2012-04-29 04:56:42,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'input:b0003v1C4Fp0003e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-04-29 04:56:42,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-29 04:56:42,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:TOS1901:')
2012-04-29 04:56:42,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001002d00009613sv00001179sd0000FF6Abc03sc00i00')
2012-04-29 04:56:42,968 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-04-29 04:56:42,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 04:56:42,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-29 04:56:42,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc02ip00')
2012-04-29 04:56:42,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-29 04:56:42,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'platform:regulatory')
2012-04-29 04:56:42,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-29 04:56:42,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001022d00009600sv00001179sd0000FF6Abc06sc00i00')
2012-04-29 04:56:42,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2012-04-29 04:56:42,969 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-29 04:56:42,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-29 04:56:42,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-04-29 04:56:42,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001179sd0000FF6Abc01sc01i8a')
2012-04-29 04:56:42,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-29 04:56:42,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2012-04-29 04:56:42,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2012-04-29 04:56:42,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00ic08isc06ip50')
2012-04-29 04:56:42,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc01ip00')
2012-04-29 04:56:42,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-29 04:56:42,970 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-29 04:56:42,971 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-29 04:56:42,971 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-29 04:56:42,971 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i00')
2012-04-29 04:56:42,971 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k100,101,102,103,110,111,145,14A,ra0,1,18,1C,mlsfw')
2012-04-29 04:56:42,971 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-29 04:56:42,971 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvr1.80:bd09/01/2009:svnTOSHIBA:pnSatelliteL300D:pvrPSLC8A-02200Y:rvnTOSHIBA:rnPortablePC:rvrBaseBoardVersion:cvnAMD:ct10:cvrNone:')
2012-04-29 04:56:42,971 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2012-04-29 04:56:42,971 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-29 04:56:42,971 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2012-04-29 04:56:42,971 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,80,8E,95,96,98,9B,A3,A4,A5,CD,E0,E1,E2,E3,E4,EC,EE,F0,1A2,1A3,1A4,1D0,212,ram4,lsfw')
2012-04-29 04:56:42,972 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'usb:v1058p1100d0175dc00dsc00dp00ic08isc06ip50')
2012-04-29 04:56:42,972 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'usb:v1C4Fp0003d0110dc00dsc00dp00ic03isc01ip02')
2012-04-29 04:56:42,972 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 04:56:42,972 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001002d00004396sv00001179sd0000FF6Abc0Csc03i20')
2012-04-29 04:56:42,972 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'input:b0003v04F2pB070e0834-e0,1,kD4,ramlsfw')
2012-04-29 04:56:42,972 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:SYN1913:SYN0700:SYN0002:PNP0F13:')
2012-04-29 04:56:42,972 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001002d00004390sv00001179sd0000FF6Abc01sc06i01')
2012-04-29 04:56:42,972 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-29 04:56:42,972 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'usb:v0BDAp8198d0200dc00dsc00dp00icFFiscFFipFF')
2012-04-29 04:56:42,972 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-29 04:56:42,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-29 04:56:42,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00icFFiscFFipFF')
2012-04-29 04:56:42,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'platform:pcspkr')
2012-04-29 04:56:42,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2012-04-29 04:56:42,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001002d00004385sv00001179sd0000FF6Abc0Csc05i00')
2012-04-29 04:56:42,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001179sd0000FF6Abc06sc01i00')
2012-04-29 04:56:42,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-29 04:56:42,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-29 04:56:42,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'pci:v00001002d00004383sv00001179sd0000FF6Abc04sc03i00')
2012-04-29 04:56:42,973 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d3df38> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-29 04:56:43,047 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:43,047 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:43,131 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:43,131 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:56:43,331 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:43,331 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:43,409 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:43,410 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:43,449 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:43,450 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:56:45,754 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:56:45,755 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:56:50,527 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-04-29 04:57:31,826 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:57:31,827 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:57:31,902 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:57:31,903 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:57:33,692 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:57:33,693 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:57:33,721 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:57:33,721 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:57:33,768 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:57:33,768 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:57:33,974 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:57:33,975 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:57:34,010 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:57:34,010 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:57:34,088 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:57:34,088 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:57:34,128 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:57:34,128 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 04:57:34,183 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 04:57:34,184 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 04:57:35,495 DEBUG: Shutting down
2012-04-29 13:56:28,410 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8>
2012-04-29 13:56:32,516 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-04-29 13:56:32,734 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-29 13:56:32,742 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-29 13:56:32,841 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-29 13:56:32,995 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-29 13:56:32,996 DEBUG: fglrx.available: falling back to default
2012-04-29 13:56:33,256 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-29 13:56:33,263 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-29 13:56:33,271 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-29 13:56:33,271 DEBUG: fglrx.available: falling back to default
2012-04-29 13:56:33,333 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-29 13:56:33,333 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-29 13:56:33,363 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-29 13:56:33,364 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-29 13:56:33,432 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-29 13:56:33,433 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-29 13:56:33,458 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-29 13:56:33,475 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-29 13:56:33,482 DEBUG: nvidia.available: falling back to default
2012-04-29 13:56:33,543 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 13:56:33,544 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-29 13:56:33,550 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-29 13:56:33,558 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-29 13:56:33,559 DEBUG: nvidia.available: falling back to default
2012-04-29 13:56:33,639 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-29 13:56:33,646 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-29 13:56:33,658 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-29 13:56:33,660 DEBUG: nvidia.available: falling back to default
2012-04-29 13:56:33,799 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-29 13:56:33,817 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-29 13:56:33,830 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-29 13:56:33,831 DEBUG: nvidia.available: falling back to default
2012-04-29 13:56:33,856 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 13:56:33,856 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-29 13:56:33,862 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-29 13:56:33,875 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-29 13:56:33,877 DEBUG: nvidia.available: falling back to default
2012-04-29 13:56:33,915 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 13:56:33,917 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-29 13:56:33,928 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-29 13:56:33,959 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-29 13:56:33,960 DEBUG: nvidia.available: falling back to default
2012-04-29 13:56:33,990 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 13:56:33,990 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-29 13:56:33,991 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-29 13:56:34,003 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-29 13:56:34,031 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-29 13:56:34,032 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-29 13:56:34,032 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-29 13:56:34,043 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-29 13:56:34,044 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-29 13:56:34,044 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-29 13:56:34,045 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-29 13:56:34,140 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-29 13:56:34,141 DEBUG: Firmware for DVB cards not available
2012-04-29 13:56:34,142 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-29 13:56:34,159 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-29 13:56:34,177 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-29 13:56:34,226 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-29 13:56:34,227 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-29 13:56:34,268 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-29 13:56:34,295 DEBUG: Software modem not available
2012-04-29 13:56:34,295 DEBUG: all custom handlers loaded
2012-04-29 13:56:34,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:TOS1900:')
2012-04-29 13:56:34,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'input:b0003v1C4Fp0003e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-04-29 13:56:34,303 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 13:56:34,580 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:34,580 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 13:56:34,580 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:34,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-29 13:56:34,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:TOS1901:')
2012-04-29 13:56:34,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001002d00009613sv00001179sd0000FF6Abc03sc00i00')
2012-04-29 13:56:35,190 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-29 13:56:35,301 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:56:35,302 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:56:35,191 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 13:56:35,310 DEBUG: fglrx.available: falling back to default
2012-04-29 13:56:35,365 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:56:35,366 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:56:35,336 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 13:56:35,366 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-29 13:56:35,391 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:56:35,391 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 13:56:35,366 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-29 13:56:35,398 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-29 13:56:35,407 DEBUG: fglrx.available: falling back to default
2012-04-29 13:56:35,497 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:56:35,498 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 13:56:35,463 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-29 13:56:35,498 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-29 13:56:35,498 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,498 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-04-29 13:56:35,522 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:56:35,522 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:56:35,498 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 13:56:35,530 DEBUG: fglrx.available: falling back to default
2012-04-29 13:56:35,590 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:56:35,590 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:56:35,567 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 13:56:35,591 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-04-29 13:56:35,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 13:56:35,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-29 13:56:35,613 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 13:56:35,613 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,614 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 13:56:35,614 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,614 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2012-04-29 13:56:35,634 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek'}
2012-04-29 13:56:35,635 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,635 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-29 13:56:35,635 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-29 13:56:35,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'platform:regulatory')
2012-04-29 13:56:35,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-29 13:56:35,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001022d00009600sv00001179sd0000FF6Abc06sc00i00')
2012-04-29 13:56:35,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001179sd0000FF6Abc04sc03i00')
2012-04-29 13:56:35,663 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-29 13:56:35,663 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,663 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-29 13:56:35,663 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-29 13:56:35,664 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-29 13:56:35,664 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-04-29 13:56:35,664 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-04-29 13:56:35,664 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,664 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001179sd0000FF6Abc01sc01i8a')
2012-04-29 13:56:35,670 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-04-29 13:56:35,671 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,671 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-29 13:56:35,671 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2012-04-29 13:56:35,671 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2012-04-29 13:56:35,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00ic08isc06ip50')
2012-04-29 13:56:35,834 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-29 13:56:35,834 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc02ip00')
2012-04-29 13:56:35,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-29 13:56:35,841 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 13:56:35,841 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-29 13:56:35,842 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 13:56:35,842 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-29 13:56:35,842 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 13:56:35,842 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-29 13:56:35,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2012-04-29 13:56:35,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k100,101,102,103,110,111,145,14A,ra0,1,18,1C,mlsfw')
2012-04-29 13:56:35,843 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 13:56:35,843 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,844 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-29 13:56:35,845 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,845 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-29 13:56:35,845 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,845 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 13:56:35,845 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-29 13:56:35,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvr1.80:bd09/01/2009:svnTOSHIBA:pnSatelliteL300D:pvrPSLC8A-02200Y:rvnTOSHIBA:rnPortablePC:rvrBaseBoardVersion:cvnAMD:ct10:cvrNone:')
2012-04-29 13:56:35,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-29 13:56:35,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2012-04-29 13:56:35,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,80,8E,95,96,98,9B,A3,A4,A5,CD,E0,E1,E2,E3,E4,EC,EE,F0,1A2,1A3,1A4,1D0,212,ram4,lsfw')
2012-04-29 13:56:35,879 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 13:56:35,879 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,879 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 13:56:35,880 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc01ip00')
2012-04-29 13:56:35,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-29 13:56:35,880 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'usb:v1C4Fp0003d0110dc00dsc00dp00ic03isc01ip02')
2012-04-29 13:56:35,882 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-29 13:56:35,882 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,882 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-04-29 13:56:35,882 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 13:56:35,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001179sd0000FF6Abc0Csc03i20')
2012-04-29 13:56:35,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'input:b0003v04F2pB070e0834-e0,1,kD4,ramlsfw')
2012-04-29 13:56:35,889 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 13:56:35,890 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,890 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 13:56:35,890 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:SYN1913:SYN0700:SYN0002:PNP0F13:')
2012-04-29 13:56:35,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001002d00004390sv00001179sd0000FF6Abc01sc06i01')
2012-04-29 13:56:35,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-29 13:56:35,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'usb:v0BDAp8198d0200dc00dsc00dp00icFFiscFFipFF')
2012-04-29 13:56:35,897 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rtl8187'}
2012-04-29 13:56:35,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rtl8187', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-29 13:56:35,898 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 13:56:35,898 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,898 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 13:56:35,898 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,898 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-29 13:56:35,898 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00icFFiscFFipFF')
2012-04-29 13:56:35,901 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'option'}
2012-04-29 13:56:35,901 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,901 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'platform:pcspkr')
2012-04-29 13:56:35,902 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-29 13:56:35,902 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,902 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-29 13:56:35,902 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2012-04-29 13:56:35,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-04-29 13:56:35,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001002d00004385sv00001179sd0000FF6Abc0Csc05i00')
2012-04-29 13:56:35,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-04-29 13:56:35,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-04-29 13:56:35,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i00')
2012-04-29 13:56:35,919 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-04-29 13:56:35,919 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-29 13:56:35,931 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-29 13:56:35,931 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,931 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-29 13:56:35,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-29 13:56:35,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 13:56:35,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 13:56:35,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 13:56:35,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001179sd0000FF6Abc06sc01i00')
2012-04-29 13:56:35,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2487ea8> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-29 13:56:35,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:TOS1900:')
2012-04-29 13:56:35,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'input:b0003v1C4Fp0003e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-04-29 13:56:35,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-29 13:56:35,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:TOS1901:')
2012-04-29 13:56:35,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001002d00009613sv00001179sd0000FF6Abc03sc00i00')
2012-04-29 13:56:35,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-04-29 13:56:35,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 13:56:35,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-29 13:56:35,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2012-04-29 13:56:35,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-29 13:56:35,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'platform:regulatory')
2012-04-29 13:56:35,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-29 13:56:35,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001022d00009600sv00001179sd0000FF6Abc06sc00i00')
2012-04-29 13:56:35,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001179sd0000FF6Abc04sc03i00')
2012-04-29 13:56:35,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-29 13:56:35,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-29 13:56:35,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-04-29 13:56:35,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001179sd0000FF6Abc01sc01i8a')
2012-04-29 13:56:35,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-29 13:56:35,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2012-04-29 13:56:35,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2012-04-29 13:56:35,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00ic08isc06ip50')
2012-04-29 13:56:35,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc02ip00')
2012-04-29 13:56:35,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-29 13:56:35,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-29 13:56:35,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-29 13:56:35,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-29 13:56:35,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2012-04-29 13:56:35,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k100,101,102,103,110,111,145,14A,ra0,1,18,1C,mlsfw')
2012-04-29 13:56:35,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-29 13:56:35,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvr1.80:bd09/01/2009:svnTOSHIBA:pnSatelliteL300D:pvrPSLC8A-02200Y:rvnTOSHIBA:rnPortablePC:rvrBaseBoardVersion:cvnAMD:ct10:cvrNone:')
2012-04-29 13:56:35,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-29 13:56:35,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2012-04-29 13:56:35,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,80,8E,95,96,98,9B,A3,A4,A5,CD,E0,E1,E2,E3,E4,EC,EE,F0,1A2,1A3,1A4,1D0,212,ram4,lsfw')
2012-04-29 13:56:35,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc01ip00')
2012-04-29 13:56:35,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'usb:v1C4Fp0003d0110dc00dsc00dp00ic03isc01ip02')
2012-04-29 13:56:35,943 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 13:56:35,943 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001179sd0000FF6Abc0Csc03i20')
2012-04-29 13:56:35,943 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'input:b0003v04F2pB070e0834-e0,1,kD4,ramlsfw')
2012-04-29 13:56:35,943 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:SYN1913:SYN0700:SYN0002:PNP0F13:')
2012-04-29 13:56:35,943 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001002d00004390sv00001179sd0000FF6Abc01sc06i01')
2012-04-29 13:56:35,943 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-29 13:56:35,943 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'usb:v0BDAp8198d0200dc00dsc00dp00icFFiscFFipFF')
2012-04-29 13:56:35,943 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-29 13:56:35,943 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-29 13:56:35,943 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00icFFiscFFipFF')
2012-04-29 13:56:35,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'platform:pcspkr')
2012-04-29 13:56:35,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2012-04-29 13:56:35,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001002d00004385sv00001179sd0000FF6Abc0Csc05i00')
2012-04-29 13:56:35,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i00')
2012-04-29 13:56:35,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-29 13:56:35,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-29 13:56:35,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001179sd0000FF6Abc06sc01i00')
2012-04-29 13:56:35,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27fcfc8> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-29 13:56:36,073 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:56:36,073 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:56:36,196 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:56:36,197 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 13:56:36,500 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:56:36,500 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:56:36,550 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:56:36,550 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:56:36,603 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:56:36,603 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 13:56:40,834 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:56:40,834 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:56:46,528 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-04-29 13:57:42,833 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:57:42,833 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:57:42,863 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:57:42,864 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:57:45,917 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:57:45,918 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:57:45,987 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:57:45,988 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:57:46,095 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:57:46,096 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 13:57:46,365 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:57:46,366 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:57:46,434 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:57:46,435 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:57:46,565 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:57:46,566 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:57:46,634 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:57:46,635 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 13:57:46,743 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 13:57:46,744 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 13:57:49,084 DEBUG: Shutting down
2012-04-29 15:09:03,683 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0>
2012-04-29 15:09:07,129 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-04-29 15:09:07,415 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-29 15:09:07,423 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-29 15:09:07,563 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-29 15:09:07,702 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-29 15:09:07,702 DEBUG: fglrx.available: falling back to default
2012-04-29 15:09:07,902 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-29 15:09:07,909 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-29 15:09:07,918 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-29 15:09:07,918 DEBUG: fglrx.available: falling back to default
2012-04-29 15:09:08,007 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-29 15:09:08,008 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-29 15:09:08,044 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-29 15:09:08,045 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-29 15:09:08,090 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-29 15:09:08,090 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-29 15:09:08,103 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-29 15:09:08,112 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-29 15:09:08,114 DEBUG: nvidia.available: falling back to default
2012-04-29 15:09:08,147 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 15:09:08,147 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-29 15:09:08,158 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-29 15:09:08,172 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-29 15:09:08,174 DEBUG: nvidia.available: falling back to default
2012-04-29 15:09:08,264 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-29 15:09:08,272 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-29 15:09:08,284 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-29 15:09:08,285 DEBUG: nvidia.available: falling back to default
2012-04-29 15:09:08,338 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-29 15:09:08,345 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-29 15:09:08,354 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-29 15:09:08,355 DEBUG: nvidia.available: falling back to default
2012-04-29 15:09:08,388 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 15:09:08,388 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-29 15:09:08,398 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-29 15:09:08,412 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-29 15:09:08,414 DEBUG: nvidia.available: falling back to default
2012-04-29 15:09:08,476 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 15:09:08,479 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-29 15:09:08,492 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-29 15:09:08,501 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-29 15:09:08,502 DEBUG: nvidia.available: falling back to default
2012-04-29 15:09:08,530 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 15:09:08,531 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-29 15:09:08,531 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-29 15:09:08,547 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-29 15:09:08,622 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-29 15:09:08,623 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-29 15:09:08,624 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-29 15:09:08,635 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-29 15:09:08,638 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-29 15:09:08,638 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-29 15:09:08,639 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-29 15:09:08,725 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-29 15:09:08,726 DEBUG: Firmware for DVB cards not available
2012-04-29 15:09:08,726 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-29 15:09:08,736 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-29 15:09:08,748 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-29 15:09:08,834 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-29 15:09:08,835 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-29 15:09:08,899 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-29 15:09:08,922 DEBUG: Software modem not available
2012-04-29 15:09:08,922 DEBUG: all custom handlers loaded
2012-04-29 15:09:08,923 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:TOS1900:')
2012-04-29 15:09:08,923 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'input:b0003v1C4Fp0003e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-04-29 15:09:08,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:09:09,061 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:09,061 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:09:09,061 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:09,061 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-29 15:09:09,061 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:TOS1901:')
2012-04-29 15:09:09,061 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001002d00009613sv00001179sd0000FF6Abc03sc00i00')
2012-04-29 15:09:09,552 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-29 15:09:09,684 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:09:09,685 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:09:09,553 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 15:09:09,712 DEBUG: fglrx.available: falling back to default
2012-04-29 15:09:09,764 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:09:09,764 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:09:09,739 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 15:09:09,765 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-29 15:09:09,790 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:09:09,790 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 15:09:09,765 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-29 15:09:09,797 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-29 15:09:09,805 DEBUG: fglrx.available: falling back to default
2012-04-29 15:09:09,926 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:09:09,926 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 15:09:09,867 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-29 15:09:09,927 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-29 15:09:09,927 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:09,927 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-04-29 15:09:09,956 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:09:09,957 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:09:09,927 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 15:09:09,966 DEBUG: fglrx.available: falling back to default
2012-04-29 15:09:10,043 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:09:10,043 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:09:10,017 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 15:09:10,043 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-04-29 15:09:10,044 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 15:09:10,065 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-29 15:09:10,066 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:09:10,066 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,066 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:09:10,066 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,066 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc02ip00')
2012-04-29 15:09:10,073 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-29 15:09:10,073 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'platform:regulatory')
2012-04-29 15:09:10,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-29 15:09:10,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001022d00009600sv00001179sd0000FF6Abc06sc00i00')
2012-04-29 15:09:10,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2012-04-29 15:09:10,115 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek'}
2012-04-29 15:09:10,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,115 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-29 15:09:10,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-29 15:09:10,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-29 15:09:10,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-04-29 15:09:10,116 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-04-29 15:09:10,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001179sd0000FF6Abc01sc01i8a')
2012-04-29 15:09:10,123 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-04-29 15:09:10,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-29 15:09:10,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2012-04-29 15:09:10,124 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-04-29 15:09:10,124 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2012-04-29 15:09:10,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00ic08isc06ip50')
2012-04-29 15:09:10,279 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-29 15:09:10,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc01ip00')
2012-04-29 15:09:10,280 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-29 15:09:10,280 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-29 15:09:10,281 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:09:10,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-29 15:09:10,281 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:09:10,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-29 15:09:10,282 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:09:10,282 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-29 15:09:10,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i00')
2012-04-29 15:09:10,288 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-04-29 15:09:10,289 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,289 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k100,101,102,103,110,111,145,14A,ra0,1,18,1C,mlsfw')
2012-04-29 15:09:10,289 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:09:10,289 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,289 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-29 15:09:10,290 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,290 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-29 15:09:10,290 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,290 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:09:10,290 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,290 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-29 15:09:10,290 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvr1.80:bd09/01/2009:svnTOSHIBA:pnSatelliteL300D:pvrPSLC8A-02200Y:rvnTOSHIBA:rnPortablePC:rvrBaseBoardVersion:cvnAMD:ct10:cvrNone:')
2012-04-29 15:09:10,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2012-04-29 15:09:10,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-29 15:09:10,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2012-04-29 15:09:10,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,80,8E,95,96,98,9B,A3,A4,A5,CD,E0,E1,E2,E3,E4,EC,EE,F0,1A2,1A3,1A4,1D0,212,ram4,lsfw')
2012-04-29 15:09:10,314 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:09:10,314 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,314 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:09:10,315 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,315 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'usb:v1058p1100d0175dc00dsc00dp00ic08isc06ip50')
2012-04-29 15:09:10,315 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-29 15:09:10,315 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,315 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'usb:v1C4Fp0003d0110dc00dsc00dp00ic03isc01ip02')
2012-04-29 15:09:10,317 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-29 15:09:10,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,317 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-04-29 15:09:10,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,317 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 15:09:10,318 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001002d00004396sv00001179sd0000FF6Abc0Csc03i20')
2012-04-29 15:09:10,324 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'input:b0003v04F2pB070e0834-e0,1,kD4,ramlsfw')
2012-04-29 15:09:10,324 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:09:10,324 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,324 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:09:10,325 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:SYN1913:SYN0700:SYN0002:PNP0F13:')
2012-04-29 15:09:10,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001002d00004390sv00001179sd0000FF6Abc01sc06i01')
2012-04-29 15:09:10,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-29 15:09:10,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'usb:v0BDAp8198d0200dc00dsc00dp00icFFiscFFipFF')
2012-04-29 15:09:10,332 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rtl8187'}
2012-04-29 15:09:10,332 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rtl8187', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-29 15:09:10,332 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:09:10,332 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,333 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:09:10,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-29 15:09:10,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00icFFiscFFipFF')
2012-04-29 15:09:10,335 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'option'}
2012-04-29 15:09:10,335 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'platform:pcspkr')
2012-04-29 15:09:10,336 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-29 15:09:10,336 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,337 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-29 15:09:10,337 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2012-04-29 15:09:10,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001002d00004385sv00001179sd0000FF6Abc0Csc05i00')
2012-04-29 15:09:10,343 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-04-29 15:09:10,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,344 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-04-29 15:09:10,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001179sd0000FF6Abc06sc01i00')
2012-04-29 15:09:10,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-29 15:09:10,362 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-29 15:09:10,362 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,362 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-29 15:09:10,363 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,363 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-29 15:09:10,363 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:09:10,363 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,363 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:09:10,363 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,363 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'pci:v00001002d00004383sv00001179sd0000FF6Abc04sc03i00')
2012-04-29 15:09:10,370 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-29 15:09:10,370 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,370 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-29 15:09:10,370 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:09:10,370 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x204def0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-29 15:09:10,371 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:TOS1900:')
2012-04-29 15:09:10,371 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'input:b0003v1C4Fp0003e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-04-29 15:09:10,371 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-29 15:09:10,371 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:TOS1901:')
2012-04-29 15:09:10,371 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001002d00009613sv00001179sd0000FF6Abc03sc00i00')
2012-04-29 15:09:10,371 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-04-29 15:09:10,371 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 15:09:10,371 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-29 15:09:10,371 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc02ip00')
2012-04-29 15:09:10,372 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-29 15:09:10,372 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'platform:regulatory')
2012-04-29 15:09:10,372 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-29 15:09:10,372 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001022d00009600sv00001179sd0000FF6Abc06sc00i00')
2012-04-29 15:09:10,372 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2012-04-29 15:09:10,372 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-29 15:09:10,372 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-29 15:09:10,372 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-04-29 15:09:10,372 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001179sd0000FF6Abc01sc01i8a')
2012-04-29 15:09:10,373 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-29 15:09:10,373 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2012-04-29 15:09:10,373 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2012-04-29 15:09:10,373 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00ic08isc06ip50')
2012-04-29 15:09:10,373 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc01ip00')
2012-04-29 15:09:10,373 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-29 15:09:10,373 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-29 15:09:10,373 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-29 15:09:10,373 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-29 15:09:10,373 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i00')
2012-04-29 15:09:10,374 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k100,101,102,103,110,111,145,14A,ra0,1,18,1C,mlsfw')
2012-04-29 15:09:10,374 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-29 15:09:10,374 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvr1.80:bd09/01/2009:svnTOSHIBA:pnSatelliteL300D:pvrPSLC8A-02200Y:rvnTOSHIBA:rnPortablePC:rvrBaseBoardVersion:cvnAMD:ct10:cvrNone:')
2012-04-29 15:09:10,374 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2012-04-29 15:09:10,374 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-29 15:09:10,374 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2012-04-29 15:09:10,374 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,80,8E,95,96,98,9B,A3,A4,A5,CD,E0,E1,E2,E3,E4,EC,EE,F0,1A2,1A3,1A4,1D0,212,ram4,lsfw')
2012-04-29 15:09:10,374 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'usb:v1058p1100d0175dc00dsc00dp00ic08isc06ip50')
2012-04-29 15:09:10,374 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'usb:v1C4Fp0003d0110dc00dsc00dp00ic03isc01ip02')
2012-04-29 15:09:10,374 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 15:09:10,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001002d00004396sv00001179sd0000FF6Abc0Csc03i20')
2012-04-29 15:09:10,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'input:b0003v04F2pB070e0834-e0,1,kD4,ramlsfw')
2012-04-29 15:09:10,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:SYN1913:SYN0700:SYN0002:PNP0F13:')
2012-04-29 15:09:10,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001002d00004390sv00001179sd0000FF6Abc01sc06i01')
2012-04-29 15:09:10,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-29 15:09:10,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'usb:v0BDAp8198d0200dc00dsc00dp00icFFiscFFipFF')
2012-04-29 15:09:10,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-29 15:09:10,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-29 15:09:10,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00icFFiscFFipFF')
2012-04-29 15:09:10,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'platform:pcspkr')
2012-04-29 15:09:10,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2012-04-29 15:09:10,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001002d00004385sv00001179sd0000FF6Abc0Csc05i00')
2012-04-29 15:09:10,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001179sd0000FF6Abc06sc01i00')
2012-04-29 15:09:10,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-29 15:09:10,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-29 15:09:10,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'pci:v00001002d00004383sv00001179sd0000FF6Abc04sc03i00')
2012-04-29 15:09:10,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23c3f38> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-29 15:09:10,444 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:09:10,444 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:09:10,545 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:09:10,545 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 15:09:10,761 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:09:10,761 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:09:10,813 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:09:10,813 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:09:10,861 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:09:10,861 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 15:09:38,350 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:09:38,350 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:09:43,596 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-04-29 15:10:35,490 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:10:35,491 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:10:35,560 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:10:35,561 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:10:41,180 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:10:41,181 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:10:41,210 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:10:41,210 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:10:41,260 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:10:41,261 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 15:10:41,483 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:10:41,484 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:10:41,520 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:10:41,520 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:10:41,585 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:10:41,586 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:10:41,616 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:10:41,616 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:10:41,659 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:10:41,660 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 15:10:43,428 DEBUG: Shutting down
2012-04-29 15:46:36,360 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0>
2012-04-29 15:46:39,868 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-04-29 15:46:40,026 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-29 15:46:40,027 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-29 15:46:40,119 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-29 15:46:40,139 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-29 15:46:40,139 DEBUG: fglrx.available: falling back to default
2012-04-29 15:46:40,266 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-29 15:46:40,273 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-29 15:46:40,282 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-29 15:46:40,283 DEBUG: fglrx.available: falling back to default
2012-04-29 15:46:40,357 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-29 15:46:40,358 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-29 15:46:40,365 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-29 15:46:40,365 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-29 15:46:40,391 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-29 15:46:40,392 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-29 15:46:40,403 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-29 15:46:40,418 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-29 15:46:40,420 DEBUG: nvidia.available: falling back to default
2012-04-29 15:46:40,453 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 15:46:40,453 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-29 15:46:40,460 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-29 15:46:40,469 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-29 15:46:40,470 DEBUG: nvidia.available: falling back to default
2012-04-29 15:46:40,522 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-29 15:46:40,529 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-29 15:46:40,538 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-29 15:46:40,539 DEBUG: nvidia.available: falling back to default
2012-04-29 15:46:40,594 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-29 15:46:40,602 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-29 15:46:40,617 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-29 15:46:40,618 DEBUG: nvidia.available: falling back to default
2012-04-29 15:46:40,650 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 15:46:40,651 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-29 15:46:40,658 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-29 15:46:40,667 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-29 15:46:40,668 DEBUG: nvidia.available: falling back to default
2012-04-29 15:46:40,695 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 15:46:40,696 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-29 15:46:40,703 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-29 15:46:40,712 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-29 15:46:40,713 DEBUG: nvidia.available: falling back to default
2012-04-29 15:46:40,739 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-29 15:46:40,739 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-29 15:46:40,739 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-29 15:46:40,747 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-29 15:46:40,775 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-29 15:46:40,776 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-29 15:46:40,776 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-29 15:46:40,783 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-29 15:46:40,784 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-29 15:46:40,785 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-29 15:46:40,785 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-29 15:46:40,826 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-29 15:46:40,827 DEBUG: Firmware for DVB cards not available
2012-04-29 15:46:40,827 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-29 15:46:40,837 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-29 15:46:40,846 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-29 15:46:40,891 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-29 15:46:40,891 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-29 15:46:40,919 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-29 15:46:40,932 DEBUG: Software modem not available
2012-04-29 15:46:40,933 DEBUG: all custom handlers loaded
2012-04-29 15:46:40,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:TOS1900:')
2012-04-29 15:46:40,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'input:b0003v1C4Fp0003e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-04-29 15:46:40,941 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:46:41,050 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:41,050 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:46:41,050 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:41,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-29 15:46:41,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:TOS1901:')
2012-04-29 15:46:41,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001002d00009613sv00001179sd0000FF6Abc03sc00i00')
2012-04-29 15:46:41,545 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-29 15:46:41,573 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:46:41,573 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:46:41,545 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 15:46:41,581 DEBUG: fglrx.available: falling back to default
2012-04-29 15:46:41,635 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:46:41,636 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:46:41,608 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 15:46:41,636 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-29 15:46:41,665 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:46:41,665 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 15:46:41,636 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-29 15:46:41,672 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-29 15:46:41,681 DEBUG: fglrx.available: falling back to default
2012-04-29 15:46:41,735 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:46:41,735 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 15:46:41,707 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-29 15:46:41,735 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-29 15:46:41,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:41,736 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-04-29 15:46:41,763 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:46:41,764 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:46:41,736 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 15:46:41,773 DEBUG: fglrx.available: falling back to default
2012-04-29 15:46:41,832 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:46:41,832 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:46:41,804 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-29 15:46:41,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-04-29 15:46:41,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 15:46:41,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-29 15:46:41,855 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:46:41,855 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:41,855 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:46:41,855 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:41,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc02ip00')
2012-04-29 15:46:41,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-29 15:46:41,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'platform:regulatory')
2012-04-29 15:46:41,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-29 15:46:41,864 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001022d00009600sv00001179sd0000FF6Abc06sc00i00')
2012-04-29 15:46:41,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2012-04-29 15:46:41,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek'}
2012-04-29 15:46:41,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:41,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-29 15:46:41,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:41,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-29 15:46:41,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-29 15:46:41,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-04-29 15:46:41,905 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-04-29 15:46:41,905 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:41,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001179sd0000FF6Abc01sc01i8a')
2012-04-29 15:46:41,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-04-29 15:46:41,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:41,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-29 15:46:41,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2012-04-29 15:46:41,913 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-04-29 15:46:41,913 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:41,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2012-04-29 15:46:41,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00ic08isc06ip50')
2012-04-29 15:46:42,078 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-29 15:46:42,079 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc01ip00')
2012-04-29 15:46:42,079 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-29 15:46:42,079 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-29 15:46:42,080 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:46:42,080 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-29 15:46:42,080 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:46:42,080 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-29 15:46:42,080 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:46:42,081 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-29 15:46:42,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i00')
2012-04-29 15:46:42,087 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-04-29 15:46:42,088 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k100,101,102,103,110,111,145,14A,ra0,1,18,1C,mlsfw')
2012-04-29 15:46:42,088 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:46:42,088 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,088 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-29 15:46:42,088 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,088 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-29 15:46:42,089 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,089 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:46:42,089 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-29 15:46:42,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvr1.80:bd09/01/2009:svnTOSHIBA:pnSatelliteL300D:pvrPSLC8A-02200Y:rvnTOSHIBA:rnPortablePC:rvrBaseBoardVersion:cvnAMD:ct10:cvrNone:')
2012-04-29 15:46:42,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2012-04-29 15:46:42,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-29 15:46:42,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2012-04-29 15:46:42,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,80,8E,95,96,98,9B,A3,A4,A5,CD,E0,E1,E2,E3,E4,EC,EE,F0,1A2,1A3,1A4,1D0,212,ram4,lsfw')
2012-04-29 15:46:42,113 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:46:42,113 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,113 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:46:42,113 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'usb:v1058p1100d0175dc00dsc00dp00ic08isc06ip50')
2012-04-29 15:46:42,114 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-29 15:46:42,114 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'usb:v1C4Fp0003d0110dc00dsc00dp00ic03isc01ip02')
2012-04-29 15:46:42,115 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-29 15:46:42,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,116 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-04-29 15:46:42,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 15:46:42,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001002d00004396sv00001179sd0000FF6Abc0Csc03i20')
2012-04-29 15:46:42,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'input:b0003v04F2pB070e0834-e0,1,kD4,ramlsfw')
2012-04-29 15:46:42,123 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:46:42,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,123 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:46:42,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:SYN1913:SYN0700:SYN0002:PNP0F13:')
2012-04-29 15:46:42,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001002d00004390sv00001179sd0000FF6Abc01sc06i01')
2012-04-29 15:46:42,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-29 15:46:42,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'usb:v0BDAp8198d0200dc00dsc00dp00icFFiscFFipFF')
2012-04-29 15:46:42,131 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rtl8187'}
2012-04-29 15:46:42,131 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rtl8187', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-29 15:46:42,131 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:46:42,131 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,131 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:46:42,131 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-29 15:46:42,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00icFFiscFFipFF')
2012-04-29 15:46:42,134 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'option'}
2012-04-29 15:46:42,134 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'platform:pcspkr')
2012-04-29 15:46:42,135 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-29 15:46:42,135 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,135 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-29 15:46:42,135 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2012-04-29 15:46:42,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001002d00004385sv00001179sd0000FF6Abc0Csc05i00')
2012-04-29 15:46:42,142 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-04-29 15:46:42,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,143 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-04-29 15:46:42,143 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001179sd0000FF6Abc06sc01i00')
2012-04-29 15:46:42,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-29 15:46:42,161 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-29 15:46:42,161 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,161 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-29 15:46:42,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-29 15:46:42,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-29 15:46:42,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-29 15:46:42,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'pci:v00001002d00004383sv00001179sd0000FF6Abc04sc03i00')
2012-04-29 15:46:42,169 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-29 15:46:42,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,169 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-29 15:46:42,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-29 15:46:42,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bccef0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-29 15:46:42,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:TOS1900:')
2012-04-29 15:46:42,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'input:b0003v1C4Fp0003e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-04-29 15:46:42,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-29 15:46:42,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:TOS1901:')
2012-04-29 15:46:42,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001002d00009613sv00001179sd0000FF6Abc03sc00i00')
2012-04-29 15:46:42,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-04-29 15:46:42,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 15:46:42,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-29 15:46:42,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc02ip00')
2012-04-29 15:46:42,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-29 15:46:42,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'platform:regulatory')
2012-04-29 15:46:42,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-29 15:46:42,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001022d00009600sv00001179sd0000FF6Abc06sc00i00')
2012-04-29 15:46:42,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2012-04-29 15:46:42,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-29 15:46:42,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-29 15:46:42,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-04-29 15:46:42,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001179sd0000FF6Abc01sc01i8a')
2012-04-29 15:46:42,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-29 15:46:42,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2012-04-29 15:46:42,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2012-04-29 15:46:42,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00ic08isc06ip50')
2012-04-29 15:46:42,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'usb:v04F2pB070d0834dcEFdsc02dp01ic0Eisc01ip00')
2012-04-29 15:46:42,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-29 15:46:42,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-29 15:46:42,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-29 15:46:42,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-29 15:46:42,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i00')
2012-04-29 15:46:42,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k100,101,102,103,110,111,145,14A,ra0,1,18,1C,mlsfw')
2012-04-29 15:46:42,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-29 15:46:42,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvr1.80:bd09/01/2009:svnTOSHIBA:pnSatelliteL300D:pvrPSLC8A-02200Y:rvnTOSHIBA:rnPortablePC:rvrBaseBoardVersion:cvnAMD:ct10:cvrNone:')
2012-04-29 15:46:42,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2012-04-29 15:46:42,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-29 15:46:42,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2012-04-29 15:46:42,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,80,8E,95,96,98,9B,A3,A4,A5,CD,E0,E1,E2,E3,E4,EC,EE,F0,1A2,1A3,1A4,1D0,212,ram4,lsfw')
2012-04-29 15:46:42,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'usb:v1058p1100d0175dc00dsc00dp00ic08isc06ip50')
2012-04-29 15:46:42,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'usb:v1C4Fp0003d0110dc00dsc00dp00ic03isc01ip02')
2012-04-29 15:46:42,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-29 15:46:42,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001002d00004396sv00001179sd0000FF6Abc0Csc03i20')
2012-04-29 15:46:42,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'input:b0003v04F2pB070e0834-e0,1,kD4,ramlsfw')
2012-04-29 15:46:42,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:SYN1913:SYN0700:SYN0002:PNP0F13:')
2012-04-29 15:46:42,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001002d00004390sv00001179sd0000FF6Abc01sc06i01')
2012-04-29 15:46:42,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-29 15:46:42,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'usb:v0BDAp8198d0200dc00dsc00dp00icFFiscFFipFF')
2012-04-29 15:46:42,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-04-29 15:46:42,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-29 15:46:42,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'usb:v19D2p1253d0000dc00dsc00dp00icFFiscFFipFF')
2012-04-29 15:46:42,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'platform:pcspkr')
2012-04-29 15:46:42,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2012-04-29 15:46:42,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001002d00004385sv00001179sd0000FF6Abc0Csc05i00')
2012-04-29 15:46:42,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001179sd0000FF6Abc06sc01i00')
2012-04-29 15:46:42,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-29 15:46:42,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-29 15:46:42,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'pci:v00001002d00004383sv00001179sd0000FF6Abc04sc03i00')
2012-04-29 15:46:42,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1f42f38> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-29 15:46:42,253 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:46:42,253 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:46:42,313 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:46:42,314 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 15:46:42,535 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:46:42,536 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:46:42,622 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:46:42,622 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:46:42,665 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:46:42,665 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-29 15:46:44,599 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:46:44,600 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:46:49,730 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-04-29 15:47:25,845 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:47:25,846 DEBUG: fglrx_updates is not the alternative in use
2012-04-29 15:47:25,872 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-29 15:47:25,873 DEBUG: fglrx_updates is not the alternative in use[/HTML]

please tell me how to fix this problem thank

---

### Post by 5ulo on 2012-04-29
I've got the same problem with the same log data

---

### Post by ingramproductions on 2012-05-01
Same problem here, same info in log file too

---

### Post by MonkeyPaw on 2012-05-01
What hardware?

Have you tried going to AMD.com and downloading their drivers directly?  They are relatively straightforward to install.

---

