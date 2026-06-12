---
title: "No wireless with new ubuntu :-("
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by dannodan2008 on 2012-05-10
Hi guys,
 Im wondering if someone can help me. I have limited knowledge of ubuntu. My problem is that since i have upgraded i have no wireless. I typed in drivers and found the additional drivers app/program which did provide me with the correct wireless drivers but when i try to activate it i get an error and tells me to check  /var/log/jockey.log   for details . Ok so i open terminal and enter the command and i get 

danno@danno-laptop:~$  /var/log/jockey.log
bash: /var/log/jockey.log: Permission denied
danno@danno-laptop:~$ sudo apt /var/log/jockey.log
[sudo] password for danno: 
sudo: apt: command not found
danno@danno-laptop:~$ 
 I know im probaly doing something really stupid wrong but can someone point me in the right direction please :-)
Thanks for reading this :-)
Regards
Danno

---

### Post by darkod on 2012-05-10
That is the location and name of the log file but you need to open it with some application, not just retype the path.

Try gedit, and in case it needs sudo permissions use gksu, like:
gksu gedit /var/log/jockey.log

---

### Post by dannodan2008 on 2012-05-12
HI, thanks for your reply. I done what you said and opened gedit but when i search in the location  /var/log/jockey.log it finds nothing. again im probaly missing something obvious  and again thanks for your time.

---

### Post by darkod on 2012-05-12
No need to search for it, you can open it directly with the command I gave you. Just open terminal and execute:
gksu gedit /var/log/jockey.log

That should open that file directly in gedit. If it asks you for your password, just enter it.

---

