---
title: "Can't get wireless driver to load"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by Zeenomorph on 2011-11-12
I'm installing Ubuntu for a friend right now.  It's a dual boot with windows 7.  In Windows 7 the wireless works fine, so hardware seems to be good.

We also tested ubuntu 11.10 before installing, and during the test from the disk wireless worked well.

Now it's installed, and no more wireless.  The computer seems to see that the wireless card (pci) is in the computer.  I think the problem is in the driver.  When I go to the activate driver screen, there is a wireless driver there that is not activated.  Of course, I hit the activate button.  But am only greeted with an error.  I traced that down to this file;

[PHP]2011-11-12 18:41:33,621 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c>
2011-11-12 18:41:34,858 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic-pae/modules.alias
2011-11-12 18:41:35,055 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-11-12 18:41:35,067 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-11-12 18:41:35,108 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-11-12 18:41:35,156 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-11-12 18:41:35,258 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-11-12 18:41:35,259 DEBUG: Firmware for DVB cards not available
2011-11-12 18:41:35,259 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-11-12 18:41:35,268 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-11-12 18:41:35,309 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-11-12 18:41:35,310 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-11-12 18:41:35,310 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-11-12 18:41:35,344 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-11-12 18:41:35,353 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-11-12 18:41:35,353 DEBUG: nvidia.available: falling back to default
2011-11-12 18:41:35,527 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-12 18:41:35,534 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-12 18:41:35,544 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-11-12 18:41:35,544 DEBUG: nvidia.available: falling back to default
2011-11-12 18:41:35,628 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-12 18:41:35,636 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-11-12 18:41:35,645 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-11-12 18:41:35,646 DEBUG: nvidia.available: falling back to default
2011-11-12 18:41:35,722 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-12 18:41:35,723 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-11-12 18:41:35,743 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-12 18:41:35,752 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-11-12 18:41:35,752 DEBUG: nvidia.available: falling back to default
2011-11-12 18:41:35,836 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-12 18:41:35,843 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-11-12 18:41:35,855 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-11-12 18:41:35,856 DEBUG: nvidia.available: falling back to default
2011-11-12 18:41:35,937 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-12 18:41:35,945 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-11-12 18:41:35,954 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-11-12 18:41:35,955 DEBUG: nvidia.available: falling back to default
2011-11-12 18:41:36,037 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-12 18:41:36,038 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-11-12 18:41:36,083 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-11-12 18:41:36,109 DEBUG: Software modem not available
2011-11-12 18:41:36,109 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-11-12 18:41:36,121 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-12 18:41:36,131 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-11-12 18:41:36,131 DEBUG: fglrx.available: falling back to default
2011-11-12 18:41:36,203 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-12 18:41:36,211 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-12 18:41:36,220 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-11-12 18:41:36,220 DEBUG: fglrx.available: falling back to default
2011-11-12 18:41:36,278 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-11-12 18:41:36,278 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-11-12 18:41:36,288 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-11-12 18:41:36,289 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-11-12 18:41:36,289 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-11-12 18:41:36,289 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-11-12 18:41:36,297 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-11-12 18:41:36,297 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-11-12 18:41:36,329 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-11-12 18:41:36,330 DEBUG: all custom handlers loaded
2011-11-12 18:41:36,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001458sd00005007bc0Csc03i30')
2011-11-12 18:41:36,343 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-11-12 18:41:36,496 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:36,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-12 18:41:36,500 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-12 18:41:36,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:36,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-12 18:41:36,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-12 18:41:36,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-12 18:41:36,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2011-11-12 18:41:36,519 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-11-12 18:41:36,519 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:36,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'platform:eisa')
2011-11-12 18:41:36,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-12 18:41:36,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-12 18:41:36,537 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-12 18:41:36,537 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:36,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'acpi:PNP0501:')
2011-11-12 18:41:36,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-12 18:41:36,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc01i85')
2011-11-12 18:41:36,541 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2011-11-12 18:41:36,541 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:36,541 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'platform:pcspkr')
2011-11-12 18:41:36,541 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-11-12 18:41:36,541 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:36,541 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-11-12 18:41:36,542 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:36,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-11-12 18:41:36,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2011-11-12 18:41:36,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-12 18:41:36,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A102bc04sc03i00')
2011-11-12 18:41:36,787 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-12 18:41:36,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:36,788 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-12 18:41:36,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:36,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-12 18:41:36,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v000010DEd00000A20sv00001458sd000034D6bc03sc00i00')
2011-11-12 18:41:37,017 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2011-11-12 18:41:37,525 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:41:37,525 DEBUG: KMH enabled: False
2011-11-12 18:41:37,017 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-11-12 18:41:37,530 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-12 18:41:37,540 DEBUG: nvidia.available: falling back to default
2011-11-12 18:41:37,635 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:41:37,636 DEBUG: KMH enabled: False
2011-11-12 18:41:37,583 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-11-12 18:41:37,636 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2011-11-12 18:41:37,681 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:41:37,682 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 18:41:37,637 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-11-12 18:41:37,687 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-12 18:41:37,694 DEBUG: nvidia.available: falling back to default
2011-11-12 18:41:37,773 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:41:37,773 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 18:41:37,730 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-11-12 18:41:37,773 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2011-11-12 18:41:37,773 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,773 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2011-11-12 18:41:37,773 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,773 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-12 18:41:37,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-12 18:41:37,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-12 18:41:37,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2011-11-12 18:41:37,780 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'usb:v046DpC316d2800dc00dsc00dp00ic03isc01ip01')
2011-11-12 18:41:37,802 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-12 18:41:37,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,802 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-11-12 18:41:37,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001737sd00000060bc02sc80i00')
2011-11-12 18:41:37,837 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2011-11-12 18:41:37,838 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 18:41:37,837 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-11-12 18:41:37,841 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-11-12 18:41:37,842 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 18:41:37,842 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-11-12 18:41:37,843 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2011-11-12 18:41:37,843 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-12 18:41:37,845 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-11-12 18:41:37,845 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'input:b0003v046DpC316e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-11-12 18:41:37,845 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-12 18:41:37,846 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,846 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-12 18:41:37,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'input:b0003v04D9p1135e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-11-12 18:41:37,847 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-12 18:41:37,848 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-12 18:41:37,859 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrFE:bd03/04/2011:svnGigabyteTechnologyCo.,Ltd.:pnGA-880GA-UD3H:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-880GA-UD3H:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2011-11-12 18:41:37,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-12 18:41:37,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'input:b0003v046DpC316e0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,B6,D2,D9,EA,100,12C,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2011-11-12 18:41:37,874 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-12 18:41:37,874 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-12 18:41:37,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-12 18:41:37,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2011-11-12 18:41:37,878 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-11-12 18:41:37,878 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,878 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-11-12 18:41:37,878 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-12 18:41:37,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-12 18:41:37,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'usb:v046DpC316d2800dc00dsc00dp00ic03isc00ip00')
2011-11-12 18:41:37,879 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-12 18:41:37,879 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v00001002d00004391sv00001458sd0000B002bc01sc06i01')
2011-11-12 18:41:37,882 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-12 18:41:37,882 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,882 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-12 18:41:37,882 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-12 18:41:37,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2011-11-12 18:41:37,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-11-12 18:41:37,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-12 18:41:37,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v000010DEd00000BE2sv00001458sd000034D6bc04sc03i00')
2011-11-12 18:41:37,896 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-12 18:41:37,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-12 18:41:37,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'usb:v04D9p1135d0100dc00dsc00dp00ic03isc01ip02')
2011-11-12 18:41:37,897 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-12 18:41:37,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,897 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-11-12 18:41:37,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc06i01')
2011-11-12 18:41:37,897 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-12 18:41:37,898 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,898 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-12 18:41:37,898 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,898 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-12 18:41:37,898 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-11-12 18:41:37,905 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-11-12 18:41:37,905 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-12 18:41:37,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-12 18:41:37,905 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-12 18:41:37,905 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 18:41:37,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71ec64c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-12 18:41:37,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001458sd00005007bc0Csc03i30')
2011-11-12 18:41:37,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-12 18:41:37,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'platform:eisa')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'acpi:PNP0501:')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc01i85')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'platform:pcspkr')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A102bc04sc03i00')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v000010DEd00000A20sv00001458sd000034D6bc03sc00i00')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-12 18:41:37,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'usb:v046DpC316d2800dc00dsc00dp00ic03isc01ip01')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001737sd00000060bc02sc80i00')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'input:b0003v046DpC316e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'input:b0003v04D9p1135e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrFE:bd03/04/2011:svnGigabyteTechnologyCo.,Ltd.:pnGA-880GA-UD3H:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-880GA-UD3H:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'input:b0003v046DpC316e0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,B6,D2,D9,EA,100,12C,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'usb:v046DpC316d2800dc00dsc00dp00ic03isc00ip00')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v00001002d00004391sv00001458sd0000B002bc01sc06i01')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2011-11-12 18:41:37,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-12 18:41:37,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v000010DEd00000BE2sv00001458sd000034D6bc04sc03i00')
2011-11-12 18:41:37,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-12 18:41:37,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'usb:v04D9p1135d0100dc00dsc00dp00ic03isc01ip02')
2011-11-12 18:41:37,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc06i01')
2011-11-12 18:41:37,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-12 18:41:37,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-11-12 18:41:37,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-12 18:41:37,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-12 18:41:37,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68e16ec> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-12 18:41:37,962 DEBUG: handler kmod:wl previously unseen
2011-11-12 18:41:37,962 DEBUG: handler xorg:nvidia_current previously unseen
2011-11-12 18:41:37,962 DEBUG: handler xorg:nvidia_current_updates previously unseen
2011-11-12 18:41:37,963 DEBUG: writing back check cache /var/cache/jockey/check
2011-11-12 18:41:37,963 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 18:41:38,007 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:41:38,008 DEBUG: KMH enabled: False
2011-11-12 18:41:38,035 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:41:38,036 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 18:41:38,066 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 18:44:22,041 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 18:44:22,189 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:44:22,189 DEBUG: KMH enabled: False
2011-11-12 18:44:23,027 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:44:23,028 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 18:44:23,782 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 18:44:23,852 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 18:44:23,932 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:44:23,932 DEBUG: KMH enabled: False
2011-11-12 18:44:24,030 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:44:24,031 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 18:44:32,749 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:44:32,750 DEBUG: KMH enabled: False
2011-11-12 18:44:33,735 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:44:33,736 DEBUG: KMH enabled: False
2011-11-12 18:44:35,816 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:44:35,816 DEBUG: KMH enabled: False
2011-11-12 18:44:43,243 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-12 18:44:43,244 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-11-12 18:45:16,192 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:45:16,193 DEBUG: KMH enabled: False
2011-11-12 18:45:16,250 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:45:16,251 DEBUG: KMH enabled: False
2011-11-12 18:45:29,097 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 18:45:29,201 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:45:29,202 DEBUG: KMH enabled: False
2011-11-12 18:45:29,259 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:45:29,260 DEBUG: KMH enabled: False
2011-11-12 18:45:29,365 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:45:29,365 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 18:45:29,479 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:45:29,480 DEBUG: KMH enabled: False
2011-11-12 18:45:29,538 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:45:29,538 DEBUG: KMH enabled: False
2011-11-12 18:45:29,622 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 18:45:29,720 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:45:29,720 DEBUG: KMH enabled: False
2011-11-12 18:45:29,778 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:45:29,778 DEBUG: KMH enabled: False
2011-11-12 18:45:29,876 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 18:45:29,877 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 18:45:59,320 DEBUG: Shutting down
2011-11-12 19:09:38,366 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c>
2011-11-12 19:09:39,641 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic-pae/modules.alias
2011-11-12 19:09:39,764 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-11-12 19:09:39,776 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-11-12 19:09:39,810 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-11-12 19:09:39,857 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-11-12 19:09:39,980 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-11-12 19:09:39,981 DEBUG: Firmware for DVB cards not available
2011-11-12 19:09:39,981 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-11-12 19:09:39,991 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-11-12 19:09:40,032 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-11-12 19:09:40,032 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-11-12 19:09:40,032 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-11-12 19:09:40,069 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-11-12 19:09:40,078 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-11-12 19:09:40,079 DEBUG: nvidia.available: falling back to default
2011-11-12 19:09:40,250 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-12 19:09:40,257 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-12 19:09:40,266 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-11-12 19:09:40,267 DEBUG: nvidia.available: falling back to default
2011-11-12 19:09:40,349 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-12 19:09:40,356 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-11-12 19:09:40,365 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-11-12 19:09:40,366 DEBUG: nvidia.available: falling back to default
2011-11-12 19:09:40,447 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-12 19:09:40,448 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-11-12 19:09:40,469 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-12 19:09:40,478 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-11-12 19:09:40,478 DEBUG: nvidia.available: falling back to default
2011-11-12 19:09:40,560 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-12 19:09:40,567 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-11-12 19:09:40,576 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-11-12 19:09:40,576 DEBUG: nvidia.available: falling back to default
2011-11-12 19:09:40,658 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-12 19:09:40,665 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-11-12 19:09:40,674 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-11-12 19:09:40,675 DEBUG: nvidia.available: falling back to default
2011-11-12 19:09:40,757 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-12 19:09:40,757 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-11-12 19:09:40,802 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-11-12 19:09:40,820 DEBUG: Software modem not available
2011-11-12 19:09:40,820 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-11-12 19:09:40,832 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-12 19:09:40,841 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-11-12 19:09:40,842 DEBUG: fglrx.available: falling back to default
2011-11-12 19:09:40,933 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-12 19:09:40,941 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-12 19:09:40,950 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-11-12 19:09:40,950 DEBUG: fglrx.available: falling back to default
2011-11-12 19:09:41,042 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-11-12 19:09:41,042 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-11-12 19:09:41,052 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-11-12 19:09:41,053 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-11-12 19:09:41,053 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-11-12 19:09:41,053 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-11-12 19:09:41,061 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-11-12 19:09:41,062 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-11-12 19:09:41,102 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-11-12 19:09:41,103 DEBUG: all custom handlers loaded
2011-11-12 19:09:41,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001458sd00005007bc0Csc03i30')
2011-11-12 19:09:41,115 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-11-12 19:09:41,240 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:41,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-12 19:09:41,243 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-12 19:09:41,243 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:41,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-12 19:09:41,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-12 19:09:41,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-12 19:09:41,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2011-11-12 19:09:41,262 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-11-12 19:09:41,263 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:41,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'platform:eisa')
2011-11-12 19:09:41,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-12 19:09:41,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-12 19:09:41,280 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-12 19:09:41,280 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:41,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'acpi:PNP0501:')
2011-11-12 19:09:41,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-12 19:09:41,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc01i85')
2011-11-12 19:09:41,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2011-11-12 19:09:41,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:41,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'platform:pcspkr')
2011-11-12 19:09:41,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-11-12 19:09:41,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:41,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-11-12 19:09:41,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:41,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-11-12 19:09:41,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2011-11-12 19:09:41,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-12 19:09:41,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A102bc04sc03i00')
2011-11-12 19:09:41,530 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-12 19:09:41,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:41,531 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-12 19:09:41,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:41,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-12 19:09:41,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v000010DEd00000A20sv00001458sd000034D6bc03sc00i00')
2011-11-12 19:09:41,760 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2011-11-12 19:09:42,140 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:09:42,141 DEBUG: KMH enabled: False
2011-11-12 19:09:41,760 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-11-12 19:09:42,148 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-12 19:09:42,157 DEBUG: nvidia.available: falling back to default
2011-11-12 19:09:42,250 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:09:42,250 DEBUG: KMH enabled: False
2011-11-12 19:09:42,200 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-11-12 19:09:42,251 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2011-11-12 19:09:42,301 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:09:42,301 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:09:42,251 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-11-12 19:09:42,308 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-12 19:09:42,318 DEBUG: nvidia.available: falling back to default
2011-11-12 19:09:42,410 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:09:42,410 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:09:42,360 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-11-12 19:09:42,411 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2011-11-12 19:09:42,411 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,411 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2011-11-12 19:09:42,412 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,412 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-12 19:09:42,412 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-12 19:09:42,423 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-12 19:09:42,423 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2011-11-12 19:09:42,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'usb:v046DpC316d2800dc00dsc00dp00ic03isc01ip01')
2011-11-12 19:09:42,452 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-12 19:09:42,452 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,452 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-11-12 19:09:42,452 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,452 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001737sd00000060bc02sc80i00')
2011-11-12 19:09:42,486 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2011-11-12 19:09:42,487 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:09:42,486 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-11-12 19:09:42,493 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-11-12 19:09:42,493 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:09:42,493 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-11-12 19:09:42,493 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2011-11-12 19:09:42,493 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-12 19:09:42,494 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-11-12 19:09:42,494 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'input:b0003v046DpC316e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-11-12 19:09:42,494 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-12 19:09:42,494 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-12 19:09:42,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'input:b0003v04D9p1135e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-11-12 19:09:42,495 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-12 19:09:42,495 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-12 19:09:42,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrFE:bd03/04/2011:svnGigabyteTechnologyCo.,Ltd.:pnGA-880GA-UD3H:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-880GA-UD3H:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2011-11-12 19:09:42,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-12 19:09:42,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'input:b0003v046DpC316e0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,B6,D2,D9,EA,100,12C,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2011-11-12 19:09:42,513 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-12 19:09:42,513 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-12 19:09:42,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-12 19:09:42,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2011-11-12 19:09:42,516 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-11-12 19:09:42,516 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,516 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-11-12 19:09:42,516 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-12 19:09:42,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-12 19:09:42,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'usb:v046DpC316d2800dc00dsc00dp00ic03isc00ip00')
2011-11-12 19:09:42,517 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-12 19:09:42,517 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v00001002d00004391sv00001458sd0000B002bc01sc06i01')
2011-11-12 19:09:42,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-12 19:09:42,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,521 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-12 19:09:42,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-12 19:09:42,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2011-11-12 19:09:42,531 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-11-12 19:09:42,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-12 19:09:42,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v000010DEd00000BE2sv00001458sd000034D6bc04sc03i00')
2011-11-12 19:09:42,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-12 19:09:42,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-12 19:09:42,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'usb:v04D9p1135d0100dc00dsc00dp00ic03isc01ip02')
2011-11-12 19:09:42,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-12 19:09:42,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-11-12 19:09:42,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc06i01')
2011-11-12 19:09:42,536 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-12 19:09:42,536 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,536 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-12 19:09:42,536 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-12 19:09:42,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-11-12 19:09:42,543 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-11-12 19:09:42,543 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,543 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-12 19:09:42,543 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-12 19:09:42,543 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-12 19:09:42,543 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb727e64c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001458sd00005007bc0Csc03i30')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'platform:eisa')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'acpi:PNP0501:')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc01i85')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'platform:pcspkr')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A102bc04sc03i00')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-12 19:09:42,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v000010DEd00000A20sv00001458sd000034D6bc03sc00i00')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'usb:v046DpC316d2800dc00dsc00dp00ic03isc01ip01')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001737sd00000060bc02sc80i00')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'input:b0003v046DpC316e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'input:b0003v04D9p1135e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrFE:bd03/04/2011:svnGigabyteTechnologyCo.,Ltd.:pnGA-880GA-UD3H:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-880GA-UD3H:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'input:b0003v046DpC316e0110-e0,1,4,k71,72,73,74,83,8A,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,B6,D2,D9,EA,100,12C,13F,148,149,14A,14B,1A2,1A3,1A4,1A5,1A7,1A9,1AE,ram4,lsfw')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-12 19:09:42,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'usb:v046DpC316d2800dc00dsc00dp00ic03isc00ip00')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v00001002d00004391sv00001458sd0000B002bc01sc06i01')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v000010DEd00000BE2sv00001458sd000034D6bc04sc03i00')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'usb:v04D9p1135d0100dc00dsc00dp00ic03isc01ip02')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc06i01')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-12 19:09:42,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69736ec> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-12 19:09:42,597 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:09:42,699 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:09:42,700 DEBUG: KMH enabled: False
2011-11-12 19:09:43,540 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:09:43,540 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:09:44,297 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:09:44,381 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:09:44,477 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:09:44,477 DEBUG: KMH enabled: False
2011-11-12 19:09:44,567 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:09:44,567 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:09:48,903 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:09:50,726 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:09:55,459 DEBUG: _check_polkit_privilege: sender :1.55 on connection <dbus._dbus.SystemBus (system) at 0xb697408c> pid 1666 is not authorized for com.ubuntu.devicedriver.install: dbus.Dictionary({dbus.String(u'polkit.retains_authorization_after_challenge'): dbus.String(u'true')}, signature=dbus.Signature('ss'))
2011-11-12 19:10:25,708 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:25,813 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:25,813 DEBUG: KMH enabled: False
2011-11-12 19:10:25,917 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:25,917 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:10:25,964 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:26,050 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:26,148 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:26,149 DEBUG: KMH enabled: False
2011-11-12 19:10:26,247 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:26,248 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:10:28,247 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:33,055 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-11-12 19:10:33,056 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-11-12 19:10:33,173 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:36,808 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:36,911 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:36,911 DEBUG: KMH enabled: False
2011-11-12 19:10:37,015 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:37,015 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:10:37,071 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:37,154 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:37,251 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:37,251 DEBUG: KMH enabled: False
2011-11-12 19:10:37,349 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:37,349 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:10:43,685 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:44,582 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:44,583 DEBUG: KMH enabled: False
2011-11-12 19:10:45,046 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:45,047 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:10:45,550 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:52,415 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:52,698 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-11-12 19:10:52,699 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-11-12 19:10:52,779 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:58,008 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:58,111 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:58,111 DEBUG: KMH enabled: False
2011-11-12 19:10:58,214 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:58,214 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:10:58,268 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:58,350 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:10:58,447 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:58,447 DEBUG: KMH enabled: False
2011-11-12 19:10:58,544 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:10:58,545 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:12:20,895 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:21:08,492 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:21:08,597 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:21:08,598 DEBUG: KMH enabled: False
2011-11-12 19:21:08,702 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:21:08,703 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:21:08,751 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:21:08,838 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:21:08,930 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:21:08,930 DEBUG: KMH enabled: False
2011-11-12 19:21:09,030 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:21:09,030 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:21:14,854 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:21:53,342 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:21:54,902 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:22:09,157 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-11-12 19:22:09,158 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-11-12 19:22:09,196 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:22:12,808 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:22:12,911 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:22:12,912 DEBUG: KMH enabled: False
2011-11-12 19:22:13,014 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:22:13,015 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:22:13,069 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:22:13,151 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-12 19:22:13,247 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:22:13,248 DEBUG: KMH enabled: False
2011-11-12 19:22:13,345 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-11-12 19:22:13,345 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-12 19:25:53,667 DEBUG: Shutting down[/PHP]

What do I do next?  Why does it work from the install disk?  How can I manually get the driver from the install disk?  Or from another computer, and load it onto that one?

I'm stumped.

Zeeno

---

### Post by Zeenomorph on 2011-11-13
Well, I've had this post up for a day without answers.  I'm down to re-installing and hoping that miraculously things will be different.  Wish me  luck!

---