### Post by dannodan2008 on 2012-05-12
Cheers for being patient i told you im a noob lol. so i found the jockey file/log here it is ..
2012-05-12 22:34:41,519 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c>
2012-05-12 22:34:43,020 DEBUG: reading modalias file /lib/modules/3.0.0-19-generic-pae/modules.alias
2012-05-12 22:34:43,134 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-05-12 22:34:43,144 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-05-12 22:34:43,198 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-05-12 22:34:43,227 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-05-12 22:34:43,234 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-05-12 22:34:43,341 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-05-12 22:34:43,342 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-05-12 22:34:43,347 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-05-12 22:34:43,348 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-05-12 22:34:43,348 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-05-12 22:34:43,349 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-05-12 22:34:43,371 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-05-12 22:34:43,397 DEBUG: Software modem not available
2012-05-12 22:34:43,397 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-05-12 22:34:43,402 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-05-12 22:34:43,402 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-05-12 22:34:43,424 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-05-12 22:34:43,424 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-05-12 22:34:43,465 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-05-12 22:34:43,466 DEBUG: Firmware for DVB cards not available
2012-05-12 22:34:43,466 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-05-12 22:34:43,501 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-05-12 22:34:43,507 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-05-12 22:34:43,509 DEBUG: nvidia.available: falling back to default
2012-05-12 22:34:43,530 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-12 22:34:43,530 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-12 22:34:43,534 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-05-12 22:34:43,541 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-05-12 22:34:43,542 DEBUG: nvidia.available: falling back to default
2012-05-12 22:34:43,583 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-05-12 22:34:43,588 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-05-12 22:34:43,594 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-05-12 22:34:43,596 DEBUG: nvidia.available: falling back to default
2012-05-12 22:34:43,637 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-12 22:34:43,641 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-05-12 22:34:43,647 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-05-12 22:34:43,648 DEBUG: nvidia.available: falling back to default
2012-05-12 22:34:43,669 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-12 22:34:43,669 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-12 22:34:43,674 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-05-12 22:34:43,680 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-05-12 22:34:43,681 DEBUG: nvidia.available: falling back to default
2012-05-12 22:34:43,701 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-12 22:34:43,702 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-12 22:34:43,706 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-05-12 22:34:43,712 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-05-12 22:34:43,713 DEBUG: nvidia.available: falling back to default
2012-05-12 22:34:43,734 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-12 22:34:43,734 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-12 22:34:43,734 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-05-12 22:34:43,740 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-12 22:34:43,762 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-05-12 22:34:43,763 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-05-12 22:34:43,763 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-05-12 22:34:43,770 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-05-12 22:34:43,776 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-05-12 22:34:43,777 DEBUG: fglrx.available: falling back to default
2012-05-12 22:34:43,818 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-12 22:34:43,823 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-05-12 22:34:43,829 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-05-12 22:34:43,829 DEBUG: fglrx.available: falling back to default
2012-05-12 22:34:43,871 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-05-12 22:34:43,871 DEBUG: all custom handlers loaded
2012-05-12 22:34:43,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v000010DEd00000BE3sv0000103Csd0000365Cbc04sc03i00')
2012-05-12 22:34:44,138 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-12 22:34:44,233 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,233 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-05-12 22:34:44,237 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-12 22:34:44,237 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,237 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-12 22:34:44,237 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,237 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00003B03sv0000103Csd0000365Cbc06sc01i00')
2012-05-12 22:34:44,499 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-05-12 22:34:44,499 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000103Csd0000365Cbc06sc04i01')
2012-05-12 22:34:44,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-05-12 22:34:44,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'acpi:ENE0100:')
2012-05-12 22:34:44,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00003B3Csv0000103Csd0000365Cbc0Csc03i20')
2012-05-12 22:34:44,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'platform:reg-dummy')
2012-05-12 22:34:44,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-05-12 22:34:44,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-12 22:34:44,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'platform:pcspkr')
2012-05-12 22:34:44,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-05-12 22:34:44,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-05-12 22:34:44,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-05-12 22:34:44,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00003B2Fsv0000103Csd0000365Cbc01sc06i01')
2012-05-12 22:34:44,527 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-05-12 22:34:44,527 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,528 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-05-12 22:34:44,528 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-05-12 22:34:44,528 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-12 22:34:44,528 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-05-12 22:34:44,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00003B30sv0000103Csd0000365Cbc0Csc05i00')
2012-05-12 22:34:44,531 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-05-12 22:34:44,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'platform:lis3lv02d')
2012-05-12 22:34:44,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v0000197Bd00002382sv0000103Csd0000365Cbc08sc80i00')
2012-05-12 22:34:44,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-05-12 22:34:44,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'platform:hp-wmi')
2012-05-12 22:34:44,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-12 22:34:44,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00000044sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-05-12 22:34:44,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-05-12 22:34:44,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-12 22:34:44,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v000010DEd00000A68sv0000103Csd0000365Cbc03sc00i00')
2012-05-12 22:34:44,542 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2012-05-12 22:34:44,542 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,542 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2012-05-12 22:34:44,542 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,542 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2012-05-12 22:34:44,580 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-12 22:34:44,581 DEBUG: KMH enabled: False
2012-05-12 22:34:44,542 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-05-12 22:34:44,585 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-05-12 22:34:44,593 DEBUG: nvidia.available: falling back to default
2012-05-12 22:34:44,631 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-12 22:34:44,632 DEBUG: KMH enabled: False
2012-05-12 22:34:44,614 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-05-12 22:34:44,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2012-05-12 22:34:44,648 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-12 22:34:44,648 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-12 22:34:44,632 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-05-12 22:34:44,652 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-05-12 22:34:44,660 DEBUG: nvidia.available: falling back to default
2012-05-12 22:34:44,696 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-12 22:34:44,697 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-12 22:34:44,681 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-05-12 22:34:44,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00002D13sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,703 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'acpi:INT0800:')
2012-05-12 22:34:44,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'acpi:SYN1E10:SYN1E00:SYN0002:PNP0F13:')
2012-05-12 22:34:44,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-12 22:34:44,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00002D11sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-12 22:34:44,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'usb:v03F0p231Dd0306dcE0dsc01dp01icE0isc01ip01')
2012-05-12 22:34:44,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-05-12 22:34:44,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00002C62sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v000014E4d00004357sv0000103Csd0000145Ebc02sc80i00')
2012-05-12 22:34:44,764 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-05-12 22:34:44,765 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-12 22:34:44,765 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-05-12 22:34:44,769 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-12 22:34:44,769 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-12 22:34:44,769 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-05-12 22:34:44,769 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2012-05-12 22:34:44,769 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00003B34sv0000103Csd0000365Cbc0Csc03i20')
2012-05-12 22:34:44,773 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-05-12 22:34:44,773 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-12 22:34:44,773 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,773 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-05-12 22:34:44,773 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-12 22:34:44,774 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'usb:v03F0p231Dd0306dcE0dsc01dp01icFEisc01ip01')
2012-05-12 22:34:44,774 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-05-12 22:34:44,774 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'input:b0003v064EpC107e0231-e0,1,kD4,ramlsfw')
2012-05-12 22:34:44,775 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-12 22:34:44,775 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2012-05-12 22:34:44,775 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-12 22:34:44,775 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,775 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-12 22:34:44,775 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,775 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-12 22:34:44,776 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,776 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00003B56sv0000103Csd0000365Cbc04sc03i00')
2012-05-12 22:34:44,779 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-12 22:34:44,779 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.13:bd12/03/2009:svnHewlett-Packard:pnHPPaviliondv7NotebookPC:pvr049D210000241210000020000:rvnHewlett-Packard:rn365C:rvr32.23:cvnHewlett-Packard:ct10:cvrN/A:')
2012-05-12 22:34:44,793 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-12 22:34:44,793 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-12 22:34:44,794 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-12 22:34:44,794 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00002D12sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2012-05-12 22:34:44,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'usb:v064EpC107d0231dcEFdsc02dp01ic0Eisc01ip00')
2012-05-12 22:34:44,797 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-05-12 22:34:44,797 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00002D10sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-12 22:34:44,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-05-12 22:34:44,800 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-12 22:34:44,800 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-12 22:34:44,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v0000197Bd00002384sv0000103Csd0000365Cbc08sc80i00')
2012-05-12 22:34:44,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'usb:v03F0p231Dd0306dcE0dsc01dp01icFFiscFFipFF')
2012-05-12 22:34:44,801 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-05-12 22:34:44,801 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-05-12 22:34:44,801 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-05-12 22:34:44,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00002D01sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v0000197Bd00002383sv0000103Csd0000365Cbc08sc80i00')
2012-05-12 22:34:44,804 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms'}
2012-05-12 22:34:44,805 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd0000365Cbc02sc00i00')
2012-05-12 22:34:44,812 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-05-12 22:34:44,812 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-12 22:34:44,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-05-12 22:34:44,813 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-12 22:34:44,813 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-05-12 22:34:44,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'usb:v064EpC107d0231dcEFdsc02dp01ic0Eisc02ip00')
2012-05-12 22:34:44,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v0000197Bd00002380sv0000103Csd0000365Cbc0Csc00i10')
2012-05-12 22:34:44,813 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-05-12 22:34:44,814 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'platform:eisa')
2012-05-12 22:34:44,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v00008086d00003B32sv0000103Csd00000000bc11sc80i00')
2012-05-12 22:34:44,817 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_ips'}
2012-05-12 22:34:44,817 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_ips', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-12 22:34:44,825 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-05-12 22:34:44,825 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,825 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-05-12 22:34:44,825 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,825 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-12 22:34:44,825 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-12 22:34:44,825 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,825 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'pci:v0000197Bd00002381sv0000103Csd0000365Cbc08sc05i01')
2012-05-12 22:34:44,826 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-05-12 22:34:44,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,826 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-05-12 22:34:44,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,1,4,14,k71,72,73,74,77,80,A1,A4,A7,A8,AE,CF,D0,D2,D4,E0,E1,E2,160,164,166,16D,16E,170,171,172,174,175,179,181,182,183,185,188,189,18E,18F,190,191,192,193,197,19C,1A9,200,201,202,203,204,205,206,207,208,209,20A,20B,ram4,lsfw')
2012-05-12 22:34:44,826 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-12 22:34:44,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-05-12 22:34:44,826 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-12 22:34:44,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7209d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v000010DEd00000BE3sv0000103Csd0000365Cbc04sc03i00')
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00003B03sv0000103Csd0000365Cbc06sc01i00')
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000103Csd0000365Cbc06sc04i01')
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'acpi:ENE0100:')
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00003B3Csv0000103Csd0000365Cbc0Csc03i20')
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'platform:reg-dummy')
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'platform:pcspkr')
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00003B2Fsv0000103Csd0000365Cbc01sc06i01')
2012-05-12 22:34:44,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00003B30sv0000103Csd0000365Cbc0Csc05i00')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'platform:lis3lv02d')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v0000197Bd00002382sv0000103Csd0000365Cbc08sc80i00')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'platform:hp-wmi')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00000044sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v000010DEd00000A68sv0000103Csd0000365Cbc03sc00i00')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00002D13sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'acpi:INT0800:')
2012-05-12 22:34:44,828 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'acpi:SYN1E10:SYN1E00:SYN0002:PNP0F13:')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00002D11sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'usb:v03F0p231Dd0306dcE0dsc01dp01icE0isc01ip01')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00002C62sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v000014E4d00004357sv0000103Csd0000145Ebc02sc80i00')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00003B34sv0000103Csd0000365Cbc0Csc03i20')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'usb:v03F0p231Dd0306dcE0dsc01dp01icFEisc01ip01')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'input:b0003v064EpC107e0231-e0,1,kD4,ramlsfw')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00003B56sv0000103Csd0000365Cbc04sc03i00')
2012-05-12 22:34:44,829 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.13:bd12/03/2009:svnHewlett-Packard:pnHPPaviliondv7NotebookPC:pvr049D210000241210000020000:rvnHewlett-Packard:rn365C:rvr32.23:cvnHewlett-Packard:ct10:cvrN/A:')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00002D12sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'usb:v064EpC107d0231dcEFdsc02dp01ic0Eisc01ip00')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00002D10sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v0000197Bd00002384sv0000103Csd0000365Cbc08sc80i00')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'usb:v03F0p231Dd0306dcE0dsc01dp01icFFiscFFipFF')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00002D01sv0000103Csd0000365Cbc06sc00i00')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v0000197Bd00002383sv0000103Csd0000365Cbc08sc80i00')
2012-05-12 22:34:44,830 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd0000365Cbc02sc00i00')
2012-05-12 22:34:44,831 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-12 22:34:44,831 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-05-12 22:34:44,831 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-05-12 22:34:44,831 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'usb:v064EpC107d0231dcEFdsc02dp01ic0Eisc02ip00')
2012-05-12 22:34:44,831 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v0000197Bd00002380sv0000103Csd0000365Cbc0Csc00i10')
2012-05-12 22:34:44,831 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'platform:eisa')
2012-05-12 22:34:44,831 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v00008086d00003B32sv0000103Csd00000000bc11sc80i00')
2012-05-12 22:34:44,831 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-12 22:34:44,831 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-12 22:34:44,831 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'pci:v0000197Bd00002381sv0000103Csd0000365Cbc08sc05i01')
2012-05-12 22:34:44,831 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,1,4,14,k71,72,73,74,77,80,A1,A4,A7,A8,AE,CF,D0,D2,D4,E0,E1,E2,160,164,166,16D,16E,170,171,172,174,175,179,181,182,183,185,188,189,18E,18F,190,191,192,193,197,19C,1A9,200,201,202,203,204,205,206,207,208,209,20A,20B,ram4,lsfw')
2012-05-12 22:34:44,831 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-05-12 22:34:44,831 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68fe90c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-12 22:34:44,852 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-12 22:34:44,918 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-12 22:34:44,918 DEBUG: KMH enabled: False
2012-05-12 22:34:45,865 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-12 22:34:45,865 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-12 22:34:46,756 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-12 22:34:46,787 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-12 22:34:46,817 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-12 22:34:46,818 DEBUG: KMH enabled: False
2012-05-12 22:34:46,851 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-12 22:34:46,851 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-12 22:34:50,557 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-12 22:34:55,007 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-12 22:34:55,007 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-05-12 22:34:55,068 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-12 22:35:04,673 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-12 22:35:04,709 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-12 22:35:04,709 DEBUG: KMH enabled: False
2012-05-12 22:35:04,745 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-12 22:35:04,746 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-12 22:35:04,772 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-12 22:35:04,807 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-12 22:35:04,838 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-12 22:35:04,839 DEBUG: KMH enabled: False
2012-05-12 22:35:04,872 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-12 22:35:04,872 DEBUG: nvidia_current_updates is not the alternative in use

i cant understand any of this :-( i need wireless ..
Danno

---

### Post by darkod on 2012-05-12
Did you need to install any special drivers, or installing them in special way, with the previous release? Or it worked straight out of the box?

---

### Post by westie457 on 2012-05-12
Can you remember which model of Broadcom wireless chip you have or post the output of ```
lspci -vnn | grep network
```

---

### Post by dannodan2008 on 2012-05-15
Hi,
    Sorry for the late reply. Darkod, yes on my previous ubuntu i did need to install the broadcom driver but if my memory serves me right i was prompted on the first startup and it completred successfully.
 and wetie457 thanks for the interest. when i get home i will give you the results. thanks again
danno

---

### Post by dannodan2008 on 2012-05-15
> **westie457 said:**
> Can you remember which model of Broadcom wireless chip you have or post the output of ```
lspci -vnn | grep network
```

I realise im probaly doing something stupid here but this is what ive got :mad:
danno@danno-laptop:~$ lspci -vnn | grep network
danno@danno-laptop:~$ lspci -vnn | grep network
danno@danno-laptop:~$ sudo apt lspci -vnn | grep network
[sudo] password for danno: 
sudo: apt: command not found
danno@danno-laptop:~$ 


Danno

---

### Post by dannodan2008 on 2012-05-15
the driver im trying to install in attatchment.

---

### Post by darkod on 2012-05-15
If you use 'sudo' it's only 'sudo', not 'sudo apt' together.

But in this case I think you odn't need sudo rights. Try without the grep, only:
lspci

That will show all PCI devices, the network card included. Look for broadcom.

Is there any chance it's disabled in BIOS or with the wi-fi button on the laptop?

---

### Post by darkod on 2012-05-15
> **dannodan2008 said:**
> the driver im trying to install in attatchment.

The gray means it's not active, it says so. Try selecting that driver, and the button Activate below.

---

### Post by dannodan2008 on 2012-05-19
> **darkod said:**
> The gray means it's not active, it says so. Try selecting that driver, and the button Activate below.

Hi mate, again sorry for the late reply. i have had to stay away with  work. Please can you post the command so i can literally just copy and  paste it into the reminal because im not getting anything and im so  frustrated. Also the wireless is activated by the button. in reply to  your message darkod, yes i have tried activating the driver via the  button but that is when i get the error message which takes us back to  the beginning of the thread mate. the " JOCKEY" file i couldnt open. As  for the bios part unless my laptop would of done it automatically during  upgrade then no it is not tuned off in bios. 
Please be patient with me lol
Regards
Danno

---

### Post by dannodan2008 on 2012-05-19
> **darkod said:**
> If you use 'sudo' it's only 'sudo', not 'sudo apt' together.

But in this case I think you odn't need sudo rights. Try without the grep, only:
lspci

That will show all PCI devices, the network card included. Look for broadcom.

Is there any chance it's disabled in BIOS or with the wi-fi button on the laptop?


im clueless with this i cannot get that command to work i have been trying all day

danno@danno-laptop:~$ lspci -vnn | network
network: command not found
danno@danno-laptop:~$ sudo lspci -vnn | grep network
[sudo] password for danno: 
danno@danno-laptop:~$ sudo lspci -vnn | grep network
danno@danno-laptop:~$ sudo lspci -vnn | network
network: command not found
danno@danno-laptop:~$ sudo ldpci
sudo: ldpci: command not found
danno@danno-laptop:~$

---

### Post by westie457 on 2012-05-19
APOLOGIES that command is not right.

lspci -vnn

will give us the necessary information to point you in the right direction for the wireless driver.

---

### Post by darkod on 2012-05-19
Come on, man. Read...

In all of those you posted you never tried just lspci. Forget about the grep options, forget about sudo, just open terminal, enter:

lspci

Hit Enter. It's simple. :)

---

### Post by dannodan2008 on 2012-05-19
> **darkod said:**
> Come on, man. Read...

In all of those you posted you never tried just lspci. Forget about the grep options, forget about sudo, just open terminal, enter:

lspci

Hit Enter. It's simple. :)

Im sorry ! i have been honest about being numb to ubuntu. and i was given a few other commands which had no effect. I have done what you asked and here it is ..
danno@danno-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation G98M [GeForce G105M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
danno@danno-laptop:~$

---

### Post by darkod on 2012-05-19
OK, Broadcom BCM43225.

Try if this will install something it might need, I've seen it around for broadcom bc43 chips:

sudo apt-get install firmware-bc43-installer

I think that's the driver at the same time, but I can't be 100% sure as I don't have that card.

Install that, if there are no errors reboot and check if it's working. If it's not, try again activating the driver it reports in Hardware (if still there).

---

### Post by dannodan2008 on 2012-05-19
> **darkod said:**
> OK, Broadcom BCM43225.

Try if this will install something it might need, I've seen it around for broadcom bc43 chips:

sudo apt-get install firmware-bc43-installer

I think that's the driver at the same time, but I can't be 100% sure as I don't have that card.

Install that, if there are no errors reboot and check if it's working. If it's not, try again activating the driver it reports in Hardware (if still there).

Aaaaaarrrgghh ..
danno@danno-laptop:~$ sudo apt-get install firmware-bc43-installer
[sudo] password for danno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-bc43-installer
danno@danno-laptop:~$

---

### Post by darkod on 2012-05-19
Do you have some of the sources disabled?

Look in Software Centre, in the menu on the top bar (don't remember now exactly where) should be option Software Sources.

Look in Updates tab, which repositories are selected.

---

### Post by westie457 on 2012-05-19
```
sudo apt-get install firmware-b43-installer
```

is the right command

---

### Post by dannodan2008 on 2012-05-19
[QUOTE=darkod;11950666]Do you have some of the sources disabled?

Look in Software Centre, in the menu on the top bar (don't remember now exactly where) should be option Software Sources.

Look in Updates tab, which repositories are selected.[/

I have the top two selected, and proposed and unsupported not selected

---

### Post by dannodan2008 on 2012-05-19
i have just selected all checkboxs and tried the process again and still cant retrieve the package. just to let you know.

---

### Post by westie457 on 2012-05-19
Shall we try again using this.

Open Software Centre as before to 'Select Sources'

In the 'Ubuntu Software' tab put a check mark in all of the boxes except for the one called source.

 In the 'Updates' tab check the first 2 boxes and the fourth box, leave the third empty. Click on 'Close' 

Open a terminal and run ```
sudo apt-get update

sudo apt-get install firmware-b43-installer
```

Post back here with the news.

Thank you

---

### Post by dannodan2008 on 2012-05-20
> **westie457 said:**
> Shall we try again using this.

Open Software Centre as before to 'Select Sources'

In the 'Ubuntu Software' tab put a check mark in all of the boxes except for the one called source.

 In the 'Updates' tab check the first 2 boxes and the fourth box, leave the third empty. Click on 'Close' 

Open a terminal and run ```
sudo apt-get update

sudo apt-get install firmware-b43-installer
```Post back here with the news.

Thank you

Hi again, I have done what you asked and here are the results..


  	 	 	 	 	 	   danno@danno-laptop:~$ sudo apt-get update  
 [sudo] password for danno:  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease  
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                              
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                              
 Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]           
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                            
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                  
 Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]             
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                            
 Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                       
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                    
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                  
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                         
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex               
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                      
 Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [8,976 B]        
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                  
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex               
 Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]     
 Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [4,063 B]    
 Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [696 B]    
 Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [35.0 kB]  
 Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]  
 Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [9,409 B]  
 Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,393 B]  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex           
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex       
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en             
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en       
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                        
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en         
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB              
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                 
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB              
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                 
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise InRelease                              
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates InRelease                      
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports InRelease                    
 Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg [198 B]                 
 Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
 Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
 Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release [49.6 kB]                   
 Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release [49.6 kB]           
 Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release [49.6 kB]         
 Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources [934 kB]               
 Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources [5,470 B]        
 Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources [5,019 kB]         
 Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources [155 kB]         
 Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]       
 Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]  
 Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]   
 Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex                                                                                
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex                                                                          
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex                                                                          
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex                                                                            
 Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources [41.3 kB]                                                                    
 Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources [1,379 B]                                                              
 Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources [11.5 kB]                                                                
 Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources [696 B]                                                                
 Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages [111 kB]                                                               
 Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages [2,439 B]                                                        
 Get:32 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages [33.6 kB]                                                          
 Get:33 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages [1,393 B]                                                        
 Get:34 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex [73 B]                                                              
 Get:35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [71 B]                                                        
 Get:36 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex [71 B]                                                        
 Get:37 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex [73 B]                                                          
 Get:38 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages [559 B]                                                              
 Get:39 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages [14 B]                                                         
 Get:40 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages [2,379 B]                                                        
 Get:41 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]                                                         
 Get:42 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex [71 B]                                                            
 Get:43 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [70 B]                                                      
 Get:44 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex [70 B]                                                      
 Get:45 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex [72 B]                                                        
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB                                                                               
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en                                                                                  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB                                                                         
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en                                                                            
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB                                                                         
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en                                                                            
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB                                                                           
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en                                                                              
 Get:46 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en [53.6 kB]                                                             
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                                    
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en                                                                    
 Get:47 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en [20.9 kB]                                                         
 Get:48 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en [308 B]                                                             
 Get:49 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en [14 B]                                                        
 Get:50 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en [14 B]                                                        
 Get:51 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en [1,477 B]                                                       
 Fetched 12.9 MB in 34s (374 kB/s)                                                                                                             
 Reading package lists... Done  
 danno@danno-laptop:~$ sudo apt-get install firmware-b43-installer  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following packages were automatically installed and are no longer required:  
   libindicator6 libapt-pkg4.11 libglew1.5 libglewmx1.5 libgssdp-1.0-2  
   liblwres60 libept1 gir1.2-dee-0.5 zeitgeist-extension-fts libblas3gf  
   libquvi0 libattica0 libdb4.8 python-wnck libgnome-desktop-2-17  
 Use 'apt-get autoremove' to remove them.  
 The following extra packages will be installed:  
   b43-fwcutter  
 The following NEW packages will be installed  
   b43-fwcutter firmware-b43-installer  
 0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.  
 Need to get 22.4 kB of archives.  
 After this operation, 111 kB of additional disk space will be used.  
 Do you want to continue [Y/n]? y  
 Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main b43-fwcutter i386 1:015-9 [18.9 kB]  
 Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/multiverse firmware-b43-installer all 1:015-9 [3,524 B]  
 Fetched 22.4 kB in 24s (927 B/s)                 
 Selecting previously unselected package b43-fwcutter.  
 (Reading database ... 253965 files and directories currently installed.)  
 Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a015-9_i386.deb) ...  
 Selecting previously unselected package firmware-b43-installer.  
 Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a015-9_all.deb) ...  
 Processing triggers for man-db ...  
 Setting up b43-fwcutter (1:015-9) ...  
 Setting up firmware-b43-installer (1:015-9) ...  
 No chroot environment found. Starting normal installation  
 This card work with newer 5.10.56.27.3 firmware. Trying to install it.  
 --2012-05-20 14:48:29--  [http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2) 
 Resolving mirror2.openwrt.org (mirror2.openwrt.org)... 46.4.11.11  
 Connecting to mirror2.openwrt.org (mirror2.openwrt.org)|46.4.11.11|:80... connected.  
 HTTP request sent, awaiting response... 200 OK  
 Length: 1596823 (1.5M) [application/x-bzip2]  
 Saving to: `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2'  
 

 100%[======================================>] 1,596,823    533K/s   in 2.9s     
 

 2012-05-20 14:48:32 (533 KB/s) - `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2' saved [1596823/1596823]  
 

 broadcom-wl-5.10.56.27.3/driver/  
 broadcom-wl-5.10.56.27.3/driver/Makefile 
 broadcom-wl-5.10.56.27.3/driver/aiutils.c 
 broadcom-wl-5.10.56.27.3/driver/bcmsrom.c 
 broadcom-wl-5.10.56.27.3/driver/bcmutils.c 
 broadcom-wl-5.10.56.27.3/driver/hnddma.c 
 broadcom-wl-5.10.56.27.3/driver/hndpmu.c 
 broadcom-wl-5.10.56.27.3/driver/include/ 
 broadcom-wl-5.10.56.27.3/driver/include/UdpLib.h 
 broadcom-wl-5.10.56.27.3/driver/include/aidmp.h 
 broadcom-wl-5.10.56.27.3/driver/include/arminc.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcdc.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/ 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aes.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aeskeywrap.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bcmccx.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bn.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/ccx.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/des.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/dh.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/hmac_sha256.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md4.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md5.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/passhash.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/prf.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rc4.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rijndael-alg-fst.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha1.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha256.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/tkhash.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmdefs.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmdevs.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmendian.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmnvram.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmotp.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmparams.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmperf.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmrobo.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmsrom.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_fmt.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_tbl.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmstdlib.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmutils.h 
 broadcom-wl-5.10.56.27.3/driver/include/bcmwifi.h 
 broadcom-wl-5.10.56.27.3/driver/include/bitfuncs.h 
 broadcom-wl-5.10.56.27.3/driver/include/dmemc_core.h 
 broadcom-wl-5.10.56.27.3/driver/include/emf/ 
 broadcom-wl-5.10.56.27.3/driver/include/emf/emf/ 
 broadcom-wl-5.10.56.27.3/driver/include/emf/igs/ 
 broadcom-wl-5.10.56.27.3/driver/include/epivers.h 
 broadcom-wl-5.10.56.27.3/driver/include/epivers.h.in 
 broadcom-wl-5.10.56.27.3/driver/include/epivers.h.prev 
 broadcom-wl-5.10.56.27.3/driver/include/etioctl.h 
 broadcom-wl-5.10.56.27.3/driver/include/flash.h 
 broadcom-wl-5.10.56.27.3/driver/include/flashutl.h 
 broadcom-wl-5.10.56.27.3/driver/include/hndarm.h 
 broadcom-wl-5.10.56.27.3/driver/include/hndchipc.h 
 broadcom-wl-5.10.56.27.3/driver/include/hndcpu.h 
 broadcom-wl-5.10.56.27.3/driver/include/hnddma.h 
 broadcom-wl-5.10.56.27.3/driver/include/hndgige.h 
 broadcom-wl-5.10.56.27.3/driver/include/hndjtagdefs.h 
 broadcom-wl-5.10.56.27.3/driver/include/hndmips.h 
 broadcom-wl-5.10.56.27.3/driver/include/hndpci.h 
 broadcom-wl-5.10.56.27.3/driver/include/hndpmu.h 
 broadcom-wl-5.10.56.27.3/driver/include/hndsoc.h 
 broadcom-wl-5.10.56.27.3/driver/include/linux_gpio.h 
 broadcom-wl-5.10.56.27.3/driver/include/linux_osl.h 
 broadcom-wl-5.10.56.27.3/driver/include/linuxver.h 
 broadcom-wl-5.10.56.27.3/driver/include/min_osl.h 
 broadcom-wl-5.10.56.27.3/driver/include/mips33_core.h 
 broadcom-wl-5.10.56.27.3/driver/include/mips74k_core.h 
 broadcom-wl-5.10.56.27.3/driver/include/mipsinc.h 
 broadcom-wl-5.10.56.27.3/driver/include/ndiserrmap.h 
 broadcom-wl-5.10.56.27.3/driver/include/nicpci.h 
 broadcom-wl-5.10.56.27.3/driver/include/osl.h 
 broadcom-wl-5.10.56.27.3/driver/include/pci_core.h 
 broadcom-wl-5.10.56.27.3/driver/include/pcicfg.h 
 broadcom-wl-5.10.56.27.3/driver/include/pcie_core.h 
 broadcom-wl-5.10.56.27.3/driver/include/proto/ 
 broadcom-wl-5.10.56.27.3/driver/include/proto/802.11.h 
 broadcom-wl-5.10.56.27.3/driver/include/proto/802.11e.h 
 broadcom-wl-5.10.56.27.3/driver/include/proto/802.1d.h 
 broadcom-wl-5.10.56.27.3/driver/include/proto/bcmeth.h 
 broadcom-wl-5.10.56.27.3/driver/include/proto/bcmevent.h 
 broadcom-wl-5.10.56.27.3/driver/include/proto/bcmip.h 
 broadcom-wl-5.10.56.27.3/driver/include/proto/bcmtcp.h 
 broadcom-wl-5.10.56.27.3/driver/include/proto/eap.h 
 broadcom-wl-5.10.56.27.3/driver/include/proto/eapol.h 
 broadcom-wl-5.10.56.27.3/driver/include/proto/ethernet.h 
 broadcom-wl-5.10.56.27.3/driver/include/proto/vlan.h 
 broadcom-wl-5.10.56.27.3/driver/include/proto/wpa.h 
 broadcom-wl-5.10.56.27.3/driver/include/rts/ 
 broadcom-wl-5.10.56.27.3/driver/include/rts/crc.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbchipc.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbconfig.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbgige.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbhndarm.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbhndcpu.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbhnddma.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbhndpio.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbmemc.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbpcmcia.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbsdio.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbsdpcmdev.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbsdram.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbsocram.h 
 broadcom-wl-5.10.56.27.3/driver/include/sbsprom.h 
 broadcom-wl-5.10.56.27.3/driver/include/sflash.h 
 broadcom-wl-5.10.56.27.3/driver/include/siutils.h 
 broadcom-wl-5.10.56.27.3/driver/include/trxhdr.h 
 broadcom-wl-5.10.56.27.3/driver/include/typedefs.h 
 broadcom-wl-5.10.56.27.3/driver/include/wlc_ethereal.h 
 broadcom-wl-5.10.56.27.3/driver/include/wlioctl.h 
 broadcom-wl-5.10.56.27.3/driver/include/wllmacctl.h 
 broadcom-wl-5.10.56.27.3/driver/linux_osl.c 
 broadcom-wl-5.10.56.27.3/driver/nicpci.c 
 broadcom-wl-5.10.56.27.3/driver/nvram_stub.c 
 broadcom-wl-5.10.56.27.3/driver/sbutils.c 
 broadcom-wl-5.10.56.27.3/driver/siutils.c 
 broadcom-wl-5.10.56.27.3/driver/siutils_priv.h 
 broadcom-wl-5.10.56.27.3/driver/wl_apsta/ 
 broadcom-wl-5.10.56.27.3/driver/wl_apsta/buildflags.mk 
 broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o 
 broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/ 
 broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/buildflags.mk 
 broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/wl_prebuilt.o 
 broadcom-wl-5.10.56.27.3/driver/wl_dbg.h 
 broadcom-wl-5.10.56.27.3/driver/wl_export.h 
 broadcom-wl-5.10.56.27.3/driver/wl_iw.c 
 broadcom-wl-5.10.56.27.3/driver/wl_iw.h 
 broadcom-wl-5.10.56.27.3/driver/wl_linux.c 
 broadcom-wl-5.10.56.27.3/driver/wl_linux.h 
 broadcom-wl-5.10.56.27.3/driver/wlc_key.h 
 broadcom-wl-5.10.56.27.3/driver/wlc_pub.h 
 broadcom-wl-5.10.56.27.3/nas_exe.o  
 broadcom-wl-5.10.56.27.3/shared/  
 broadcom-wl-5.10.56.27.3/shared/Makefile 
 broadcom-wl-5.10.56.27.3/shared/UdpLib.c 
 broadcom-wl-5.10.56.27.3/shared/bcmcvar.h 
 broadcom-wl-5.10.56.27.3/shared/bcmtimer.h 
 broadcom-wl-5.10.56.27.3/shared/ctype.c 
 broadcom-wl-5.10.56.27.3/shared/linux_timer.c 
 broadcom-wl-5.10.56.27.3/shared/netconf.h 
 broadcom-wl-5.10.56.27.3/shared/opencrypto.h 
 broadcom-wl-5.10.56.27.3/shared/rte_timers.c 
 broadcom-wl-5.10.56.27.3/shared/shutils.c 
 broadcom-wl-5.10.56.27.3/shared/shutils.h 
 broadcom-wl-5.10.56.27.3/shared/wl.c  
 broadcom-wl-5.10.56.27.3/shared/wl_linux.c 
 broadcom-wl-5.10.56.27.3/shared/wlutils.h 
 broadcom-wl-5.10.56.27.3/wl_exe.o  
 This file is recognised as:  
   filename   :  wl_prebuilt.o  
   version    :  508.1084  
   MD5        :  490d4e149ecc45eb1a91f06aa75be071  
 Extracting b43/ucode19.fw  
 Extracting b43/lp0initvals14.fw  
 Extracting b43/ucode16_lp.fw  
 Extracting b43/ucode16_sslpn.fw  
   ucode revision: 1084  
 Extracting b43/lp0bsinitvals14.fw  
 Extracting b43/b0g0initvals9.fw  
 Extracting b43/sslpn2bsinitvals17.fw  
 Extracting b43/a0g1bsinitvals9.fw  
 Extracting b43/b0g0bsinitvals13.fw  
 Extracting b43/ucode16_sslpn_nobt.fw  
 Extracting b43/b0g0bsinitvals5.fw  
 Extracting b43/sslpn2initvals17.fw  
 Extracting b43/b0g0initvals13.fw  
 Extracting b43/ucode17.fw  
 Extracting b43/sslpn1bsinitvals20.fw  
 Extracting b43/ucode14.fw  
 Extracting b43/a0g0initvals5.fw  
 Extracting b43/lp0bsinitvals16.fw  
 Extracting b43/a0g1bsinitvals5.fw  
 Extracting b43/n0bsinitvals11.fw  
 Extracting b43/n0absinitvals11.fw  
 Extracting b43/a0g1bsinitvals13.fw  
 Extracting b43/pcm5.fw  
 Extracting b43/ucode9.fw  
 Extracting b43/a0g0bsinitvals9.fw  
 Extracting b43/ucode20.fw  
 Extracting b43/a0g1initvals5.fw  
 Extracting b43/n0bsinitvals16.fw  
 Extracting b43/lp0initvals15.fw  
 Extracting b43/b0g0initvals5.fw  
 Extracting b43/sslpn0initvals16.fw  
 Extracting b43/a0g1initvals13.fw  
 Extracting b43/sslpn2initvals19.fw  
 Extracting b43/a0g1initvals9.fw  
 Extracting b43/ucode5.fw  
 Extracting b43/lp0bsinitvals13.fw  
 Extracting b43/n0initvals16.fw  
 Extracting b43/b0g0bsinitvals9.fw  
 Extracting b43/ucode11.fw  
 Extracting b43/lp0initvals16.fw  
 Extracting b43/ucode16_mimo.fw  
 Extracting b43/a0g0initvals9.fw  
 Extracting b43/lp0initvals13.fw  
 Extracting b43/a0g0bsinitvals5.fw  
 Extracting b43/ucode13.fw  
 Extracting b43/sslpn2bsinitvals19.fw  
 Extracting b43/ucode15.fw  
 Extracting b43/lp0bsinitvals15.fw  
 Extracting b43/n0initvals11.fw  
 Extracting b43/sslpn0bsinitvals16.fw  
 Extracting b43/sslpn1initvals20.fw  
 danno@danno-laptop:~$  
  
Unfortunately the problem seems to have got worse. i still have no wireless ( same problem with activating the driver) but now my wireless button operates my bluetooth ?!?. Im so gutted with this new release :-(

Danno

---

### Post by westie457 on 2012-05-20
Yes the wireless does operate the Bluetooth.

Have you tried a restart?

After a restart could you post the results of these please. And put the output in ```
 tags by clicking the # at the top of the message pane - generates the tags - and paste between them.

[CODE]rfkill list all

lsmod
```

Thank you

---

### Post by dannodan2008 on 2012-05-20
Hi, this is the result for - rfkill list all


```
danno@danno-laptop:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
danno@danno-laptop:~$ 


```

And the same for - lsmod 

```
danno@danno-laptop:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
udf                    83826  1 
dm_crypt               22565  0 
snd_hda_codec_hdmi     31426  4 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  12 
bnep                   17923  2 
binfmt_misc            17292  1 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_idt      60049  1 
snd_hda_intel          28358  3 
snd_hda_codec          91888  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                63474  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
wmi                    18744  1 hp_wmi
ir_rc5_decoder         12490  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
ir_nec_decoder         12490  0 
rc_rc6_mce             12454  0 
ene_ir                 18214  0 
rc_core                25797  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
hp_accel               21632  0 
snd_timer              28932  2 snd_pcm,snd_seq
lis3lv02d              19280  1 hp_accel
input_polldev          13648  1 lis3lv02d
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
intel_ips              17753  0 
btusb                  18160  2 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth             148869  23 rfcomm,bnep,btusb
jmb38x_ms              17406  0 
memstick               15857  1 jmb38x_ms
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
video                  19069  0 
ahci                   21634  3 
libahci                25761  1 ahci
firewire_ohci          35846  0 
firewire_core          56937  1 firewire_ohci
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
crc_itu_t              12627  2 udf,firewire_core
r8169                  47200  0 
danno@danno-laptop:~$ 

```

also, yes i did restart before the last message and a full shut down after that.:confused:
Danno

---

### Post by westie457 on 2012-05-20
You are getting there.

May we see the results of ```
nm-tool
```please

---

### Post by dannodan2008 on 2012-05-20
> **westie457 said:**
> You are getting there.

May we see the results of ```
nm-tool
```please

```
 Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:26:9E:CE:EB:6C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.78
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


danno@danno-laptop:~$ 

```

---

### Post by darkod on 2012-05-20
westie looks much better than me with networking, but just to mention that I don't think I see a module loaded for the wifi card. This could be a problem since without the module loaded it's like the card is not even there.

---

### Post by dannodan2008 on 2012-05-22
thanks Darko, 
                           Westie can you help mate ? is there anyone out there who can talk a complete ubuntu noob into fixing this ?
Regards
A very desperate Danno who thinks he is going to end up with Win 7 again :-(  :mad:

---

### Post by darkod on 2012-05-22
Try this:
Open /etc/modules.conf with:

gksu gedit /etc/modules.conf

At the end, add a line with only:
b43

Save and close. Reboot.

See if wi-fi works, you can also post again the results of:
lsmod

like you did earlier.

---

### Post by darkod on 2012-05-22
Actually, as a quick temporary try you can do in terminal:

sudo modprobe -a b43

Try to disable/enable the wireless in Network Manager. See if that helped.

---

### Post by dannodan2008 on 2012-05-22
> **darkod said:**
> Actually, as a quick temporary try you can do in terminal:

sudo modprobe -a b43

Try to disable/enable the wireless in Network Manager. See if that helped.
 Hi Darko,
  I could not get anything in terminal with sudo modprobe -a b43.

```
danno@danno-laptop:~$ sudo modprobe -a b43
[sudo] password for danno: 
danno@danno-laptop:~$ 

```
  So i opened network and looked to disable/enable the wireless but cannot find the option to do so .
 
Here is lsmod again
```
danno@danno-laptop:~$ lsmod
Module                  Size  Used by
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31444  0 
ntfs                  100171  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55577  2 vfat,msdos
jfs                   175084  0 
xfs                   746838  0 
reiserfs              230932  0 
b43                   318816  0 
ssb                    50682  1 b43
mac80211              393421  1 b43
cfg80211              172427  2 b43,mac80211
nls_utf8               12493  1 
udf                    83826  1 
dm_crypt               22565  0 
rfcomm                 38408  12 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  4 
hp_wmi                 13652  0 
joydev                 17393  0 
sparse_keymap          13658  1 hp_wmi
btusb                  18160  2 
psmouse                63474  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_codec_idt      60049  1 
ir_lirc_codec          12770  0 
intel_ips              17753  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
snd_rawmidi            25241  1 snd_seq_midi
bluetooth             148869  23 rfcomm,bnep,btusb
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
snd_hda_intel          28358  3 
snd_hda_codec          91888  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ir_nec_decoder         12490  0 
rc_rc6_mce             12454  0 
ene_ir                 18214  0 
rc_core                25797  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
jmb38x_ms              17406  0 
hp_accel               21632  0 
lis3lv02d              19280  1 hp_accel
input_polldev          13648  1 lis3lv02d
memstick               15857  1 jmb38x_ms
wmi                    18744  1 hp_wmi
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
ahci                   21634  3 
libahci                25761  1 ahci
video                  19069  0 
firewire_ohci          35846  0 
r8169                  47200  0 
firewire_core          56937  1 firewire_ohci
sdhci_pci              13658  0 
crc_itu_t              12627  2 udf,firewire_core
sdhci                  27360  1 sdhci_pci
danno@danno-laptop:~$ 

```

Also i have followed your instruction above through gedit/etc/modules.conf but i am not sure where to add the information. I have included a screenshot so maybe you can tell me where. I hope this is right. i rebooted and no difference  mate

---

### Post by dannodan2008 on 2012-05-22
...

---

### Post by darkod on 2012-05-22
In the latest lsmod output you can clearly see the b43 module loaded.

There wasn't supposed to be any reply from the modprobe command, it just loads the module and it did.

Assuming you haven't restarted yet, what does:
ifconfig -a

say now?

Also, about the /etc/modules and the screenshot, under the line with 'lp' simply write:
b43

in a new line. That's it.

---

### Post by dannodan2008 on 2012-05-22
> **darkod said:**
> In the latest lsmod output you can clearly see the b43 module loaded.

There wasn't supposed to be any reply from the modprobe command, it just loads the module and it did.

Assuming you haven't restarted yet, what does:
ifconfig -a

say now?

Also, about the /etc/modules and the screenshot, under the line with 'lp' simply write:
b43

in a new line. That's it.

Hi Darko,
                  the reply to ifconfig -a was 

```
danno@danno-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:9e:ce:eb:6c  
          inet addr:192.168.1.78  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:9eff:fece:eb6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1091 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1169109 (1.1 MB)  TX bytes:282273 (282.2 KB)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:234194 (234.1 KB)  TX bytes:234194 (234.1 KB)

danno@danno-laptop:~$ 


```
  The next step, i am trying to add b43 to the line where you stated but i cannot save it. im assuming it is because this is "readonly" how do i overcome this in ubuntu so i can save it please?
Danno

---

### Post by dannodan2008 on 2012-05-22
...

---

### Post by darkod on 2012-05-22
Forget about /etc/modules at the moment. I think I know why it's read-only, we'll sort it out later.

The wireless still doesn't show up. Are you sure it's not disabled by the button switch or in BIOS? Double check that.

When it's available you should see it when you click the Network Manager icon top right. I guess you know by now what icon are we talking about. :)

There should be Enable Wireless option inside the menu that opens when clicking the icon, and also it might even show wifi networks that are available.

---

### Post by dannodan2008 on 2012-05-22
> **darkod said:**
> Forget about /etc/modules at the moment. I think I know why it's read-only, we'll sort it out later.

The wireless still doesn't show up. Are you sure it's not disabled by the button switch or in BIOS? Double check that.

When it's available you should see it when you click the Network Manager icon top right. I guess you know by now what icon are we talking about. :)

There should be Enable Wireless option inside the menu that opens when clicking the icon, and also it might even show wifi networks that are available.

Hi Darko,
                  Jeez, this is a big learning curve for me lol :-) So....
BIOS- I have just entered the bios (for the first time ever)  and the only thing i noticed is that in one section it reads   " Internal Network Adapter[disabled]"Is this what i am looking for ?. 
Also on the main page of bios (the first one)  where there is info on everything, product conf , WLAN FCC ID, Bluetooth FCC ID etc. I noticed that the only field that is blank with no info is the WLAN FCC ID. I have changed nothing yet untill i hear from you incase i mess up my wireless for Win 7 (as i dual boot).
The Wireless Switch/Touchkey -  Since one of the commands you or westie gave me before the wireless key has started to turn my bluetooth on and off. Still not giving me wireless. I have no wireless options when i click the network option (top right). This is how my menu looks,
Wired Network
Disconnect 
VPN Connections ->
Enable Networking-(which is ticked)
Connection Information
Edit Connections
In " edit connections" i can add edit or delete a network but no option to look or join one. It just says my home network last used 14 days ago (before attempted upgrade).
 I think i covered what you asked. ?? If not explained in a very tech head way :-)
Thanks Danno

---

### Post by darkod on 2012-05-22
The internal network adapter might refer to the wired, but if it says Disabled then how come it's working.
In any case, I would Enable that option. That shouldn't interfere with using your wi-fi in windows.

Yes, you are looking at the correct place, under Enable Networking there should be Enable Wireless when it recognizes the wi-fi card.

Don't forget that at this moment you still didn't set up the b43 module to load at boot, so after every reboot you need to load it manually to see if the wi-fi will work. That modprobe command loads it:
sudo modprobe -a b43

Until we can confirm that module is making your wi-fi work there is no point including it in /etc/modules anyway.

As for the wireless key turning bluetooth on and off, that's normal. Usually they call it wireless key but in fact it enables/disables together the wi-fi and the bluetooth. Make sure it's on enable.

---

### Post by dannodan2008 on 2012-05-22
Sorry, silly i know.  I just went into bios and i read it wrong. it is in "boot options" and it reads " Internal Network Adapter Boot" . I missed the boot :-(. do you still want me to enable it ?

---

### Post by dannodan2008 on 2012-05-22
Also, i just restarted- loaded b43 (sudo modprobe -a b43) then tried to activate driver. Still same message. not sure if important just thought id chuck it out there

---

### Post by darkod on 2012-05-22
No, if it's related to the boot no need to enable it.

We might be barking under the wrong tree, if that module is not correct for your card, but it seemed so.

I'm out of ideas, and westie seems busy these days to visit the forum.

I just found something that could be related. Try this in terminal:
sudo modprobe -r hp_wmi

Tell us what happens.

---

### Post by darkod on 2012-05-22
OK, just found new info.

We were barking under the wrong tree, that is not the correct driver for that card. So, we will not try to configure bc43 to load at boot because it's not needed.

At the moment, forget all the previous posts, lets try this first:

sudo apt-get update
sudo apt-get install bcmwl-kernel-source

After that look in Hardware if there is driver named STA that is not activated. If there is, activate it.
Reboot.

Let us know.

---

### Post by dannodan2008 on 2012-05-22
> **darkod said:**
> No, if it's related to the boot no need to enable it.

We might be barking under the wrong tree, if that module is not correct for your card, but it seemed so.

I'm out of ideas, and westie seems busy these days to visit the forum.

I just found something that could be related. Try this in terminal:
sudo modprobe -r hp_wmi

Tell us what happens.
  
I rebooted and run the command and nothing happened in terminal. no wireless appeared and the driver still wont activate.  :-( 
Darko,I have a couple of questions for you.
1- Is there anyway i can make this thread reach more people using the forum ? ive never used forums before.
2- I have just found a site online 
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)
 it says it makes win drivers work in linux and it seems my card is in the known working category. Can i ask your opinion on this please ? and if you think my " knowledge" lol could pull it off.  I have heard before that you should never download a program that doesnt come from the software centre
Danno

---

### Post by darkod on 2012-05-22
I made another post meanwhile. look at post #45. If you are only looking in your email you only receive the first reply by email, don't rely on that. Visit the thread more often if you can.

Lets see if post #45 helps and after that is installed we can troubleshoot because so far we have been working with the wrong driver.

Hold on with that ndiswrapper link for now.

---

### Post by dannodan2008 on 2012-05-22
> **darkod said:**
> OK, just found new info.

We were barking under the wrong tree, that is not the correct driver for that card. So, we will not try to configure bc43 to load at boot because it's not needed.

At the moment, forget all the previous posts, lets try this first:

sudo apt-get update
sudo apt-get install bcmwl-kernel-source

After that look in Hardware if there is driver named STA that is not activated. If there is, activate it.
Reboot.

Let us know.

 The command read that the newest version is already installed
```
danno@danno-laptop:~$ sudo apt-get update
[sudo] password for danno: 
Ign http://extras.ubuntu.com precise InRelease
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Ign http://archive.canonical.com precise InRelease                             
Ign http://archive.canonical.com precise InRelease                             
Ign http://security.ubuntu.com precise-security InRelease                      
Hit http://extras.ubuntu.com precise Release                                   
Ign http://gb.archive.ubuntu.com precise InRelease                   
Ign http://gb.archive.ubuntu.com precise-updates InRelease           
Ign http://gb.archive.ubuntu.com precise-backports InRelease         
Hit http://archive.canonical.com precise Release.gpg                 
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B] 
Hit http://archive.canonical.com precise Release.gpg                  
Get:3 http://gb.archive.ubuntu.com precise Release.gpg [198 B]        
Get:4 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://archive.canonical.com precise Release                               
Get:6 http://gb.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://archive.canonical.com precise Release                               
Get:7 http://gb.archive.ubuntu.com precise Release [49.6 kB]                   
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:8 http://security.ubuntu.com precise-security/main Sources [11.5 kB]       
Get:9 http://gb.archive.ubuntu.com precise-updates Release [49.6 kB]           
Get:10 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Get:11 http://security.ubuntu.com precise-security/universe Sources [4,063 B]  
Get:12 http://gb.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:13 http://security.ubuntu.com precise-security/multiverse Sources [696 B]  
Get:14 http://security.ubuntu.com precise-security/main i386 Packages [42.1 kB]
Get:15 http://gb.archive.ubuntu.com precise/main Sources [934 kB]              
Get:16 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:17 http://security.ubuntu.com precise-security/universe i386 Packages [9,616 B]
Get:18 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,393 B]
Get:19 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:20 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:21 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:22 http://security.ubuntu.com precise-security/universe TranslationIndex [72 B]
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Get:23 http://security.ubuntu.com precise-security/main Translation-en [19.5 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://archive.canonical.com precise/partner Translation-en_GB             
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:24 http://security.ubuntu.com precise-security/universe Translation-en [7,227 B]
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://archive.canonical.com precise/partner Translation-en_GB
Ign http://archive.canonical.com precise/partner Translation-en
Get:25 http://gb.archive.ubuntu.com precise/restricted Sources [5,470 B]
Get:26 http://gb.archive.ubuntu.com precise/universe Sources [5,019 kB]
Get:27 http://gb.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:28 http://gb.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:29 http://gb.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:30 http://gb.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:31 http://gb.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex             
Get:32 http://gb.archive.ubuntu.com precise-updates/main Sources [42.4 kB]     
Get:33 http://gb.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:34 http://gb.archive.ubuntu.com precise-updates/universe Sources [12.3 kB] 
Get:35 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [696 B] 
Get:36 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [113 kB]
Get:37 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:38 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [34.4 kB]
Get:39 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [1,393 B]
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:40 http://gb.archive.ubuntu.com precise-backports/main i386 Packages [559 B]
Get:41 http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages [14 B]
Get:42 http://gb.archive.ubuntu.com precise-backports/universe i386 Packages [2,379 B]
Get:43 http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                
Hit http://gb.archive.ubuntu.com precise/main Translation-en                   
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en             
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com precise/universe Translation-en               
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 12.8 MB in 22s (570 kB/s)                                              
Reading package lists... Done
danno@danno-laptop:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
The following packages were automatically installed and are no longer required:
  libindicator6 libapt-pkg4.11 libglew1.5 libglewmx1.5 libgssdp-1.0-2
  liblwres60 libept1 gir1.2-dee-0.5 zeitgeist-extension-fts libblas3gf
  libquvi0 libattica0 libdb4.8 python-wnck libgnome-desktop-2-17
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
danno@danno-laptop:~$ 

```

And the second thing, Im embarrassed to say but how do i check hardware ? If you have told me before i appologise my brain is in overdrive

---

### Post by darkod on 2012-05-22
Hardware or Additional Drivers is the program that lists any drivers that can be activated to make your hardware work.

In the new Unity interface the easiest is to open the Dashboard (the top button in Unity with the ubuntu logo, or simply pressing the windows logo key on the keyboard), and in the search line that opens on top of the new window, start typing what you are looking for.

In this case hardware, I think it was called like that. Below the search line it will show all programs found that contain the word/phrase you are searching for. Then just open what you are looking for.

Look around if there is a driver to activate for the wireless. According to what I read it should be called STA but that might be different. Just look if there are any drivers that it suggests to activate.

---

### Post by dannodan2008 on 2012-05-22
> **darkod said:**
> Hardware or Additional Drivers is the program that lists any drivers that can be activated to make your hardware work.

In the new Unity interface the easiest is to open the Dashboard (the top button in Unity with the ubuntu logo, or simply pressing the windows logo key on the keyboard), and in the search line that opens on top of the new window, start typing what you are looking for.

In this case hardware, I think it was called like that. Below the search line it will show all programs found that contain the word/phrase you are searching for. Then just open what you are looking for.

Look around if there is a driver to activate for the wireless. According to what I read it should be called STA but that might be different. Just look if there are any drivers that it suggests to activate.

 Yes sorry i understand now, I am trying to activate this STA driver everytime after reboot which takes me right back to post 1. :-( picture attatched  of the activate driver page.
Seperately, I really cant find any place within ubuntu that lists your hardware, also pic attatched (probaly not important right now)
Danno

---

### Post by darkod on 2012-05-22
OK, so if you try:
sudo apt-get install --reinstall bcmwl-kernel-source

That should reinstall the package. Also in software sources make sure restricted repository is enabled.

---

### Post by dannodan2008 on 2012-05-22
> **darkod said:**
> OK, so if you try:
sudo apt-get install --reinstall bcmwl-kernel-source

That should reinstall the package. Also in software sources make sure restricted repository is enabled.

Just want to post the code now. as i have to restart and dont want to lose it
```
danno@danno-laptop:~$ sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for danno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libindicator6 libapt-pkg4.11 libglew1.5 libglewmx1.5 libgssdp-1.0-2
  liblwres60 libept1 gir1.2-dee-0.5 zeitgeist-extension-fts libblas3gf
  libquvi0 libattica0 libdb4.8 python-wnck libgnome-desktop-2-17
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,202 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 254266 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6.1 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building for 3.0.0-19-generic-pae and 3.2.0-24-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.2.0-24-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
danno@danno-laptop:~$ 

```

---

### Post by dannodan2008 on 2012-05-22
Ok so installed what you asked (as above), rebooted and still no wireless option and still cannot activate the broadcom driver .  gutted.

---

### Post by darkod on 2012-05-22
OK, now try this:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
```

Wait few seconds and look in Network Manager if wireless will show up.

If that still doesn't make it show up, try also this:
```
sudo modprobe -r hp_wmi
```

Wait again few seconds, and check in Network Manager.

---

### Post by dannodan2008 on 2012-05-22
> **darkod said:**
> OK, now try this:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
```Wait few seconds and look in Network Manager if wireless will show up.

If that still doesn't make it show up, try also this:
```
sudo modprobe -r hp_wmi
```Wait again few seconds, and check in Network Manager.

Ok here goes,

```
danno@danno-laptop:~$ sudo modprobe -r b43 ssb wl
[sudo] password for danno: 
FATAL: Module wl not found.
danno@danno-laptop:~$ sudo modprobe wl
FATAL: Module wl not found.
danno@danno-laptop:~$ sudo modprobe -r hp_wmi
danno@danno-laptop:~$ 


```
Unfortunately as you can see mate. Nothing

---

### Post by darkod on 2012-05-22
Sorry, I did my best.

That card can work with ubuntu but I don't know if you have some weird conflict or what.

---

### Post by dannodan2008 on 2012-05-22
No Worries Darko. Thanks for your time. Is there anybody else out there before i take a step back to windows ? :-(
Darko your a legend mate. Thanks anyway

---

### Post by dannodan2008 on 2012-05-22
ATTENTION ADMIN- please do not close this thread. Im hoping that sometime somebody will see it and i can use ubuntu again.
Thank you
Danno

---

### Post by darkod on 2012-05-22
You might have better luck opening a new thread in Networking, there are more experts there.

Explain shortly, and link this thread.

---

### Post by ratcheer on 2012-05-22
This is from your install log:  "Module build for the currently running kernel was skipped since kernel source for this kernel does not seem to be installed."

[FONT=monospace]You need to install the kernel headers for your specific kernel, then rerun the module build. At least, that is what I think.

It looks to me like the package should be either linux-headers-3.2.0-24-generic-pae or linux-headers-3.2.0-24-generic-pae:i386

Tim
[/FONT]

---

### Post by westie457 on 2012-05-23
@ dannodan2008

As stated in the PM yesterday I am back to try to get the wireless working. Something was missed from the start and not sure what it is that got missed. So we will start the diagnostics over from where you are now. Could you post the output of all these commands please.```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan
dmesg | grep wl
lsmod | grep wl
```

---

### Post by darkod on 2012-05-23
If it helps, I found this about his BCM43225 card:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

It seems our try with firmware-b43-installer is not for this model.

But the try with bcmwl-kernel-source (as stated there) failed too. :(

He can actually see the STA driver in Additional Drivers from the start, only it doesn't want to activate. I'm out of ideas and not a real expert on this...

---

### Post by westie457 on 2012-05-24
> **darkod said:**
> If it helps, I found this about his BCM43225 card:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

It seems our try with firmware-b43-installer is not for this model.

But the try with bcmwl-kernel-source (as stated there) failed too. :(

He can actually see the STA driver in Additional Drivers from the start, only it doesn't want to activate. I'm out of ideas and not a real expert on this...

Thank you for having a try at fixing this, exactly how I learned.
Hopefully those commands will show something (simple)that was missed.

---

### Post by dannodan2008 on 2012-05-24
Hi again Westie and Darko, Unfortunately i will be stuck at work tonight so will not be able to respond with the outcome untill tomorrow evening.  
I have put this thread into the "networking" forum 
[http://ubuntuforums.org/showthread.php?t=1985665](http://ubuntuforums.org/showthread.php?t=1985665)
Should i post the outcome here or there guys ?. Talk tomorrow and thanks again :-)
Danno

---

### Post by darkod on 2012-05-24
Well, westie is running the show, lets see what he thinks. I would say the Networking section might receive more attention from network gurus, and maybe some fresh ideas.

But in that case continue posting in the same place, for continuity.

---

### Post by dannodan2008 on 2012-05-24
Hi westie,
                   I managed to get home tonight so i am just about to run these commands for you. As darko has suggested i shall post on the other thread in the networking forum so i guess ill speak with you there shortly :-)
[http://ubuntuforums.org/showthread.php?t=1985665](http://ubuntuforums.org/showthread.php?t=1985665)
 cheers guys :-)
Danno

---

### Post by km3952 on 2012-05-24
> **dannodan2008 said:**
> the driver im trying to install in attatchment.

I believe you just need to press 'activate'.

Edit: Origional post had a screen shot with the 'activate' button highlighted; I was replying to that post.

---

### Post by dannodan2008 on 2012-05-24
> **km3952 said:**
> I believe you just need to press 'activate'.

Edit: Origional post had a screen shot with the 'activate' button highlighted; I was replying to that post.

When i try to activate the driver thats when i get the error message pictured. In the last ubuntu i activated on first boot and all was well untill now.

---

### Post by westie457 on 2012-05-24
Having taken a look at your other thread I will bow out gracefully and learn from the sidelines. You are now in very capable hands that have vastly more knowledge than me.

Good luck and who knows, we might bump into each other again on the Fora.

---

